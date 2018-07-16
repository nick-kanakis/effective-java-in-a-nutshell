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
* [Chapter 3: Methods common to all objects](#chapter-3-methods-common-to-all-objects)
    * [Item 10: Obey the general contract when overriding equals](#item-10-obey-the-general-contract-when-overriding-equals)
    * [Item 11: Always override hashCode when you override equals](#item-11-always-override-hashcode-when-you-override-equals)
    * [Item 12: Always override toString](#item-12-always-override-tostring)
    * [Item 13: Override clone judiciously](#item-13-override-clone-judiciously)
    * [Item 14: Consider implementing Comparable](#item-14-consider-implementing-comparable)
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
* [Chapter 5: Generics](#chapter-5-generics)
    * [Item 26: Don’t use raw types](#item-26-dont-use-raw-types)
    * [Item 27: Eliminate unchecked warnings](#item-27-eliminate-unchecked-warnings)
    * [Item 28: Prefer lists to arrays](#item-28-prefer-lists-to-arrays)
    * [Item 29: Favor generic types](#item-29-favor-generic-types)
    * [Item 30: Favor generic methods](#item-30-favor-generic-methods)
    * [Item 31: Use bounded wildcards to increase API flexibility](#item-31-use-bounded-wildcards-to-increase-api-flexibility)
    * [Item 32: Combine generics and varargs judiciously](#item-32-combine-generics-and-varargs-judiciously)
    * [Item 33: Consider typesafe heterogeneous containers](#item-32-consider-typesafe-heterogeneous-containers)
* [Chapter 6: Enums and Annotations](#chapter-6-enums-and-annotations)
    * [Item 34: Use enums instead of int constants](#item-34-use-enums-instead-of-int-constants)
    * [Item 35: Use instance fields instead of ordinals](#item-35-use-instance-fields-instead-of-ordinals)
    * [Item 36: Use EnumSet instead of bit fields](#item-36-use-enumset-instead-of-bit-fields)
    * [Item 37: Use EnumMap instead of ordinal indexing](#item-36-use-enummap-instead-of-ordinal-indexing)
    * [Item 38: Emulate extensible enums with interfaces](#item-38-emulate-extensible-enums-with-interfaces)
    * [Item 39: Prefer annotations to naming patterns](#item-39-prefer-annotations-to-naming-patterns)
    * [Item 40: Consistently use the Override annotation](#item-40-consinstetly-use-the-override-annotation)
    * [Item 41: Use marker interfaces to define types](#item-41-use-marker-interfaces-to-define-types)
* [Chapter 8: Methods](#chapter-8-methods)
    * [Item 49: Check parameters for validity](#item-49-check-parameters-for-validity)
    * [Item 50: Make defensive copies when needed](#item-50-make-defensive-copies-when-needed)
    * [Item 51: Design method signatures carefully](#item-51-design-method-signatures-carefully)
    * [Item 52: Use overloading judiciously](#item-52-use-overloading-judiciously)
    * [Item 53: Use varargs judiciously](#item-53-use-varargs-judiciously)
    * [Item 54: Return empty collections or arrays, not nulls](#item-54-return-empty-collections-or-arrays-not-nulls)
    * [Item 55: Return optionals judiciously](#item-55-return-optionals-judiciously)


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

## Chapter 3: Methods common to all objects

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

Raw type of List\<E> is List. Raw types behave as if all of
the generic type information were erased from the type declaration.
They exist primarily for compatibility with pre-generics code.

With generics you can control what instance can be inserted into your datastructure.
If you use raw types, you lose all the safety and expressiveness benefits of generics

What is the difference between the raw type List and the parameterized type List\<Object>?

While you can pass a List\<String> to a parameter of type List, you can’t pass it to a parameter
of type List\<Object>. List\<Object> is perfectly acceptable.

If you want to use a generic type but you don’t know or care what the actual type parameter is,
you can use a question mark instead.

eg: Set<?>

It is the most general parameterized Set type, capable of holding any set.

There are two facts about Set<?>:

- Since the question mark ? stands for any type. Set<?> is capable of holding any type of elements.
- Because we don't know the type of ?, we can't put any element into Set<?>

What is the difference between the unbounded wildcard type Set<?> and the
raw type Set?

ArrayList with raw type is not type safe but ArrayList<?> with the unbounded wildcard is type safe.

You can add objects of any type into raw ArrayList but you cannot do
that with a generic ArrayList with unbounded wildcard i.e. ArrayList.

```
//Legal Code
public static void main(String[] args) {
	HashSet<Integer> s1 = new HashSet<Integer>(Arrays.asList(1, 2, 3));
	printSet(s1);

	HashSet<String> s2 = new HashSet<String>(Arrays.asList("a", "b", "c"));
	printSet(s2);
}

public static void printSet(Set<?> s) {
	for (Object o : s) {
		System.out.println(o);
	}
}

//Illegal Code
public static void printSet2(Set<?> s) {
	s.add(10);//this line is illegal
	for (Object o : s) {
		System.out.println(o);
	}
}

```

```printSet2``` method whould be legal if the argument was ```Set s```
However, this will easily corrupt the invariant of collection.

Generally in we cannot assume anything about the unbounded wild card, so you
cannot insert anything, you cannot even instantiate one:

```
//Illegal Code
Set<?> set = new HashSet<?>();
```

### Item 27: Eliminate unchecked warnings

Eliminate every unchecked warning that you can.

If you can’t eliminate a warning, but you can prove that the code that
provoked the warning is typesafe, then (and only then) suppress the
warning with an @SuppressWarnings("unchecked") annotation. And always use the
SuppressWarnings annotation on the smallest scope possible. Do not forget to
comment asying why it is safe to do so.

### Item 28: Prefer lists to arrays

If Sub is a subtype of Super, then the array type Sub\[] is a subtype of the array type Super\[].
This is not the case in Generics, for any two distinct types Type1 and
Type2, List\<Type1> is neither a subtype nor a supertype of List\<Type2>.

Why this is a preferable?

Because you can find errors during compiling and not during run-time.

```
// Fails at runtime!
Object[] objectArray = new Long[1];
objectArray[0] = "I don't fit in"; // Throws ArrayStoreException


// Won't compile!
List<Object> ol = new ArrayList<Long>(); // Incompatible types
ol.add("I don't fit in");
```

It is illegal to create an array of a generic type (because generic isn't typesafe), a
parameterized type, or a type parameter. Therefore, none of these array creation
expressions are legal: new List\<E>\[], new List\<String>\[], new
E\[]

Generally arrays provide runtime type safety but not compile-time type safety, and vice
versa for generics avoid combining generics and arrays!

### Item 29: Favor generic types

Generic types are safer and easier to use than types that require
casts in client code. When you design new types, make sure that they can be
used without such casts

### Item 30: Favor generic methods

The type parameter list, which declares the type parameters, goes
between a method’s modifiers and its return type
eg:

```
// Generic method
public static <E> Set<E> union(Set<E> s1, Set<E> s2) {
    Set<E> result = new HashSet<>(s1);
    result.addAll(s2);
    return result;
}

```

Generic methods, like generic types, are safer and easier to use
than methods requiring their clients to put explicit casts on input parameters and
return values.

### Item 31: Use bounded wildcards to increase API flexibility

As we said in item 28

Despite the fact that String is a subtype of Object List\<String> is not a subtype of
List\<Object>, so you cannot add a String to a list\<Object>, and this is good. But sometimes you
may need to have that flexibility.

For this we can use bounded wildcards. Eg:

```
Iterable<? extends E>
```

This means that Iterable can be any time that is subtype of E, or E itshelf.

For maximum flexibility, use wildcard types on input parameters that represent producers or consumers.

**PECS stands for producer-extends, consumer-super.**
- if a parameterized type represents a T producer, use **<?extends T>**
- if it represents a T consumer, use **<? super T>**.

But keep in mind you should never use bounded wildcard types as return types.
This force the client to use wildcard types too.

- Use Comparable<? super T> in preference to Comparable<T>.
- Use Comparator<? super T> in preference to Comparator<T>

eg:

```
public static <T extends Comparable<? super T>> T max(List<? extends T> list)
```

### Item 32: Combine generics and varargs judiciously

When you invoke a varargs method, an array of Object is created to hold the varargs parameters.
Remember that generics and arrays do not play well together.

It is unsafe most of the times to store a value in a generic varargs array parameter.

When it is safe to use generic with arrays?

1) If the method doesn’t store anything into the array.

2) If the method doesn’t allow a reference to the array to escape.


If the method is 100% safe you can use the SafeVarargs (@SafeVarargs) annotation that constitutes
a promise by the author of a method that it is typesafe

As an alternative you can use a list of lists as arguments :

```
static <T> List<T> flatten(List<List<? extends T>> lists) {
    List<T> result = new ArrayList<>();
    for (List<? extends T> list : lists)
        result.addAll(list);
    return result;
}
```

### Item 33: Consider typesafe heterogeneous containers

You can add elements of different type by parameterizing the key instead of the container.
Then present the parameterized key to the container to insert or retrieve a value.

eg: The Class object for the type will play the part of the parameterized key.
The reason this works is that class Class is generic. The type of a class literal
is not simply Class, but Class\<T>. For example, String.class is of type
Class\<String>, and Integer.class is of type Class\<Integer>.


```
// Typesafe heterogeneous container pattern - implementation
public class Favorites {
    private Map<Class<?>, Object> favorites = new HashMap<>();

    public <T> void putFavorite(Class<T> type, T instance) {
        favorites.put(Objects.requireNonNull(type), instance);
    }

    public <T> T getFavorite(Class<T> type) {
        return type.cast(favorites.get(type));
    }
}
```

The cast method is the dynamic analogue of Java’s cast operator. It simply
checks that its argument is an instance of the type represented by the Class
object. If so, it returns the argument; otherwise it throws a
ClassCastException.

The normal use of generics, exemplified by the collections APIs,
restricts you to a fixed number of type parameters per container. You can get
around this restriction by placing the type parameter on the key rather than the
container. You can use Class objects as keys for such typesafe heterogeneous
containers. A Class object used in this fashion is called a type token. You can
also use a custom key type. For example, you could have a DatabaseRow type
representing a database row (the container), and a generic type Column\<T> as
its key.

## Chapter 6: Enums and Annotations

### Item 34: Use enums instead of int constants

Why to avoid int constants?
1) Their is no type safety, the compiler won’t complain if you pass an apple to a method that
expects an orange
2) There is no easy way to translate int enum constants into printable strings. If
you print such a constant or display it from a debugger, all you see is a number.
3) You have to use prefixes to identify different things like: ELEMENT_MERCURY and PLANET_MERCURY

solution:
```
public enum Apple { FUJI, PIPPIN, GRANNY_SMITH }
public enum Orange { NAVEL, TEMPLE, BLOOD }
```

The basic idea behind Java’s enum types is simple: they are classes that export
one instance for each enumeration constant via a public static final field. Enum
types are effectively final, by virtue of having no accessible constructors.
They are a generalization of singletons, which are essentially single-element enums.

Enums provide compile-time type safety. If you declare a parameter to be of
type Apple, you are guaranteed that any non-null object reference passed to the
parameter is one of the three valid Apple values.

To associate data with enum constants, declare instance fields and write a constructor that takes
the data and stores it in the fields.

eg:
```
public enum Planet {
    MERCURY(3.302e+23, 2.439e6),
    VENUS (4.869e+24, 6.052e6),
    EARTH (5.975e+24, 6.378e6),
    MARS (6.419e+23, 3.393e6),
    JUPITER(1.899e+27, 7.149e7),
    SATURN (5.685e+26, 6.027e7),
    URANUS (8.683e+25, 2.556e7),
    NEPTUNE(1.024e+26, 2.477e7);

    private final double mass; // In kilograms
    private final double radius; // In meters
    private final double surfaceGravity; // In m / s^2

    // Universal gravitational constant in m^3 / kg s^2
    private static final double G = 6.67300E-11;

    // Constructor
    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
        surfaceGravity = G * mass / (radius * radius);
    }

    public double mass() { return mass; }

    public double radius() { return radius; }

    public double surfaceGravity() { return surfaceGravity; }

    public double surfaceWeight(double mass) {
        return mass * surfaceGravity; // F = ma
    }
}
```

**SOS: Enums are by their nature immutable, so all fields should be final.**

How to add constant-specific behavior?

 1) Create an abstract method in the enum
 2) In each constant override the abstract method and create a concrete
 implementation

 ```
public enum Operation {
    PLUS {public double apply(double x, double y){return x + y;}},
    MINUS {public double apply(double x, double y){return x - y;}},
    TIMES {public double apply(double x, double y){return x * y;}},
    DIVIDE{public double apply(double x, double y){return x / y;}};

    public abstract double apply(double x, double y);
}
 ```

 **Enum types have an automatically generated valueOf(String) method
   that translates a constant’s name into the constant itself.**

```
Operation op = Operation.valueOf("PLUS");
```

### Item 35: Use instance fields instead of ordinals

All enums have an ordinal method, which returns the numerical position of each enum
constant in its type.


```
public enum Ensemble {
    SOLO, DUET, TRIO, QUARTET, QUINTET,
    SEXTET, SEPTET, OCTET, NONET, DECTET;

    public int numberOfMusicians() { return ordinal() + 1; }
}
```

This is very fragile a simple reordering or an addition/deletion of a constant
will break any implementation relying on ordinal() method.

Never derive a value associated with an enum from its ordinal; store it in an instance field
instead:

```
public enum Ensemble {
    SOLO(1), DUET(2), TRIO(3), QUARTET(4), QUINTET(5),
    SEXTET(6), SEPTET(7), OCTET(8), DOUBLE_QUARTET(8),
    NONET(9), DECTET(10), TRIPLE_QUARTET(12);

    private final int numberOfMusicians;
    Ensemble(int size) { this.numberOfMusicians = size; }

    public int numberOfMusicians() { return numberOfMusicians; }
}
```


### Item 36: Use EnumSet instead of bit fields

Just because an enumerated type will be used in sets, there is
no reason to represent it with bit fields. The EnumSet class combines the
conciseness and performance of bit fields with all the many advantages of enum types

EnumSet is a a concrete implementation of Set interface that is used to combine
one or more Enum constants

```
Set<Style> styles = EnumSet.of(Style.BOLD, Style.ITALIC)
```

### Item 37: Use EnumMap instead of ordinal indexing

There is a very fast Map implementation designed for use with
enum keys.

```
Map<Plant.LifeCycle, Set<Plant>> plantsByLifeCycle = new EnumMap<>(Plant.LifeCycle.class);
```
In the parenthesis you put the key class.

You can also do mor complex nested maps:
```
public enum Phase {
    SOLID, LIQUID, GAS;
    public enum Transition {
        MELT(SOLID, LIQUID), FREEZE(LIQUID, SOLID),
        BOIL(LIQUID, GAS), CONDENSE(GAS, LIQUID),
        SUBLIME(SOLID, GAS), DEPOSIT(GAS, SOLID);

        private final Phase from;
        private final Phase to;
        Transition(Phase from, Phase to) {
            this.from = from;
            this.to = to;
        }
```

and use a EnumMap like this:
```
Map<Phase, Map<Phase, Transition>> = new EnumMap<>(Phase.class)
```

The above means: “map from (source) phase to map from (destination) phase to transition.”

### Item 38: Emulate extensible enums with interfaces

Generally you cannot (and should not) extend enums, you can emulate it by writing an interface
to accompany a basic enum type that implements the interface.
This allows clients to write their own enums (or other types) that implement the interface.
Instances of these types can then be used wherever instances of the basic enum type can be used,
assuming APIs are written in terms of the interface.

```
public interface Operation {
    double apply(double x, double y);
}

public enum BasicOperation implements Operation {
    PLUS("+") {
        public double apply(double x, double y) { return x + y; }
    },
    MINUS("-") {
        public double apply(double x, double y) { return x - y; }
    },
    TIMES("*") {
        public double apply(double x, double y) { return x * y; }
    },
    DIVIDE("/") {
        public double apply(double x, double y) { return x / y; }
    };

    private final String symbol;
    BasicOperation(String symbol) {
        this.symbol = symbol;
    }
 }

public enum ExtendedOperation implements Operation {
    EXP("^") {
        public double apply(double x, double y) {
            return Math.pow(x, y);
        }
    },
    REMAINDER("%") {
        public double apply(double x, double y) {
            return x % y;
        }
  };

    private final String symbol;
    ExtendedOperation(String symbol) {
        this.symbol = symbol;
    }
}

```

The extended enum do not have the functionalities of the "super" enum.
You have to re-write the functionality or use encapsulation.

### Item 39: Prefer annotations to naming patterns

How to define your own annotation:

```
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Test {
}
```

- @Retention(RetentionPolicy.RUNTIME) meta-annotation indicates
  that Test annotations should be retained at runtime.

- @Target.get(ElementType.METHOD) meta-annotation indicates that the
  Test annotation is legal only on method declarations

Both @Retention & @Target are called meta-annotations

What if you want to indicate that the method must throw the designated exception?

```
@Target(ElementType.METHOD)
public @interface ExceptionTest {
    Class<? extends Throwable> value();
}
```

or for multiple exceptions:

```
@Target(ElementType.METHOD)
public @interface ExceptionTest {
    Class<? extends Throwable>[] value();
}
```

### Item 40: Consistently use the Override annotation

You should use the Override annotation on every method
declaration that you believe to override a superclass declaration.
This will help to identify cases you have accidentally messed up the signature
of the method you are overriding.

Also the Override annotation may be used on method declarations that override
declarations from interfaces (default methods) as well as classes.


### Item 41: Use marker interfaces to define types

Do not use marker annotations for marker interfaces.

Marker interface is an interface that contains no method declarations but
merely designates (or “marks”) a class that implements the interface as having
some property. For example, consider the Serializable interface.

Marker interfaces define a type that is implemented by instances of the marked class; marker
annotations do not

If you define it as a marker interface, you can have it extend
the sole interface to which it is applicable, guaranteeing that all marked types are
also subtypes of the sole interface to which it is applicable. This cannot be done
in a marker annotation.

When should you use a marker annotation and when should you use a
marker interface?

Clearly you must use an annotation if the marker applies to
any program element other than a class or interface, because only classes and
interfaces can be made to implement or extend an interface

If you want to define a type that does not have any new methods associated with it,
a marker interface is the way to go. If you want to mark program elements other
than classes and interfaces or to fit the marker into a framework that already
makes heavy use of annotation types, then a marker annotation is the correct
choice.

## Chapter 8: Methods

### Item 49: Check parameters for validity

You must always check the validity of the parameters and throw exception if
they are incorrect. Also document which parameters are considered valid.

Use @throws annotation for exceptions that the method throws (checked & unchecked)

eg:
```
...
// @throws ArithmeticException if m is less than or equal to 0
...
```

**SOS:** The Objects.requireNonNull method, added in Java 7, is flexible
and convenient, so there’s no reason to perform null checks manually
anymore.

```
// "pointer cannot be null" as the exception detail message
Pointer ptr = Objects.requireNonNull(ptr, "pointer cannot be null");
```

### Item 50: Make defensive copies when needed

Date is obsolete and should no longer be used in new code, instead use Instant
(or Local-DateTime or ZonedDateTime)

```
public final class Period {
    private final Date start;
    private final Date end;

    public Period(Date start, Date end) {
        if (start.compareTo(end) > 0)
            throw new IllegalArgumentException(start + " after " + end);
        this.start = start;
        this.end = end;
    }
    public Date start() {
        return start;
    }

    public Date end() {
        return end;
    }
}

Date start = new Date();
Date end = new Date();
Period p = new Period(start, end);
end.setYear(78); // Modifies internals of p!
```

HOW????

Date is mutable and can be changed after it has been passed to the Period instance.

To fix it you must use defence copying:

```
// Repaired constructor - makes defensive copies of parameters
public Period(Date start, Date end) {
    this.start = new Date(start.getTime()); //copy of the input
    this.end = new Date(end.getTime()); //copy of the input
    if (this.start.compareTo(this.end) > 0)
        throw new IllegalArgumentException(this.start + " after " + this.end);
}

// Repaired accessors - make defensive copies of internal fields
public Date start() {
    return new Date(start.getTime());
}

public Date end() {
    return new Date(end.getTime());
}
```

You should think twice before returning a reference to an internal component that is mutable,
mutable objects can be changed by the the client and these changes will reflect on the
creator method as well.

Generally if a class has mutable components that it **gets from** or **returns to**
its clients, the class must defensively copy these components

**Java is Pass-by-value**

Unfortunately, they decided to call the location of an object a "reference".
When we pass the value of an object, we are passing the reference to it. This is confusing.

```
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    // we pass the object to foo
    foo(aDog);
    // aDog variable is still pointing to the "Max" dog when foo(...) returns
    aDog.getName().equals("Max"); // true
    aDog.getName().equals("Fifi"); // false
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // change d inside of foo() to point to a new Dog instance "Fifi"
    d = new Dog("Fifi");
    d.getName().equals("Fifi"); // true
}
```

In the example above aDog.getName() will still return "Max".
The value aDog within main is not changed in the function foo with the Dog "Fifi" as the object reference is passed by value.
If it were passed by reference, then the aDog.getName() in main would return "Fifi" after the call to foo.

```
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    foo(aDog);
    // when foo(...) returns, the name of the dog has been changed to "Fifi"
    aDog.getName().equals("Fifi"); // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // this changes the name of d to be "Fifi"
    d.setName("Fifi");
}
```

In the above example, Fifi is the dog's name after call to foo(aDog) because the object's name was set inside of foo(...).
Any operations that foo performs on d are such that, for all practical purposes,
they are performed on aDog itself (except when d is changed to point to a different Dog instance like d = new Dog("Boxer")).

### Item 51: Design method signatures carefully

- Use <= 4 parameters per method, if you find yourself with more than 4 break up the method,
use builder patter or use helper class (Java Beans) to group the parameters.

- Favor interfaces over classes, eg: prefer Map instead of HashMap.

### Item 52: Use overloading judiciously

Overloading can be confusing to API clients and should be avoided.
A safe, conservative policy is never to export two overloadings with
the same number of parameters.

You should give give methods different names instead of overloading them.

Overloading is especially dangerous with autoboxing.

```
public class SetList {
    public static void main(String[] args) {
        Set<Integer> set = new TreeSet<>();
        List<Integer> list = new ArrayList<>();

        for (int i = -3; i < 3; i++) {
            set.add(i);
            list.add(i);}

    for (int i = 0; i < 3; i++) {
        set.remove(i);
        list.remove(i);}

    System.out.println(set + " " + list);
}}
```

This will print:

[-3, -2, -1] [-2, 0, 2].

This is because in the list.remove(i), selects the overloading remove(int i),
which removes the element at the specified position in the list.


### Item 53: Use varargs judiciously

The varargs facility works by first creating an array whose size is the number of arguments
passed at the call site, then putting the argument values into the array,
and finally passing the array to the method.

- Every invocation of a varargs method causes an array allocation and initialization.
This may cause performance issues.
- There do no go well with generics.

### Return empty collections or arrays, not nulls

For Collections it is preferable to return empty collection instead of null
you can use these for convenience:

```
Collections.emptyList
Collections.emptySet
Collections.emptyMap
```

The same advise should be used and when return an array.

### Item 55: Return optionals judiciously

When things go south you had 2 options: throw an exception, return null.

In Java 8 you can use Optional\<T>, it represents an immutable container that
can hold either a single non-null T reference or nothing at all

To return an optional:
```
Optional.empty() //empty Optional
Optional.of(value) //non empty Optional
```

Optionals are similar in spirit to checked exceptions,
in that they force the user of an API to confront the fact that there may
be no value returned.

Container types, including collections, maps, streams, arrays, and optionals should not be
wrapped in optionals. Rather than returning an empty
Optional<List\<T>>, you should simply return an empty List\<T>

An Optional is an object that has to be allocated and
initialized, and reading the value out of the optional requires an extra indirection.
This makes optionals inappropriate for use in some performance-critical
situations.

You should never return an optional of a boxed primitive type. Boxed primitive type is prohibitively
expensive compared to returning a primitive type because the optional has two
levels of boxing instead of zero.

There are special optional for primitive types: OptionalInt, OptionalLong, and OptionalDouble.

Generally, if you find yourself writing a method that can’t always return a
value and you believe it is important that users of the method consider this
possibility every time they call it, then you should probably return an optional.
Finally, you should rarely use an optional in any other capacity than as a return value.