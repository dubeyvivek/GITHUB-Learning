1. Will this code compile successfully?
class Test <T> {
Test(T my) {
    boolean b = (my instanceof T);
}
}
Since the JVM has no information of the Parameterized type on runtime, there's no way you can do an instanceof

2. Collections.checkedCollection()
The generics mechanism in the language provides compile-time (static) type checking, but it is possible to defeat this mechanism with unchecked casts. Usually this is not a problem, as the compiler issues warnings on all such unchecked operations. There are, however, times when static type checking alone is not sufficient. For example, suppose a collection is passed to a third-party library and it is imperative that the library code 
not corrupt the collection by inserting an element of the wrong type.

Syntax:  public static  Collection  checkedCollection(Collection c, Class type)

 List<String> names = new ArrayList<>();
    Collections.addAll(names, "John", "Anton", "Heinz");
    List huh = names;
    List<Integer> numbers = huh;
    numbers.add(42);
    
    this will cause class cast exception . to give run time safety below code 
     List<String> names = Collections.checkedList(
        new ArrayList<>(), String.class);
    Collections.addAll(names, "John", "Anton", "Heinz");
    List huh = names;
    List<Integer> numbers = huh;
    numbers.add(42);

3.Will this code compile successfully?
class Test <T> {
private T[] array = null;
}
4  class Test <T> {
private T[] array = new T[7];
}
