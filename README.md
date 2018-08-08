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
* [Chapter 4: Classes and Interfaces](#chapter-4-classes-and-interfaces)
    * [Item 15: Minimize the accessibility of classes and members](#item-15-minimize-the-accessibility-of-classes-and-members)
    * [Item 16: In public classes, use accessor methods, not public fields](#item-16-in-public-classes-use-accessor-methods-not-public-fields)
    * [Item 17: Minimize mutability](#item-17-minimize-mutability)
    * [Item 18: Favor composition over inheritance](#item-18-favor-composition-over-inheritance)
    * [Item 19: Design and document for inheritance or else prohibit it](#item-19-design-and-document-for-inheritance-or-else-prohibit-it)
    * [Item 20: Prefer interfaces to abstract classes](#item-20-prefer-interfaces-to-abstract-classes)
    * [Item 21: Design interfaces for posterity (future generations)](#item-21-design-interfaces-for-posterity-future-generations)
    * [Item 22: Use interfaces only to define types](#item-22-use-interfaces-only-to-define-types)
    * [Item 23: Prefer class hierarchies to tagged classes](#item-23-prefer-class-hierarchies-to-tagged-classes)
    * [Item 24: Favor static member classes over nonstatic](#item-24-favor-static-member-classes-over-nonstatic)
    * [Item 25: Limit source files to a single top-level class](#item-25-limit-source-files-to-a-single-top-level-class)
* [Chapter 5: Generics](#chapter-5-generics)
    * [Item 26: Don’t use raw types](#item-26-dont-use-raw-types)
    * [Item 27: Eliminate unchecked warnings](#item-27-eliminate-unchecked-warnings)
    * [Item 28: Prefer lists to arrays](#item-28-prefer-lists-to-arrays)
    * [Item 29: Favor generic types](#item-29-favor-generic-types)
    * [Item 30: Favor generic methods](#item-30-favor-generic-methods)
    * [Item 31: Use bounded wildcards to increase API flexibility](#item-31-use-bounded-wildcards-to-increase-api-flexibility)
    * [Item 32: Combine generics and varargs judiciously](#item-32-combine-generics-and-varargs-judiciously)
    * [Item 33: Consider typesafe heterogeneous containers](#item-33-consider-typesafe-heterogeneous-containers)
* [Chapter 6: Enums and Annotations](#chapter-6-enums-and-annotations)
    * [Item 34: Use enums instead of int constants](#item-34-use-enums-instead-of-int-constants)
    * [Item 35: Use instance fields instead of ordinals](#item-35-use-instance-fields-instead-of-ordinals)
    * [Item 36: Use EnumSet instead of bit fields](#item-36-use-enumset-instead-of-bit-fields)
    * [Item 37: Use EnumMap instead of ordinal indexing](#item-37-use-enummap-instead-of-ordinal-indexing)
    * [Item 38: Emulate extensible enums with interfaces](#item-38-emulate-extensible-enums-with-interfaces)
    * [Item 39: Prefer annotations to naming patterns](#item-39-prefer-annotations-to-naming-patterns)
    * [Item 40: Consistently use the override annotation](#item-40-consistently-use-the-override-annotation)
    * [Item 41: Use marker interfaces to define types](#item-41-use-marker-interfaces-to-define-types)
* [Chapter 7: Lambdas and Streams](#chapter-7-lambdas-and-streams)
    * [Item 42: Prefer lambdas to anonymous classes](#item-42-prefer-lambdas-to-anonymous-classes)
    * [Item 43: Prefer method references to lambdas](#item-43-prefer-method-references-to-lambdas)
    * [Item 44: Favor the use of standard functional interfaces](#item-44-favor-the-use-of-standard-functional-interfaces)
    * [Item 45: Use streams judiciously](#item-45-use-streams-judiciously)
    * [Item 46: Prefer side-effect-free functions in streams](#item-46-prefer-side-effect-free-functions-in-streams)
    * [Item 47: Prefer Collection to Stream as a return type](#item-47-prefer-collection-to-stream-as-a-return-type)
    * [Item 48: Use caution when making streams parallel](#item-48-use-caution-when-making-stream-parallel)
* [Chapter 8: Methods](#chapter-8-methods)
    * [Item 49: Check parameters for validity](#item-49-check-parameters-for-validity)
    * [Item 50: Make defensive copies when needed](#item-50-make-defensive-copies-when-needed)
    * [Item 51: Design method signatures carefully](#item-51-design-method-signatures-carefully)
    * [Item 52: Use overloading judiciously](#item-52-use-overloading-judiciously)
    * [Item 53: Use varargs judiciously](#item-53-use-varargs-judiciously)
    * [Item 54: Return empty collections or arrays, not nulls](#item-54-return-empty-collections-or-arrays-not-nulls)
    * [Item 55: Return optionals judiciously](#item-55-return-optionals-judiciously)
    * [Item 56: Write doc comments for all exposed API elements](#item-56-write-doc-comments-for-all-exposed-api-elements)
* [Chapter 9: General Programming](#chapter-9-general-programming)
    * [Item 57: Minimize the scope of local variables](#item-57-minimize-the-scope-of-local-variables)
    * [Item 58: Prefer for-each loops to traditional for loops](#item-58-prefer-for-each-loops-to-traditional-for-loops)
    * [Item 59: Know and use the libraries](#item-59-know-and-use-the-libraries)
    * [Item 60: Avoid float and double if exact answers are required](#item-60-avoid-float-and-double-if-exact-answers-are-required)
    * [Item 61: Prefer primitive types to boxed primitives](#item-61-prefer-primitive-types-to-boxed-primitives)
    * [Item 62: Avoid strings where other types are more appropriate](#item-62-avoid-strings-where-other-types-are-more-appropriate)
    * [Item 63: Beware the performance of string concatenation](#item-63-beware-the-performance-of-string-concatenation)
    * [Item 64: Refer to objects by their interfaces](#item-64-refer-to-objects-by-their-interfaces)
    * [Item 65: Prefer interfaces to reflection](#item-65-prefer-interfaces-to-reflection)
    * [Item 66: Use native methods judiciously](#item-66-use-native-methods-judiciously)
    * [Item 67: Optimize judiciously](#item-67-optimize-judiciously)
    * [Item 68: Adhere to generally accepted naming conventions](#item-68-adhere-to-generally-accepted-naming-conventions)
* [Chapter 10: Exceptions](#chapter-10-exceptions)
    * [Item 69: Use exceptions only for exceptional conditions](#item-69-use-exceptions-only-for-exceptional-conditions)
    * [Item 70: Use checked exceptions for recoverable conditions and runtime exceptions for programming errors](#item-70-use-checked-exceptions-for-recoverable-conditions-and-runtime-exceptions-for-programming-errors)
    * [Item 71: Avoid unnecessary use of checked exceptions](#item-71-avoid-unnecessary-use-of-checked-exceptions)
    * [Item 72: Favor the use of standard exceptions](#item-72-favor-the-use-of-standard-exceptions)
    * [Item 73: Throw exceptions appropriate to the abstraction](#item-73-throw-exceptions-appropriate-to-the-abstraction)
    * [Item 74: Document all exceptions thrown by each method](#item-74-document-all-exceptions-thrown-by-each-method)
    * [Item 75: Include failure-capture information in detail messages](#item-75-include-failure-capture-information-in-detail-messages)
    * [Item 76: Strive for failure atomicity](#item-76-strive-for-failure-atomicity)
    * [Item 77: Don’t ignore exceptions](#item-77-dont-ignore-exceptions)
* [Chapter 11: Concurrency](#chapter-11-concurrency)
    * [Item 78: Synchronize access to shared mutable data](#item-78-synchronize-access-to-shared-mutable)
    * [Item 79: Avoid excessive synchronization](#item-79-avoid-excessive-synchronization)
    * [Item 80: Prefer executors, tasks, and streams to threads](#item-80-prefer-executors-tasks-and-streams-to-threads)
    * [Item 81: Prefer concurrency utilities to wait and notify](#item-81-prefer-concurrency-utilities-to-wait-and-notify)
    * [Item 82: Document thread safety](#item-82-document-thread-safety)
    * [Item 83: Use lazy initialization judiciously](#item-83-use-lazy-initialization-judiciously)
    * [Item 84: Don’t depend on the thread scheduler](#item-84-dont-depend-on-the-thread-scheduler)
* [Chapter 12. Serialization](#chapter-12-serialization)
    * [Item 85: Prefer alternatives to Java serialization](#item-85-prefer-alternatives-to-java-serialization)
    * [Item 86: Implement Serializable with great caution](#item-86-implement-serializable-with-great-caution)
    * [Item 87: Consider using a custom serialized form](#item-87-consider-using-a-custom-serialized-form)
    * [Item 88: Write readObject methods defensively](#item-88-write-readobject-methods-defensively)
    * [Item 89: For instance control, prefer enum types to readResolve](#item-89-for-instance-control-prefer-enum-types-to-readresolve)
    * [Item 90: Consider serialization proxies instead of serialized instances](#item-90-consider-serialization-proxies-instead-of-serialized-instances)

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

**Difference between static class and singleton pattern?**

A singleton allows access to a single created instance - that instance (or rather, a reference to that instance)
can be passed as a parameter to other methods, and treated as a normal object.

A static class allows only static methods.

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

### Item 7: Eliminate obsolete object references

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

### Item 8: Avoid finalizers and cleaners

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

Providing a good toString implementation makes your class much more pleasant
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
comparison, and that’s exactly what the second comparator method, thenComparingInt, does.


## Chapter 4: Classes and Interfaces

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
- **public**.

Private & Package private members are part of class's implementation and do not impact the
exposed API.

Why minimize the expose of members, classes?

1) Decouples components.
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
1) Don’t provide methods that modify the object’s state. *(Check Item 50 for more information about pass-by-value)*
2) Ensure that the class can’t be extended (Make the class final or make the constructor private, the latest is better because
it allows for future refactoring, by adding a new inner subclass).
3) Make all fields final (you can have non-final fields as long as you control the access to it and return only
cached results, to avoid the recalculation cost).
4) Make all fields private. To avoid clients obtaining access to a field and modifying it.
5) Ensure exclusive access to any mutable components. If a field is mutable make sure that the
client cannot obtain a reference to these objects, make defensive copies in constructors, accessors. *(Check Item 50 for more information about pass-by-value)*

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
- You do not need Cloneable if a object is immutable.
- They make great building blocks for other objects.

If you cannot make the class immutable limit it's immutability as much as possible

What about the performance overhead of all those object, since an immutable objects
requires a new instance for every different state it is?

This is something to take into consideration, if the object is small make it immutable,
if it is large try to make it as immutable as possible ( by making fields final etc...).
Also you can internally use a package-private mutable companion class that it uses to speed up expensive computations

**Tip: ** When creating a new class start by making everything immutable (and inaccessible) change only the things that you need to make them
mutable (& accessible)

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
    .
    .
    .

    @Override public boolean equals(Object o) { return s.equals(o); }
    @Override public int hashCode() { return s.hashCode(); }
    @Override public String toString() { return s.toString(); }
}
```

The advantages of this approach is that the forwarding class can be used by many classes that may want to
compose the Set\<E> Interface. This approach is a decorator pattern.

### Item 19: Design and document for inheritance or else prohibit it

How to design for inheritance:

1) The class must document its self-use of overridable methods.

2) You should add hooks into its internal workings in the form of judiciously chosen protected methods. The subclass can
use these methods (hooks) more easily than overriding and rewriting parts of the superclass.

You will need to commit forever to these 2 patterns (documentation, hooks).


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

1) Study the interface and decide which methods are the primitives in
terms of which the others can be implemented. These primitives will be the
abstract methods in your skeletal implementation.

2) Provide default methods in the interface for all of the methods that can be implemented directly atop the
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

How to transform tagged classes to hierarchy:

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

**Tip: ** As we said before make your inner class static at creation and remove static if you
really need to as you develop further.

### Item 25: Limit source files to a single top-level class

Never put multiple top-level classes or interfaces in a single source file.

Following this rule guarantees that you can’t have multiple
definitions for a single class at compile time. This in turn guarantees that the
class files generated by compilation, and the behavior of the resulting program,
are independent of the order in which the source files are passed to the compiler.

## Chapter 5: Generics

### Item 26: Don’t use raw types

Raw type of List\<E> is List. Raw types behave as if all of
the generic type information were erased from the type declaration.
They exist primarily for compatibility with pre-generics code.

With generics you can control what instance can be inserted into your datastructure.
If you use raw types, you lose all the safety and expressiveness benefits of generics

**What is the difference between the raw type List and the parametrized type List\<Object>?**

While you can pass a List\<String> to a parameter of type List, you can’t pass it to a parameter
of type List\<Object>.

If you want to use a generic type but you don’t know or care what the actual type parameter is,
you can use a question mark instead.

eg: Set<?>

It is the most general parametrized Set type, capable of holding any set.

There are two facts about Set<?>:

- Since the question mark ? stands for any type. Set<?> is capable of holding any type of elements.
- Because we don't know the type of ?, we can't put any element into Set<?>. (You can only retrieve from it)

** What is the difference between the unbounded wildcard type Set<?> and the
raw type Set?**

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

```printSet2``` method would be legal if the argument was ```Set``` and not ```Set<?>```
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
- if a parameterized type represents a T producer, use **<? extends T>**
- if it represents a T consumer, use **<? super T>**.

But keep in mind you should never use bounded wildcard types as return types.
This force the client to use wildcard types too.

- Use Comparable<? super T> in preference to Comparable\<T>.
- Use Comparator<? super T> in preference to Comparator\<T>

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

**Why to avoid int constants?**
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

You can also do more complex nested maps:
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

### Item 40: Consistently use the override annotation

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

**When should you use a marker annotation and when should you use a
marker interface?**

Clearly you must use an annotation if the marker applies to
any program element other than a class or interface, because only classes and
interfaces can be made to implement or extend an interface.

If you want to define a type that does not have any new methods associated with it,
a marker interface is the way to go. If you want to mark program elements other
than classes and interfaces or to fit the marker into a framework that already
makes heavy use of annotation types, then a marker annotation is the correct
choice.

## Chapter 7: Lambdas and Streams

### Item 42: Prefer lambdas to anonymous classes

Lambda expression is composed by 3 parts:

- The list of parameters ```(Type1 t1, Type2 t2)```
- An arrow ```->``` it separates teh patameters from the body
- The Lambda body ```t1.getX().compareTo(t2.getX())```

 ```(Type1 t1, Type2 t2) -> t1.getX().compareTo(t2.getX())```


**Where to use lambda expressions?**

You can use a lambda expression in the context of a functional interface.

Functional Interface is a interfaces annotated with @FunctionInterface that has only one
abstract method (it may have several default or static methods).

*Example: behavior parameterization*: You may have multiple implementation of one interface you can create an anonymous class and implement the interface
or you can create a lambda expression (faster and without boilerplate code). As long as the interface is a functional interface.

**Type checking**

The type of a lambda is deduced from the context in which the lambda is used. As a result he same lambda expression can
be associated with different functional interfaces if they have a compatible abstract method signature.

eg:

```
Callable<Integer> c = () -> 42;
PrivilegedAction<Integer> p = () -> 42;
```

Omit the types of all lambda parameters unless their presence makes your program clearer

**Exceptions**

Lambdas can throw checked exceptions but non of the default functional interfaces provided by the JDK support one,
so you will need to create one
eg:

```
@FunctionalInterface
public interface BufferedReaderProcessor {
    String process(BufferedReader b) throws IOException;
}
BufferedReaderProcessor p = (BufferedReader br) -> br.readLine();
```

**Using local variables**

Lambdas can access local variables as long as they are final or effective final
eg:

```
final int portNumber = 1337;
Runnable r = () -> System.out.println(portNumber); //works because portNumber is final

int portNumber2 = 1337;
Runnable r2 = () -> System.out.println(portNumber2); //works because portNumber2 is effective final since it does not change after instantiation

int portNumber3 = 1337;
Runnable r3 = () -> System.out.println(portNumber3); //Does not work because portNummber3 in not final or effective final
int portNumber3 = 8080;

```

**Useful methods**

Several functional interfaces in the Java 8 API contain convenient default methods.

*Ordering*
```
Comparator.comparing(Apple::getWeight);
//or
list.sort(comparing(Apple::getWeight).reversed();
```

*Chaining*

```
Function<Integer, Integer> f = x+1;
Function<Integer, Integer> g = x*2;
Function<Integer, Integer> r = f.compose(g); // If x = 1, r = 3, f(g(1))
Function<Integer, Integer> r2 = f.andThe(g); // if x = 1, r2 = 4, g(f(1))

```


Lambdas should be one line long or self-explanatory, if this is not true use a classic class to
make the code cleaner to read and maintain.

And lastly if you do not have a functional interface you must use anonymous method like before.

### Item 43: Prefer method references to lambdas

There is nothing you can do with lambda that you cannot do with method references.
Where method references are shorter and clearer, use them; where they aren’t, stick with lambdas.

|Method type|Example| Lambda|
|:---|:----|:---|
|Static |```Integer::parseInt ```|```str -> Integer.parseInt(str)```|
|Bound |```Instant.now()::isAfter``` |```Instant then = Instant.now(); t -> then.isAfter(t)```|
|Unbound |```String::toLowerCase```| ```str -> str.toLowerCase()```|
|Class Constructor| ```TreeMap<K,V>::new ```|```() -> new TreeMap<K,V>```|
|Array Constructor| ```int[]::new ```|```len -> new int[len]```


If the constructor takes multiple arguments you can use method reference and the arguments will be deduced
by the context.

eg:

```
@FunctionalInterface
public interface TriFunction<T, U, V, R>{
    R apply(T t, U u, V v);
}

TriFunction<Integer, Integer, Integer, Color> colorFactory = Color::new;
```


### Item 44: Favor the use of standard functional interfaces

If one of the standard functional interfaces does the job, you should
generally use it in preference to a purpose-built functional interface.

**Common functional interfaces in Java 8**

|Functional interface|Function descriptor| Primitive specializations |
|:---|:----|:---|
|Predicate\<T>|T -> boolean|IntPredicate, LongPredicate, DoublePredicate |
|Consumer\<T>|T -> void| IntConsumer, LongConsumer, DoubleConsumer |
|Function\<T, R>|T -> R| IntFunction\<R>, IntToDoubleFunction, IntToLongFunction, LongFunction\<R>, LongToDoubleFunction, LongToIntFunction, DoubleFunction\<R>, ToIntFunction\<T>, ToDoubleFunction\<T>, ToLongFunction\<T>|
|Supplier\<T>|() -> T| BooleanSupplier, IntSupplier, LongSupplier, DoubleSupplier |
|UnaryOperator\<T>|T -> T| IntUnaryOperator, LongUnaryOperator, DoubleUnaryOperator |
|BinaryOperator\<T>|(T, T) -> T| IntBinaryOperator, LongBinaryOperator, DoubleBinaryOperator |
|BiPredicate\<L, R>| (L, R) -> boolean| |
|BiConsumer\<T, U>| (T, U) -> void | ObjIntConsumer\<T>, ObjLongConsumer\<T>, ObjDoubleConsumer\<T>|
|BiFunction\<T, U, R>| (T, U) -> R |ToIntBiFunction\<T, U>, ToLongBiFunction\<T, U>, ToDoubleBiFunction\<T, U>|

With primitives use the specialized interfaces provided by the JDK, to avoid the cost off auto-boxing/unboxing.

Sometimes you may need to provide your own functional interface even if the signatures matches a existing one this
can happen for 2 reasons:
1) Descriptive name for self-documentation.
2) It can benefit from custom default methods.


### Item 45: Use streams judiciously

Stream is a sequence of elements from a source that supports data processing operations

A collection is an in-memory data structure that holds all the values the data
structure currently has—every element in the collection has to be computed before it can be
added to the collection.

By contrast, a stream is a conceptually fixed data structure (you can’t add or remove elements
from it) whose elements are computed on demand.

Keep in mind that a stream can be traversed only once. After that a stream is said
to be consumed.

eg:

```
Stram<String> s= titles.stream();
s.forEach(System.out::println)
s.forEach(System.out::println) //Will throw IllegalStateException since the stream is already consumed
```

Complex streams should be avoided and replaced with iterative style programming, to make them
easier to read/write and specialy to maintain.

To increase the readability & maintainability of stream:
- In the absence of explicit types, careful naming of lambda parameters is essential.
- Use helper method whenever possible.

If you need to:
- Modify external variables
- Throw checked exceptions
- Use continue, break in a loop
- Return from an enclosing method

Prefer the iterative approach since none of these is possible in streams!

#### A comprehensive guide to streams

**Stream common operations**

Stream operations that can be connected are called *intermediate* operations (they return Stream<>), and operations
that close a stream are called *terminal* operations.

Intermediate operations don’t perform any processing until a terminal operation is invoked on the stream
pipeline—they’re lazy.

*Intermediate operations*:

|Operation|Return type|Argument|Functional Descriptor| Purpose|
|:---|:---|:---|:---|:---|
|filter|Stream\<T>| Predicate\<T>|T -> boolean|Filter out data|
|map|Stream\<R>|Function\<T, R>|T -> R|Transform data|
|limit|Stream\<T>|||Limit data count|
|sorted|Stream\<T>|Comparator\<T>|(T, T) -> int| Sorts data|
|distinct|Stream\<T>|||Return all distinct data|
|skip|Stream\<T>|long||skip first elements|
|flatMap|Stream\<R>|Function<T, Stream\<R>>|T -> Stream<R>| flattens the nested Stream and perform a map operaiton|

*Terminal operations*:

|Operation|Purpose|
|:---|:---|
|forEach|Consumes each element from a stream and applies a lambda to each of them. The operation returns void.|
|count|Returns the number of elements in a stream. The operation returns a long.|
|collect|Reduces the stream to create a collection such as a List, a Map, or even an Integer|
|anyMatch| Returns true if at least one value of stream returns true (when used in lambda)|
|noneMatch| Returns true if non of the stream values returns true (when used in lambda)|
|allMatch| Returns true if all values of stream returns true (when used in lambda)|
|findAny| Returns an Optional that may contain a random value of the stream|
|findFirst|Returns an Optional that may contain the first value of the stream|
|reduce| Performs reduction operation (like sum, product ...) to the stream|

**Operations in depth**

*Filter*

Takes as argument a predicate (a function returning a boolean) and returns a stream
including all elements that match the predicate
```
List<Dish> vegetarianMenu = menu.stream()
                                .filter(Dish::isVegeterian)
                                .collect(toList()); //toList() is statically import default method of the Collection interface
```

*Distinct*

Returns a stream with unique elements (according to the implementation of the hashCode
and equals methods of the objects produced by the stream)

```
numbers.stream()
       .filter(i -> i % 2 == 0)
       .distinct()
       .forEach(System.out::println);
```

*Limit*

Returns another stream that’s no longer than a
given size

```
List<Dish> shortMenu = menu.stream()
                       .limit(3) //only first 3 elements will be added
                       .collect(toList());
```

*Skip*

Return a stream that discards the first n elements.
```
List<Dish> shortMenu = menu.stream()
                       .skip(3) //first 3 elements will be skipped.
                       .collect(toList());
```

*Map*

Takes a function as argument. The function is applied to each element, mapping it into a new element.
At the end a new stream is created.

```
List<String> dishNames = menu.stream()
                             .map(Dish::getName)
                             .collect(toList());
```

*FlatMap*

FlatMap method lets you replace each value of a stream with another stream
and then concatenates all the generated streams into a single stream.

```
List<List<String>> list = Arrays.asList(
  Arrays.asList("a","c","d"),
  Arrays.asList("b","f"));

list.stream()
    .flatMap(Collection::stream)
    .collect(Collectors.toList());
```

The flatMap() method first flattens the input Stream of Streams to a Stream of Strings.
Thereafter it works similarly to the map() method.

*anyMatch, allMatch, noneMatch*

- anyMatch method can be used to answer the question “Is there an element in the stream matching the given predicate?”
- allMatch method works similarly to anyMatch but will check to see if all the elements of the stream match the given predicate
- It ensures that no elements in the stream match the given predicate.


```
menu.stream().anyMatch(Dish::isVegetarian); //returns true if there is at least one dish that is vegetarian
menu.stream().allMatch(d -> d.getCalories() < 1000); //returns true if all dishes are bellow 1000 calories
menu.stream().noneMatch(d -> d.getCalories() > 1000); //returns true if there is no dish above 1000 calories
```


*findAny*

Returns an arbitrary element of the current stream, it returns an Optional that forces the client
to handle the case that the Stream is empty.

```
menu.stream()
    .filter(Dish::isVegetarian)
    .findAny()
    .ifPresent(d ->System.out.Println(d.getName()))

```

*reduce*

With reduce you can add/multiply/divide etc. all elements. It takes 2 arguments:
- an initial value
- a BinaryOperator\<T> to combine 2 elements and produce a new value

```
int sum = numbers.stream().reduce(0,(a,b) -> a + b);
int produt = numbers.stream().reduce(1,(a,b) -> a * b);
```

Compute max, min with reduce

```
int max = numbers.stream().reduce(0,Integer::max);
int min = numbers.stream().reduce(0,Integer::min);

//or
int max = numbers.stream().reduce(0,(x,y)->x>y?x:y);
int min = numbers.stream().reduce(0,(x,y)->x<y?x:y);

```

**Primitive stream specializations**

- IntStream
- DoubleStream
- LongStream


*mapToInt, mapToDouble, mapToLong.*

Are used to create primitive stream from complex objects.

```
IntStream intStream = menu.stream().mapToInt(Dish::getCalories);

int sum = intStream.sum()
```

*max*

Returns an primitive specialisation of Optional (OptionalInt, OptionalLong, OptionalDouble).
Can only be used with primitive streams.

*sum*

Returns the sum of a primitive stream

*range, rangeClosed*

Both methods take the starting value of the range as the first parameter and the
end value of the range as the second parameter. But range is exclusive, whereas rangeClosed is
inclusive.


**Creating a Stream**


You can use *Stream.of* to create a stream.

eg:
```
Stream<String> stream = Stream.of("Java 8 ", "Lambdas ", "In ", "Action");
```

From an array you can do:

```
int[] numArray = {2,3,4,5,6}
IntStream stream = Arrays.stream(numArray)
```

You can also create streams from files.

Create an infinite stream:

- The *iterate* method takes an initial value, here 0, and a lambda (of type Unary-Operator\<T>) to
  apply successively on each new value produced
- The *generate* method takes a lambda of type Supplier\<T> to provide new values
```
Stream.iterate(0, n -> n + 2)
      .limit(10)
      .forEach(System.out::println);

Stream.generate(Math::random)
      .limit(5)
      .forEach(System.out::println);
```

**Collectors interface**

*Collectors.maxBy, Collectors.minBy*

These two collectors take a Comparator as argument to compare the elements in the stream.

```
Comparator<Dish> dishCaloriesComparator = Comparator.comparingInt(Dish::getCalories);
Optional<Dish> mostCalorieDish = menu.stream().collect(maxBy(dishCaloriesComparator)); //Optional in cas the menu is empty
```


*Collectors.summingInt, Collectors.summingLong, Collectors.summingDouble*
*Collectors.averagingInt, Collectors.averagingLong, Collectors.averagingDouble*

It accepts a function that maps an object into the int that has to be summed/averaged.

```
int totalCalories = menu.stream().collect(summingInt(Dish::getCalories));
double avgCalories = menu.stream().collect(averagingInt(Dish::getCalories));
```

*Collectors.summarizingInt, Collectors.summarizingLong, Collectors.summarizingDouble*

It obtains the sum, average, maximum, and minimum.

```
IntSummaryStatistics menuStatistics = menu.stream().collect(summarizingInt(Dish::getCalories));

IntSummaryStatistics{count=9, sum=4300, min=120, average=477.777778, max=800}
```

*Collectors.joining*

Concatenates into a single string all strings resulting from invoking the toString method on each object in the stream,
it uses StringBuilder.

```
String shortMenu = menu.stream().map(Dish::getName).collect(joining());
String shortMenu = menu.stream().map(Dish::getName).collect(joining(", "));
```


*Collectors.groupingBy*

The method takes a Function as input that is used to classify (separate) the elements, the result is a Map
that has a key the value that is returned by the classification function and value a list of all the items in the stream having
that classified value.

```
Map<Dish.Type, List<Dish>> dishesByType = menu.stream().collect(groupingBy(Dish::getType));

/*
It returns:
{FISH=[prawns, salmon], OTHER=[french fries, rice, season fruit, pizza], MEAT=[pork, beef, chicken]}
*/
```

If you want you can use the overloaded groupBy method that takes 2 arguments the first is the classification method, and the other
is a Collector type.

```
Map<Dish.Type, Long> typesCount = menu.stream().collect( groupingBy(Dish::getType, counting()));
/*
    The result is the following Map:
    {MEAT=3, FISH=2, OTHER=4}
*/
```

*Collectors.partitioningBy*

Takes a Predicate as argument and is used as a partitioning function. This is basically a grouping function
that group in key=true the values that return true, and in key=false the values that return false.

```
Map<Boolean, List<Dish>> = menu.stream().collect(partitioningBy(Dish::isVegeterian))

/*
Returns the following map:
{false=[pork, beef, chicken, prawns, salmon],
true=[french fries, rice, season fruit, pizza]}
*/
```

**Collector interface**

The Collector interface consists of a set of methods that provide a blueprint for how to
implement specific reduction operations (that is, collectors), toList and groupingBy are some that
implement the Collector interface.

You can develop your own collectors by implementing the methods defined in the Collector interface.

### Item 46: Prefer side-effect-free functions in streams

The forEach operation should be used only to report the result of a stream computation,
not to perform the computation.

Use the method provide by the ```Collectors``` interface whenever possible.

### Item 47: Prefer Collection to Stream as a return type

When writing a method that returns a sequence of elements,
remember that some of your users may want to process them as a stream while
others may want to iterate over them.

Collection or an appropriate subtype is generally the best return type
for a public, sequence-returning method, because it is a subtype of Iterable and has a stream method

### Item 48: Use caution when making streams parallel

*parallel*

With the use of parallel method the stream is internally divided into multiple chunks that
will run in parallel.

Parallelizing a pipeline is unlikely to increase its performance
if the source is from Stream.iterate, or the intermediate operation limit is used.

As a rule, performance gains from parallelism are best on streams over
ArrayList, HashMap, HashSet, and ConcurrentHashMap instances;
arrays; int ranges; and long ranges. Generally if a data structures can all accurately and cheaply split into
subranges of any desired sizes, it makes it easy to divide work among parallel threads.

It is important to remember that some stream operations are more parallelizable than others. It is crucial to
benchmark the code when trying to use ```parallel()```

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

### Item 54: Return empty collections or arrays, not nulls

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


### Item 56: Write doc comments for all exposed API elements

Javadoc generates API documentation automatically from source code
with specially formatted documentation comments, more commonly known as
doc comments.

To document your API properly, you must precede every exported class,
interface, constructor, method, and field declaration with a doc comment.

Comments should describe what the method does and not how it does it, only exception
are method in classes designed for inheritance.

eg:
```
/**
* Returns the element at the specified position in this list.    <-SUMMARY
*
*<p>This method is <i>not</i> guaranteed to run in constant      <-Further explanation/clarification
* time. In some implementations it may run in time proportional
* to the element position.
*
*@param index index of element to return; must be                <-PARAMETER #1
* non-negative and less than the size of this list
* @return the element at the specified position in this list     <- What it returns
* @throws IndexOutOfBoundsException if the index is out of range <- Exception thrown
* ({@code index < 0 || index >= this.size()})
*/
E get(int index);
```

If you want to describe how a method works (for inheritance percusses) you can use:

@impSpec annotation:

```
/**
* Returns true if this collection is empty.
*
*@implSpec
* This implementation returns {@code this.size() == 0}.
*
*@return true if this collection is empty
*/
public boolean isEmpty() { ... }
```

In enums it is best to document all constants:

```
/**
* An instrument section of a symphony orchestra.
*/
public enum OrchestraSection {
    /** Woodwinds, such as flute, clarinet, and oboe. */
    WOODWIND,
    /** Brass instruments, such as french horn and trumpet. */
    BRASS;
}
```

## Chapter 9: General Programming

### Item 57: Minimize the scope of local variables

The most powerful technique for minimizing the scope of a local variable
is to declare it where it is first used.

You can declare multiple variables with for statement:

```
for (int i = 0, n = expensiveComputation(); i < n; i++) {
    ... // Do something with i;
}
```

Most importantly you should keep methods small and focused.

### Item 58: Prefer for-each loops to traditional for loops

for-each loop provides compelling advantages over the
traditional for loop in clarity, flexibility, and bug prevention, with no
performance penalty. Use for-each loops in preference to for loops wherever
you can.

### Item 59: Know and use the libraries

Keep up to date with new libraries of Java, don’t reinvent the wheel.

### Item 60: Avoid float and double if exact answers are required

The float and double types are particularly ill-suited for monetary calculations,
because it is impossible to represent 0.1 (or any other negative power of ten)
as a float or double exactly.


eg:

```
System.out.println(1.00 - 9 * 0.10);
```
Prints 0.09999999999999998.

The right way to solve monetary problems is to use BigDecimal, int, or long.
BigDecimal it a lot slower than int and long, so if you care about performance,
keep track of the track of the decimal point yourself use int or long.

If quantities don’t exceed nine decimal digits, you can use int; if they don’t
exceed eighteen digits, you can use long. If the quantities might exceed
eighteen digits, use BigDecimal.

### Item 61: Prefer primitive types to boxed primitives

Every primitive type has a corresponding reference type, called a boxed primitive. The
boxed primitives corresponding to int, double, and boolean are Integer,
Double, and Boolean.

There are 2 major differences between primitives and boxed primitives.

1) Primitives have only their values, whereas boxed primitives have identities
  distinct from their values. In other words, two boxed primitive instances can
  have the same value and different identities. This means that applying the == operator
  to boxed primitives will almost always fail.

2) Primitives are more time- and space efficient than boxed primitives.


When your program does mixed-type computations
involving boxed and unboxed primitives, it does unboxing, and when your
program does unboxing, it can throw a NullPointerException

Also when your program boxes primitive values, it can result in costly and
unnecessary object creations

### Item 62: Avoid strings where other types are more appropriate

Avoid the natural tendency to represent objects as strings when
better data types exist or can be written. Used inappropriately, strings are more
cumbersome, less flexible, slower, and more error-prone than other types. Types
for which strings are commonly misused include primitive types, enums, and
aggregate types.

### Item 63: Beware the performance of string concatenation

Using the string concatenation operator (+) repeatedly to concatenate n strings
requires time quadratic in n. This is an unfortunate consequence of the fact
that strings are immutable. When two strings are concatenated, the
contents of both are copied.

To achieve acceptable performance, use a StringBuilder in place of a String

### Item 64: Refer to objects by their interfaces

If appropriate interface types exist, then parameters, return values,
variables, and fields should all be declared using interface types.
The only time you really need to refer to an object’s class is when you’re creating it
with a constructor.

This will make the switching implementations quite easy.

### Item 65: Prefer interfaces to reflection

1) You lose all the benefits of compile-time type checking, if a program attempts
to invoke a nonexistent or inaccessible method reflectively,
it will fail at runtime unless you’ve taken special precautions.

2) The code required to perform reflective access is clumsy and verbose.

3) Performance suffers. Reflective method invocation is much slower than
   normal method invocation.


If you need to  use a class that is unavailable at compile time, use a
appropriate interface or superclass by which to refer to the class.

### Item 66: Use native methods judiciously

The Java Native Interface (JNI) allows Java programs to call native methods,
which are methods written in native programming languages such as C or C++.

It is rarely advisable to use native methods for improved performance. In
early releases (prior to Java 3), it was often necessary, but JVMs have gotten
much faster since then.

Native code has many disadvantages:

1) Native languages are not safe, applications using native methods are no longer
   immune to memory corruption errors

2) They are also harder to debug

3) May decrease performance because the garbage collector can’t automate.


### Item 67: Optimize judiciously

Do not strive to write fast programs—strive to write good ones;
speed will follow. But do think about performance while you’re designing
systems, especially while you’re designing APIs, wire-level protocols, and
persistent data formats. When you’ve finished building the system, measure its
performance. If it’s fast enough, you’re done. If not, locate the source of the
problem with the aid of a profiler and go to work optimizing the relevant parts of
the system.

### Item 68: Adhere to generally accepted naming conventions

Type parameter names usually consist of a single letter. Most commonly it is
one of these five: ```T``` for an arbitrary type, ```E``` for the element type of a collection, ```K```
and ```V``` for the key and value types of a map, and ```X``` for an exception. The return
type of a function is usually ```R```. A sequence of arbitrary types can be ```T, U, V``` or
```T1, T2, T3```.


Common names for static factories include ```from```, ```of```, ```valueO```f, ```instance```, ```getInstance```, ```newInstance```,
```getType```, and ```newType```


## Chapter 10: Exceptions

### Item 69: Use exceptions only for exceptional conditions

Exceptions should never be used for ordinary control flow. This is also true for
a well-designed API, it must not force its clients to use exceptions for ordinary control flow.
For example, the Iterator interface has the state-dependent method next and
the corresponding state-testing method hasNext. It allows the client of the API to
check if next element is available and it does not force it to handle a potential exception.

### Item 70: Use checked exceptions for recoverable conditions and runtime exceptions for programming errors

Java provides three kinds of throwables: **checked exceptions**, **runtime exceptions**,
and **errors**

- Generally use **checked exceptions** for conditions from which the caller
can reasonably be expected to recover. By throwing a checked exception, you
force the caller to handle the exception in a catch clause or to propagate it outward.

There are two kinds of unchecked throwables: **runtime exceptions** and **errors**.
They are identical in their behavior: both are throwables that needn’t, and
generally shouldn’t, be caught.

- Use **runtime exceptions** to indicate programming errors. The great
majority of runtime exceptions indicate precondition violations (eg: ArrayIndexOutOfBounds) .

Sometimes it is difficult to know if it is a recoverable condition (so to use checked exceptions)
or the problem will persist (and use unchecked exceptions). If it isn’t clear whether recovery is possible, you’re
probably better off using an unchecked exception.

It a conventions that errors are reserved for use by the JVM to indicate resource
deficiencies, invariant failures, or other conditions that make it impossible to continue execution.
Use only subclasses of RuntimeException for unchecked throwables and do not use Error.

Do not forget that exceptions are classes and you shoul provide methods that help the caller
to recover (for checked exceptions)

### Item 71: Avoid unnecessary use of checked exceptions

Remember: A method that throws checked exceptions cannot be used in streams!

When used sparingly, checked exceptions can increase the
reliability of programs; when overused, they make APIs painful to use. If callers
won’t be able to recover from failures, throw unchecked exceptions. If recovery
may be possible and you want to force callers to handle exceptional conditions,
first consider returning an optional. Only if this would provide insufficient
information (in order to recover from the error) in the case of failure should you throw a checked exception.


### Item 72: Favor the use of standard exceptions

Reusing standard exceptions has several benefits. Chief among them is that it
makes your API easier to learn and use because it matches the established
conventions that programmers are already familiar with.

|Exception|Use|
|:---|:----|
|IllegalArgumentException|Non-null parameter value is inappropriate|
|IllegalStateException|Object state is inappropriate for method invocation|
|NullPointerException|Parameter value is null where prohibited|
|IndexOutOfBoundsException|Index parameter value is out of range|
|ConcurrentModificationException|Concurrent modification of an object has been detected where it is prohibited|
|UnsupportedOperationException|Object does not support method|

### Item 73: Throw exceptions appropriate to the abstraction

Higher layers should catch lower-level exceptions and, in their place,
throw exceptions that can be explained in terms of the higher-level abstraction.

Exception chaining is called in cases the lower-level exception might be helpful to someone debugging
the problem that caused the higher-level exception. The lower-level exception
(the cause) is passed to the higher-level exception, which provides an accessor
method (Throwable’s getCause method) to retrieve the lower-level exception. This
technique is better than bubbling the exception to higher level but it should not be
overused.

eg:

```
// Exception Chaining
try {
    ... // Use lower-level abstraction to do our bidding
} catch (LowerLevelException cause) {
    throw new HigherLevelException(cause);
}
```


### Item 74: Document all exceptions thrown by each method

Always declare checked exceptions individually, and document precisely
the conditions under which each one is thrown using the Javadoc @throws tag.

Also don’t take the shortcut of declaring that a method throws some superclass of
multiple exception classes that it can throw. As an extreme example, don’t
declare that a public method throws Exception or, worse, throws Throwable.

### Item 75: Include failure-capture information in detail messages

To capture a failure, the detail message of an exception should contain the
values of all parameters and fields that contributed to the exception.


### Item 76: Strive for failure atomicity

Generally speaking, a failed method invocation should leave the object in the state that it was in prior to the
invocation.

- The simplest way for this is to design immutable objects.
- Another way is to check the parameters and throw exceptions before accessing the rest of the method and
change the state of any object.
- A third approach to achieving failure atomicity is to perform the operation on
a temporary copy of the object and to replace the contents of the object with the
temporary copy once the operation is complete.
- A final way is to write recovery code that intercepts a failure that
 occurs in the midst of an operation, and causes the object to roll back its state

### Item 77: Don’t ignore exceptions

An empty catch block defeats the purpose of exceptions, which is to
force you to handle exceptional conditions. Ignoring an exception is analogous
to ignoring a fire alarm—and turning it off so no one else gets a chance to see if
there’s a real fire. And if you chose to ignore the exception at least
write a comment explaining why?

## Chapter 11: Concurrency

### Item 78: Synchronize access to shared mutable data


Synchronization is required for reliable communication between threads as well as for mutual exclusion.

A "synchronized" keyword does 2 thinks:

1) Prevents an object from being seen in an inconsistent state by one thread while it’s being modified by another.
2) It ensures that each thread entering a synchronized method or block sees the effects of all previous modifications
 that were guarded by the same lock.

eg:
```
public class StopThread {
    private static boolean stopRequested;

    public static void main(String[] args) throws InterruptedException {
        Thread backgroundThread = new Thread(() -> {
        int i = 0;
        while (!stopRequested)
            i++;
        });
        backgroundThread.start();
        TimeUnit.SECONDS.sleep(1);
        stopRequested = true;
    }
}
```

Because the access to ```stopRequested``` value is not synchronized the thread will run forever!

You need to control the access of ```stopRequested``` with synchronized in both read and write!
Synchronization is not guaranteed to work unless both read and write operations are synchronized


```
// Properly synchronized cooperative thread termination
public class StopThread {
    private static boolean stopRequested;

    private static synchronized void requestStop() {
        stopRequested = true;
    }

    private static synchronized boolean stopRequested() {
        return stopRequested;
    }

    public static void main(String[] args) throws InterruptedException {
    Thread backgroundThread = new Thread(() -> {
        int i = 0;
        while (!stopRequested())
            i++;
    });

    backgroundThread.start();
    TimeUnit.SECONDS.sleep(1);
    requestStop();
    }}
```

If a value is atomic like here you may use ```volatile``` to ensure that each thread reads the latest value of
```stopRequested```

```
    private static volatile boolean stopRequested;
```

But the best way for multithreaded environments is to avoid sharing mutable object and share only
immutable or effective immutable data (data that change only once and never again)

### Item 79: Avoid excessive synchronization

Inside a synchronized region, do not invoke a method that is designed to be overridden, or one
provided by a client in the form of a function object.

As a rule, you should do as little work as possible inside synchronized regions.

Also now that all servers/pcs are multicore it is a waste of time to synchronize code.

When you are writing a mutable class, you have two options:
1) you can omit all synchronization and allow the client to synchronize externally if concurrent use
is desired,
2) you can synchronize internally, making the class thread-safe

You should choose the latter option only if you can achieve significantly
higher concurrency with internal synchronization than you could by having the
client lock the entire object externally.


### Item 80: Prefer executors, tasks, and streams to threads

Prefer tasks (and task executors) instead of threads.

In Java 7, the Executor Framework was extended to support fork-join tasks, writing and tuning fork-join tasks is tricky.
Use Parallel streams are written atop fork join pools and allow you to take advantage of their performance benefits.

### Item 81: Prefer concurrency utilities to wait and notify

Given the difficulty of using wait and notify correctly, you should use the higher-level
concurrency utilities in java.util.concurrent (Executor Framework, concurrent collections, synchronizers).

**Concurrent Collections**

The concurrent collections are high-performance concurrent implementations
of standard collection interfaces such as List, Queue, and Map. To provide
high concurrency, these implementations manage their own synchronization
internally.

> Use ConcurrentHashMap in preference to Collections.synchronizedMap.


**Synchronizers**

Synchronizers are objects that enable threads to wait for one another, allowing
them to coordinate their activities. The most commonly used synchronizers are
CountDownLatch and Semaphore.

Countdown latches are single-use barriers that allow one or more threads to
wait for one or more other threads to do something. The sole constructor for
CountDownLatch takes an int that is the number of times the countDown
method must


### Item 82: Document thread safety

To enable safe concurrent use, a class must clearly document what level of thread safety it supports.

Every class should clearly document its thread safety properties
with a carefully worded prose description or a thread safety annotation (Immutable, ThreadSafe, and NotThreadSafe)

### Item 83: Use lazy initialization judiciously

Lazy initialization is a double-edged sword.
It decreases the cost of initializing a class or creating an instance, at the
expense of increasing the cost of accessing the lazily initialized field.
In the presence of multiple threads, lazy initialization is tricky and should be avoided.

If you need to use lazy initialization for performance on a static field, use
the lazy initialization holder class idiom

```
private static class FieldHolder {
    static final FieldType field = computeFieldValue();
}
private static FieldType getField() { return FieldHolder.field; }
```

If you need to use lazy initialization for performance on an instance field,
use the double-check idiom.

```
private volatile FieldType field;
private FieldType getField() {
    FieldType result = field;
    if (result == null) { // First check (no locking)
        synchronized(this) {
            if (field == null) // Second check (with locking)
                field = result = computeFieldValue();
            }
   }return result;
}
```

### Item 84: Don’t depend on the thread scheduler

Any program that relies on the thread scheduler for correctness or performance is likely to be
nonportable.

As a corollary, do not rely on Thread.yield or thread priorities. These facilities
are merely hints to the scheduler.

## Chapter 12. Serialization

### Item 85: Prefer alternatives to Java serialization

Fundamental problem with serialization is that its attack surface is too big to
protect, and constantly growing

There is no reason to use Java serialization in any new system you write.

A few other ways  for translating between objects and byte sequences that avoid
many of the dangers of Java serialization are:

- JSON
- Protocol Buffers (protobuf)

The most significant differences between JSON and protobuf are that JSON is
text-based and human-readable, whereas protobuf is binary and substantially
more efficient; and that JSON is exclusively a data representation, whereas
protobuf offers schemas (types) to document and enforce appropriate usage.
Although protobuf is more efficient than JSON, JSON is extremely efficient for
a text-based representation.

### Item 86: Implement Serializable with great caution

Disadvantages of Serializable:

1) It decreases the flexibility to change a class’s implementation once it has been released.
2) It increases the likelihood of bugs and security holes.
3) It increases the testing burden associated with releasing a new version of a class.
4) Classes that are design for inheritance should not implement Serializable.
5) You should not implement Serializable in a inner class.

### Item 87: Consider using a custom serialized form

If you have to use Serializable you must consider the create your own serialized form

The default serialized form is likely to be appropriate if an object’s
physical representation is identical to its logical content. But even then it is best to provide a
```readObject``` method to ensure invariants and security.

A class that is serializable makes the private field part of the exposed API,
use @serial tag tells Javadoc to place this documentation on a special page that
documents serialized forms.

Every instance field that can be declared transient should be otherwise it will be serialized when the
```defaultWriteObject``` method is invoked

Finally regardless of what serialized form you choose, declare an explicit serial
version UID in every serializable class you write.

```
private static final long serialVersionUID = randomLongValue;
```

It doesn’t matter what value you choose for
randomLongValue. You can generate the value by running the serialver
utility on the class, but it’s also fine to pick a number out of thin air. It is not
required that serial version UIDs be unique.

### Item 88: Write readObject methods defensively

readObject method is effectively another public
constructor, and it demands all of the same care as any other constructor (validity checks & defensive copying).

How to write a readObject method:

- For classes with object reference fields that must remain private, defensively
 copy each object in such a field. Mutable components of immutable classes
 fall into this category.
- Check any invariants and throw an InvalidObjectException if a
  check fails. The checks should follow any defensive copying.
- Do not invoke any overridable methods in the class, directly or indirectly.

### Item 89: For instance control, prefer enum types to readResolve

Use enum types to enforce instance control invariants wherever
possible.

```
public enum Elvis {
    INSTANCE;
    private String[] favoriteSongs = { "Hound Dog", "Heartbreak Hotel" };
    public void printFavorites() {
        System.out.println(Arrays.toString(favoriteSongs));
    }
}
```


### Item 90: Consider serialization proxies instead of  serialized instances

Consider the serialization proxy pattern whenever you find
yourself having to write a readObject or writeObject method on a class
that is not extendable by its clients.

