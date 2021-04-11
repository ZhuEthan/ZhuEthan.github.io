Java functional programming: 
-   Functions as first class objects
-   Pure functions
-   Higher order functions

Pure functional programming has a set of rules to follow too:

-   No state
-   No side effects
-   Immutable variables
-   Favour recursion over looping


### Lambda
* A Java lambda can capture the value of a local variable declared outside the lambda body. 
* A lambda expression can also capture an instance variable in the object that creates the lambda. 

**Method References as Lambdas:**
In the case where all your lambda expression does is to call another method with the parameters passed to the lambda, the Java lambda implementation provides a shorter way to express the method call. e.g. Finder finder = MyClass::doFind;
* Static Method References
* Parameter Method Reference (reference a method of one of the parameters to the lambda.)
* Instance Method References (creating instance)
* Constructor References (without creating instance)

### [Java Stream API](http://tutorials.jenkov.com/java-functional-programming/streams.html)

**Non-Terminal Operations:** A _non-terminal stream operation_ is an operation that adds a listener to the stream without doing anything else
* map(Function<? super T, ? extends R>)
* filter(Predicate<? super T>):
* flatMap(Function<? super T, ? extends Stream<? extends R>> mapper): 
* distinct(): return a stream
* limit(): return a stream
* peek(Consumer<? super T> action)
* 

**Terminal operations:** A  _terminal stream operation_  is an operation that starts the internal iteration of the elements, calls all the listeners, and returns a result.
* count()
* reduce()
	* To put it simply, if we use sequential streams and the types of the accumulator arguments match the types of the identifier (initial value type), we don't need to use a combiner.
	* Why? 
		* https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html#reduce-T-java.util.function.BinaryOperator-
		* https://www.baeldung.com/java-stream-reduce
	* Reducing in parallel requires aggregate operations executed on the streams are: 
		* associative: the result is not affected by the order of operands. 
		* non-interfering: the operation doesn't affect the data source. 
		* stateless and deterministic: the operation doesn't have state and produces the same output for a given inupt. 
* collect(java.util.stream.Collector/Collectors): and collects the elements in the stream in a collection or object of some kind. 
* anyMatch(Predicate<? super T>), if the predicate retuns true for any of the elements, the anyMatch() method returns true. If no elements match the Predicate, anyMatch() will return false. here is a Java Stream anyMatch() example: 
* allMatch(Predicate<? super T>): If the `Predicate` returns `true` for all elements in the `Stream`, the `allMatch()` will return `true`. If not all elements match the `Predicate`, the `allMatch()` method returns `false`
* noneMatch(Predicate<? super T>): The `noneMatch()` method will return `true` if no elements are matched by the `Predicate`, and `false` if one or more elements are matched
* Count()
* findAny(): `findAny()` method returns an `Optional`. The `Stream` could be empty
* findFirst(): 
* forEach(Consumer<? super T> action)
* Option< T> min(Comparator<? super T> comparator): 
* max
* Object[] toArray(): returns an array of Object containing all the elements. 

Stream.concat(Steam<? extends T>, Stream<? extends T>)

Stream.of(T... objects): 
