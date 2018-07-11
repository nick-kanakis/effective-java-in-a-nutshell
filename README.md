# Effective Java in a nutshell (3rd edition)


## Index
* [Chapter 2: Creating and Destroying Objects](#chapter-2-creating-and-destroying-objects)
    * [Item 1: Consider static factory methods instead of constructors](#item-1-consider-static-factory-methods-instead-of-constructors)
    * [Item 2: Consider a builder when faced with many constructor parameters](#item-2-consider-a-builder-when-faced-with-many-constructor-parameters)
    * [Item 3: Enforce the singleton property with a private constructor or an enum type](#item-3-enforce-the-singleton-property-with-a-private-constructor-or-an-enum-type)
    * [Item 4: Enforce noninstantiability with a private constructor](#item-4-enforce-noninstantiability-with-a-private-constructor)
    * [Item 5: Prefer dependency injection to hardwiring resources](#item-5-prefer-dependency-injection-to-hardwiring-resources)
    * [Item 6: Avoid creating unnecessary objects](#item-6-avoid-creating-unnecessary-objects)
    * [Item 7: Eliminate obsolete object references](#item-7-eliminate-obsolete-object-references)
    * [Item 8: Avoid finalizers and cleaners](#item-8-avoid-finalizers-and-cleaners)
    * [Item 9: Prefer try-with-resources to try-finally](#item-9-prefer-try-with-resources-to-try-finally)
* [Methods Common to All Objects](#chapter3)
    * [Item 10: Obey the general contract when overriding equals](#item10)
    * [Item 11: Always override hashCode when you override equals](#item11)
    * [Item 12: Always override toString](#item12)
    * [Item 13: Override clone judiciously](#item13)
    * [Item 14: Consider implementing Comparable](#item14)
* [Classes and Interfaces](#chapter4)
    * [Item 15: Minimize the accessibility of classes and members](#item15)
    * [Item 16: In public classes, use accessor methods, not public fields](#item16)
    * [Item 17: Minimize mutability](#item17)
    * [Item 18: Favor composition over inheritance](#item18)
    * [Item 19: Design and document for inheritance or else prohibit it](#item19)
    * [Item 20: Prefer interfaces to abstract classes](#item20)
    * [Item 21: Design interfaces for posterity (future generations)](#item21)
    * [Item 22: Use interfaces only to define types](#item22)
    * [Item 23: Prefer class hierarchies to tagged classes](#item23)
    * [Item 24: Favor static member classes over nonstatic](#item24)
    * [Item 25: Limit source files to a single top-level class](#item25)
* [Generics](#chapter5)
    * [Item 26: Don’t use raw types](#item26)

## Chapter 2: Creating and Destroying Objects
### Item 1: Consider static factory methods instead of constructors

It is preferred to use static factory instead of constructor for the following
reasons:
1) They have names that can help identify the action of the static constructor
2) It is not required to return a new object, you can control when and if
you need to return a new instance (immutability, caching etc)
3) You can return an object of any subtype of the return type. For example
you can return ArrayList in a static factory method that returns Collection.
This helps with encapsulation.

Limitations:
1) Without a public/protected constructor class can not be subclassed.
(This can be a good thing see Item 17)

How to name a static factory method
- **from** eg: Date.from(argument)
- **of** eg: EnumSet.of(argument1, argument2)
- **valueOf** eg: BigInteger.valueOf(Integer.MAX_VALUE)
- **getInstance** eg: myObject.getInstance(argument)
- **getXXX** eg: Files.getFileStore(path)
- **newXXX** eg: Files.newBufferedReader(path)

### Item 2: Consider a builder when faced with many constructor parameters

Use the builder pattern when you have objects with many variables.
1) Easy to read and wright.

Why to void JavaBeans pattern (getter/setter):
1) The object could be in a inconsistent state partway through the setters call.
2) You cannot make the class immutable


### Item 3: Enforce the singleton property with a private constructor or an enum type

To make a class a singleton, keep the constructor private and a static factory method
to access the underlying sole instance.

You can also have an enum with a single-element:
```
public enum Elvis{
Instance
 ...
}
```

### Item 4: Enforce noninstantiability with a private constructor

Class that should not be instantiable(eg. utility classes) should have a private
constructor. This class can not be instantiated or extended.

### Item 5: Prefer dependency injection to hardwiring resources

Do not create new instances within an object let the client pass you the necessary instances.
This helps decouples your code.

### Item 6: Avoid creating unnecessary objects

- Item 1 static factory methods can help to minimize the number of objects that are
created by caching same used objects or by providing a singleton instance.
- Prefer primitives (int, boolean, long...) to boxed primitives (Integer, Boolean, Long...),
also watch out for unintentional autoboxing.

#### Item 7: Eliminate obsolete object references

Remove obsolete references to objects that are not needed any more.

The best way to eliminate an obsolete reference is to let the variable that
contained the reference fall out of scope. This occurs naturally if you define each
variable in the narrowest possible scope.

Another way is to null the reference but this should be avoided in order to avoid
cluttering the code.

Be extra careful when:

1) A class manages its own memory.
2) In caches. Caches may hold outdated references to objects that are obsolete.
3) Listeners and callbacks. Remember to deregister a listener/callback.

On way to solve these kind of problems is to use WeakHashMap.

#### Item 8: Avoid finalizers and cleaners

Disadvantages:
1) There is no guarantee they’ll be executed promptly (or that they will ever run),
they are just a "suggestion" to the gc.
2) Uncaught exceptions during finalization is ignored, that may leave
the object in a corrupted state (this is not the case with cleaners)
3) They cause performance issues.

Cleaners are a bit better than finalizers in this regard because
class authors have control over their own cleaner threads

What to do instead?
Implement AutoCloseable and require the client to invoke the close method,
typically using try-with-resources.

### Item 9: Prefer try-with-resources to try-finally

A resource must implement AutoClosable interface in order to be used by try-with-resources
eg:
```
try (InputStream in = new FileInputStream(src); OutputStream out = new FileOutputStream(dst)) {
    byte[] buf = new byte[BUFFER_SIZE];
    int n;
    while ((n = in.read(buf)) >= 0)
        out.write(buf, 0, n);
} catch (IOException e) {
 //do something with the exception
}
```

Advantages:
1) Try-finally is more verbose
2) Try-finally can easily written wrong (eg: forget the finally block)
3) If an error is thrown by the try block and the finally block only the
exception in the finally block will be written.

## Methods Common to All Objects

### Item 10: Obey the general contract when overriding equals

When to not override **equals** method:
1) Each instance of the class is inherently unique. eg: Thread class
2) A superclass has already overridden equals and the provided equals is appropriate.
3) When you know that the equal method will never be called (eg: a private class)

Equals should be overridden only when a class has a notion of *logical* equality.

Eg: a value class like Integer and String.

**5 properties of equals**

1) **Reflexive**: x.equals(x) should always return true.
2) **Symmetric**: x.equals(y) should be true if and only if y.equals(x).
3) **Transitive**: If x.equals(y) == true && y.equals(z)== true then x.equals(z) should be true.
4) **Consistent**: The result of an equals method should always be the same if the objects is not modified.
5) **Non-nullity**: x.equals(null) should return false.

**TIP 1**: There is no way to extend an instantiable class and add a value component while preserving the
equals contract

How to correctly overridden equal method:
1) Use the == operator to check if the argument is a reference to this object, if so return true.
This is a performance optimization
2) Use the *instanceof* operator to check if the argument has the correct type.
3) Cast the argument to the correct type.
4) For each “significant” field in the class, check if that field of the
argument matches the corresponding field of this object. Prioritize the check as
the most "light" operations and the ones that are most likely to differ to be on top,
for performance.

```
@Overridde
public boolean equals(Object o) {
(1) if ( o == this)
        return true;
(2) if(! (o instanceof MyType)
        return false;
(3) MyType mt = (MyType) o;
(4)... (expensive/unlikely to differ eqaulity checks at the end)
}
```

**TIP 2**: float & doubles should be checked with Float.compare(float, float)
and Double.compare(double, double) because of Float.NaN, Double.NaN.

### Item 11: Always override hashCode when you override equals

Equal objects must have equal hashcode, why?

Hashing retrieval is a two-step process.

1) Find the right bucket (using hashCode())
2) Search the bucket for the right element (using equals() )

If you override only equals and not the hashcode, 2 objects that are equal
will be in different buckets since their hashcode is not equal.

Also If a PhoneNumber object's equality is based on the number is passed as argument,
this will not work:
```
Map<PhoneNumber, String> m = new HashMap<>();
m.put(new PhoneNumber(2109412422), "Jenny");
m.get(new PhoneNumber(2109412422)) // will return null
```

This will happen because when you call push you use the hashcode function to get the bucket to insert
the Jenny's number, but get method uses also the hashcode to find the bucket and since the results of the
hashcode function are not based on the number (2 equal objects do not have the same hashcode), get will look
in a completely different bucket.

How to write a correct hashcode function:

1) Declare an int variable result and initialize it to the hashcode c for the first
significant field in your object as computed in step 2.a.
2) For every remaining significant field f in your object, do the following:
    1) Compute an int hash code c for the field:
        1) If the field is of a primitive type, compute Type.hashCode(f),
           where Type is the boxed primitive class corresponding to f’s type.
        2) If the field is an object reference and this class’s equals method
           compares the field by recursively invoking equals, recursively invoke
           hashCode on the field.
        3) If the field is an array, treat it as if each significant element were a
           separate field. That is, compute a hash code for each significant element
           by applying these rules recursively, and combine the values per step 2.b
    2) Combine the hash code c computed in step 2.a into result as follows:
    ``` result = 31 * result + c```
3) Return result.


eg:

Let's say you have a PhoneNumber object with:
short areaCode
short prefix
short lineNum

```
@Override
public int hashCode() {
int result = Short.hashCode(areaCode);
result = 31 * result + Short.hashCode(prefix);
result = 31 * result + Short.hashCode(lineNum);
return result;
}
```

### Item 12: Always override toString

providing a good toString implementation makes your class much more pleasant
to use and makes systems using the class easier to debug.

It is best to add comment to specify the format of the the toString() method

### Item 13: Override clone judiciously

Why not to use clonable:
- A class that implements Cloneable is expected to provide a properly functioning public clone()
method. Also all superclass must implement clone(). This is a fragile mechanism and this
is the one (of many) reason it is best to avoid overriding clone.
- Creating a correct clone method is quite difficult and should be avoided whenever possible.
- Classes that are design for inheritance should not implement Clonnable
- Immutable class should never provide a clone method because it would merely encourage a wasteful copying.

To create a "correct" clone method:
1) Call ```super.clone```
2) Fix any field that needs fixing by "deep coping" (recursively or not)

What to do instead of clone?

A better approach to object copying is to provide a copy constructor or copy factory.

**Copy constructor** simply a constructor that takes a single argument whose type is the class containing the
constructor, for example,

```
class Complex {

    private double re, im;

    // A normal parametrized constructor
    public Complex(double re, double im) {
        this.re = re;
        this.im = im;
    }

    // copy constructor
    Complex(Complex c) {
        re = c.re;
        im = c.im;
    }
 }
```

**Copy Factory** is the static factory (Item 1) analogue of a copy constructor.

With copy constructor/factory can take an interface as argument do not force the client accept concrete
implementations.

### Item 14: Consider implementing Comparable

Every class that can have natural ordering should implement Comparable.

```
public interface Comparable<T> {
    int compareTo(T t);
}
```

1) sgn(x.compareTo(y)) == - sgn(y. compareTo(x)) for all x and y.
2) (x.compareTo(y) > 0 && y.compareTo(z) > 0) implies x.compareTo(z) > 0.
3) x.compareTo(y) == 0 implies that sgn(x.compareTo(z)) == sgn(y.compareTo(z)), for all z.
4) (x.compareTo(y) == 0) == (x.equals(y)). Not mandatory but highly advised

Like overriding equals there is no way to extend an instantiable class with a new value
component while preserving the compareTo contract.

Do not use ```<``` or ```>``` operator instead use boxed compare methods:
```
Double.compare(Double, Double)
Float.compare(Float, Float)
Short.compare(Short, Short)
```

In Java 8+ you can do:
```
private static final Comparator<PhoneNumber> COMPARATOR =
    comparingInt((PhoneNumber pn) -> pn.areaCode)
                            .thenComparingInt(pn -> pn.prefix)
                            .thenComparingInt(pn -> pn.lineNum);

public int compareTo(PhoneNumber pn) {
    return COMPARATOR.compare(this, pn);
}
```

If two phone numbers have the same area code, we need to further refine the
comparison, and that’s exactly what the second comparator construction method,
thenComparingInt, does.


## Classes and Interfaces

### Item 15: Minimize the accessibility of classes and members

A well designed component hides all its implementation details, cleanly separating its
API from its implementation. This concept, known as information hiding or encapsulation.

The rule of thumb is simple: make each class or member as inaccessible as
possible.

**For classes**:
If you declare a top-level class or interface with the public modifier, it will be public;
otherwise, it will be package-private.

By making it package-private, you make it part of the implementation
rather than the exported API, and you can modify it, replace it, or eliminate it in
a subsequent release without fear of harming existing clients

**For members (fields, methods, nested classes, and nested interfaces)**

Sorted (private >>> public)
- **private**.
- **package private** (default access). The member is accessible from any class in the package
 where it is declared.
- **protected**. The member is accessible from subclasses of the class where it is
declared and from any class in the package where it is declared.
- **protected**.
- **public**.

Private & Package private members are part of class's implementation and do not impact the
exposed API.

Why minimize the expose of members, classes?

1) Decoubles components.
2) It eases the burden of maintenance.
3) Increase software reuse.
4) Decreases the risk of creating large systems.

### Item 16: In public classes, use accessor methods, not public fields

If a class is package-private or is a private nested class, there is nothing
inherently wrong with exposing its data fields. This approach is better because it's
generates less visual clutter.

Otherwise use getters/setters if you want to expose mutable fields. It is best
to follow this advise and for immutable fields.


### Item 17: Minimize mutability

An immutable class is simply a class whose instances cannot be modified.

How to make a class immutable:
1) Don’t provide methods that modify the object’s state.
2) Ensure that the class can’t be extended (Make the class final or make the constructor private, the latest is better because
it allows for future refactoring, by adding a new inner subclass).
3) Make all fields final (you can have non-final fields as long as you control the access to it and return only
cached results, to avoid the recalculation cost).
4) Make all fields private. To avoid clients obtaining access to a field and modifying it.
5) Ensure exclusive access to any mutable components. If a field is mutable make sure that the
client cannot obtain a reference to these objects, make defensive copies in constructors, accessors.

eg:

```
// Immutable complex number class
public **final** class Complex {
    private **final** double re;
    private **final** double im;

    public Complex(double re, double im) {
        this.re = re;
        this.im = im;
    }

    public double realPart() { return re; }
    public double imaginaryPart() { return im; }
    public Complex plus(Complex c) {
        **return new Complex(re + c.re, im + c.im);** // Because fields are final return a new instance with the result.
    }
    ...
}
```

Advantages of immutable objects:
- Immutable objects are simple. An immutable object can be in exactly one state, the state in which it
was created, and it will remain like this until it is collected by the gc.
- Immutable objects are inherently thread-safe; they require no
synchronization.
- You do not need Clonable if a object is immutable.
- They make great building blocks for other objects.

If you cannot make the class immutable limit it's immutability as much as possible

What about the performance overhead of all those object, since an immutable objects
requires a new instance for every different state it is?

This is something to take into consideration, if the object is small make it immutable,
if it is large try to make it as immutable as possible ( by making fields final etc...).
Also you can internally ise a package-private mutable companion class! that it uses to speed up
expensive computations

### Item 18: Favor composition over inheritance

Problems with inheritance:

1) **Violates encapsulation**. A subclass depends on the implementation details of its
superclass for its proper function. The superclass’s implementation may change from release to release,
and if it does, the subclass may break, even though its code has not been touched.

2) **Cloneable or Serializable** are not easily supported in hierarchical classes.

**How to use composition instead of inheritance**

Instead of extending an existing class, give your new class a private field that references
an instance of the existing class. Each instance method in the new class invokes the corresponding
method on the contained instance of the existing class and returns the results. This is known as *forwarding*.

Example:
```
// Wrapper class - uses composition in place of inheritance
public class InstrumentedSet<E> extends ForwardingSet<E> {
    private int addCount = 0;
    public InstrumentedSet(Set<E> s) {
        super(s);
    }

    @Override
    public boolean add(E e) {
        addCount++;
        return super.add(e);
    }

    @Override
    public boolean addAll(Collection<? extends E> c) {
        addCount += c.size();
        return super.addAll(c);
    }

     public int getAddCount() {
        return addCount;
    }
}

// Reusable forwarding class
public class ForwardingSet<E> implements Set<E> {
    private final Set<E> s;
    //Constructor with a Set argument for the composed instance s.
    public ForwardingSet(Set<E> s) { this.s = s; }
    public void clear() { s.clear(); }
    public boolean contains(Object o) { return s.contains(o); }
    public boolean isEmpty() { return s.isEmpty(); }
    public int size() { return s.size(); }
    public Iterator<E> iterator() { return s.iterator(); }
    public boolean add(E e) { return s.add(e); }
    public boolean remove(Object o) { return s.remove(o); }
    public boolean containsAll(Collection<?> c) { return s.containsAll(c); }
    public boolean addAll(Collection<? extends E> c) { return s.addAll(c); }
    public boolean removeAll(Collection<?> c) { return s.removeAll(c); }
    public boolean retainAll(Collection<?> c) { return s.retainAll(c); }
    public Object[] toArray() { return s.toArray(); }
    public <T> T[] toArray(T[] a) { return s.toArray(a); }

    @Override public boolean equals(Object o) { return s.equals(o); }
    @Override public int hashCode() { return s.hashCode(); }
    @Override public String toString() { return s.toString(); }
}
```

The advantages of this approach is that the forwarding class can be used by many classes that may want to
compose the Set<E> Interface. This approach is a decorator pattern.

### Item 19: Design and document for inheritance or else prohibit it

How to design for inheritance:

1) The class must document its self-use of overridable methods.

2) You should add hooks into its internal workings in the form of judiciously chosen protected methods. The subclass can
use these methods (hooks) more easily than overriding and rewriting parts of the superclass.

You will need to commit forever to these 2 patterns (documentation,hooks).


### Item 20: Prefer interfaces to abstract classes

Advantages of interfaces:

1) Existing classes can easily be retrofitted to implement a new interface.
Many existing classes were retrofitted to implement the Comparable, Iterable, and
Autocloseable interfaces when they were added to the platform.

2) Interfaces allow for the construction of nonhierarchical type frameworks.
eg:
```
//Interface 1
public interface Singer {
    AudioClip sing(Song s);
}

//Interface 2
public interface Songwriter {
    Song compose(int chartPosition);
}

// Interface 3 = Interface 1 + Interface 2
public interface SingerSongwriter extends Singer, Songwriter {
    AudioClip strum();
    void actSensitive();
}

```


Disadvantages:

1) Interfaces are not permitted to contain instance fields or nonpublic static members
2) Default methods have a limit (Methods that are declared in java.lang.Object like: equals(), hashCode() cannot defaulted )

Solution:

Combine abstract classes & interfaces. The interface defines the type, perhaps providing some default methods, while
the abstract implementation class implements the remaining non-primitive interface methods atop the primitive interface methods.

Examples:
```
/**
 * The Interface
 *
 */
interface RedisConnection
{
    int connect();
    boolean isConnected();
    int disconnect();
    int getDatabaseNumber();
}

/**
 * Abstract class which implements the interface.
 * This is called Abstract Interface
 *
 */
abstract class AbstractRedisConnection implements RedisConnection
{
    @Override
    public final int connect()
    {
        //... lots of code to connect to Redis
    }

    @Override
    public final boolean isConnected()
    {
        //... code to check Redis connection
    }

    @Override
    public final int disconnect()
    {
        //... lots of code to disconnect from Redis and perform cleanup
    }
 }

/**
 * A subclass which extends from the Abstract Interface
 *
 */
class RedisOptOut extends AbstractRedisConnection {…}

```

Also if a class cannot be made to extend the skeletal implementation, the class can always
implement the interface directly.

In order to write "Skeletal" or AbstractXXX class:

1) study the interface and decide which methods are the primitives in
terms of which the others can be implemented. These primitives will be the
abstract methods in your skeletal implementation.

2) provide default methods in the interface for all of the methods that can be implemented directly atop the
primitives, but recall that you may not provide default methods for Object
methods such as equals and hashCode.

3) If the primitives and default methods cover the interface,
you’re done, and have no need for a skeletal implementation class.
Otherwise, write a class declared to implement the interface, with
implementations of all of the remaining interface methods. The class may
contain any nonpublic fields and methods appropriate to the task.


### Item 21: Design interfaces for posterity (future generations)

```
interface TestInterface
{
    void square(int a);

    // default method
    default void show()
    {
      System.out.println("Default Method Executed");
    }
}
```

Even though default methods are now a part of the Java
platform and be "injected" into existing implementations without the knowledge or consent of their
implementors, it is still of the utmost importance to design interfaces with great care.

### Item 22: Use interfaces only to define types

Do not use interfaces to define constants. Better add them to the a class, utility classes or a enum.

### Item 23: Prefer class hierarchies to tagged classes

Tag classes are classes that contain a tag field that indicates the flavor of the instance
eg:

```
class Figure {
    enum Shape { RECTANGLE, CIRCLE };

    // Tag field - the shape of this figure
    final Shape shape;
    ...
}

```

Tagged classes are verbose, error-prone, and inefficient. They should be avoided.

How to transorm tagged classes to hierarchy:

1) Define an abstract class/interface containing an abstract method for each method in the tagged class whose
   behavior depends on the tag value.
2) Define a concrete subclass of the root class for each flavor of the
   original tagged. In our example, there are two: circle and rectangle.
   Also include in each subclass the appropriate implementation of each abstract method
   in the root class.

### Item 24: Favor static member classes over nonstatic

Differences between static and non static nested classes:

A non-static nested class has full access to the members of the class within which it is nested.
A static nested class does not have a reference to a nesting instance,
so a static nested class cannot invoke non-static methods or access non-static fields of an instance of the class within which it is nested.

If you declare a nested class that does not require access to an enclosing
instance, always put the static modifier in its declaration. If you omit this modifier, each
instance will have a hidden extraneous reference to its enclosing instance.
As previously mentioned, storing this reference takes time and space.
More seriously, it can result in the enclosing instance being retained when it would
otherwise be eligible for garbage collection.

Eg: Entry inner class of Map. While each entry is associated with a map,
the methods on an entry (getKey, getValue, and setValue) do not need access to the map.

### Item 25: Limit source files to a single top-level class

Never put multiple top-level classes or interfaces in a single source file.

Following this rule guarantees that you can’t have multiple
definitions for a single class at compile time. This in turn guarantees that the
class files generated by compilation, and the behavior of the resulting program,
are independent of the order in which the source files are passed to the compiler.


## Generics

### Item 26: Don’t use raw types