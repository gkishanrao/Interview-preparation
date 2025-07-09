
# ✅  Java 5.0

✅ Enhanced For Loop-Iteration over collection and arrays.

                  int[] numbers = {1, 2, 3, 4};
                  for (int n : numbers) {
                      System.out.println(n);
                  }

      
✅  Generics- Enabled type safety in collection and methods 
Allows you to define classes, interfaces, and methods with type parameters—enabling type safety and avoiding casting.
                  
                  List<String> list = new ArrayList<>();
                  list.add("Hello");
                  // list.add(123); // Compile-time error
                  String value = list.get(0); // No casting needed

            
 ✅  Enums- Provides a type-safe way to fefine contancts

                 enum Season{
                 WINTER,SPRING,SUMMER,FALL

 ✅  Autoboxing- Automatically converts primitives to wrapper classes

                  int i = 5;
                  Integer obj = i;         // autoboxing
                  int j = obj;             // unboxing

# ✅  Java 7
# Try-With-Resources: 
Automates resource manageement in try-catch block

                  try(BufferedReader br=
                  
                  new BufferedReader(new FileReader("File.txt"))){

   # String in Switch:
   Allows using String values in switch statements.
                  
                  switch (role) {
                              case "admin":
                                  System.out.println("Access granted to admin panel.");
                                  break;
                              case "user":
                                  System.out.println("Access granted to user dashboard.");
                                  break;
                              case "guest":
                                  System.out.println("Limited access.");
                                  break;
                              default:
                                  System.out.println("Unknown role.");
        }
# ✅ Java 8

       #  1. Lambda Expressions
       
      Enables functional-style programming.

     Makes code more concise, especially for functional interface

                       List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
                        names.forEach(name -> System.out.println(name));

                        
     # 2. Functional Interfaces

     
        An interface with exactly one abstract method.

        Examples: Runnable, Comparator, Predicate.
        
                          @FunctionalInterface
                           interface Greeting {
                               void sayHello(String name);
                           }
                           
                           Greeting greet = name -> System.out.println("Hello, " + name);
                           greet.sayHello("John");


    # 3. Streams API

    
    Allows processing collections in a functional, declarative way.
    
         List<String> names = Arrays.asList("Tom", "Jerry", "Tim");
                     names.stream()
                       .filter(n -> n.startsWith("T"))
                       .map(String::toUpperCase)
                       .forEach(System.out::println);

# 4. Default and Static Methods in Interfaces

You can now define concrete methods in interfaces.

                  interface Vehicle {
                      default void start() {
                          System.out.println("Vehicle is starting");
                      }
                  
                      static void stop() {
                          System.out.println("Vehicle stopped");
                      }
                  }
                  
#5. Method References

Shorter syntax for lambda expressions that just call a method.
                  
                  List<String> list = Arrays.asList("a", "b", "c");
                  list.forEach(System.out::println);

# 6. Optional Class

A container object that may or may not contain a non-null value. Helps avoid NullPointerException.
                  
                  Optional<String> name = Optional.ofNullable("Java");
                  name.ifPresent(System.out::println);
                  
#7. New Date and Time API (java.time)

                  LocalDate today = LocalDate.now();
                  LocalDate birthday = LocalDate.of(1990, Month.JULY, 20);
                  System.out.println("Today: " + today);
                  System.out.println("Birthday: " + birthday);

#8. Collectors (with Streams)

Used to collect the result of stream operations into a collection or a summary.

                  
                  List<String> names = Arrays.asList("Anna", "Bob", "Alice");
                  String result = names.stream()
                      .collect(Collectors.joining(", "));
                  System.out.println(result);  // Output: Anna, Bob, Alice
