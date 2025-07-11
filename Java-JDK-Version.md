
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
                  
# 5. Method References

  Shorter syntax for lambda expressions that just call a method.
                  
                  List<String> list = Arrays.asList("a", "b", "c");
                  list.forEach(System.out::println);

# 6. Optional Class

A container object that may or may not contain a non-null value. Helps avoid NullPointerException.
                  
                  Optional<String> name = Optional.ofNullable("Java");
                  name.ifPresent(System.out::println);
                  
# 7. New Date and Time API (java.time)

                  LocalDate today = LocalDate.now();
                  LocalDate birthday = LocalDate.of(1990, Month.JULY, 20);
                  System.out.println("Today: " + today);
                  System.out.println("Birthday: " + birthday);

# 8. Collectors (with Streams)

Used to collect the result of stream operations into a collection or a summary.

                  
                  List<String> names = Arrays.asList("Anna", "Bob", "Alice");
                  String result = names.stream()
                      .collect(Collectors.joining(", "));
                  System.out.println(result);  // Output: Anna, Bob, Alice

# ✅ Java 9

 ✅ 1. Java Platform Module System (JPMS) – Project Jigsaw

   Introduced modularity to Java, allowing better organization, security, and maintainability.

    Example:
              
              module com.example.myapp {
                  requires java.base;
                  exports com.example.myapp.api;
              }


✅ 2. JShell (REPL)
A command-line tool to run Java code snippets without creating full classes — great for learning and prototyping.
    
    Usage:
    
                jshell
                jshell> int x = 5;
                jshell> System.out.println(x * 2);

 # ✅ Java 10

 ✅ 1. Local Variable Type Inference (var)
Introduced the var keyword to declare local variables without explicitly specifying the type — type is inferred by the compiler.
⚠️ var can only be used for local variables (not fields, method parameters, or return types).


  Example:
            
            var name = "Java 10";         // Inferred as String
            var list = List.of(1, 2, 3);  // Inferred as List<Integer>

✅ 2. Unmodifiable Collectors
Enhancement to Collectors.toUnmodifiableList(), toUnmodifiableSet(), and toUnmodifiableMap() to create immutable collections directly from streams.

    Example:
              
              List<String> list = List.of("a", "b", "c");
              List<String> unmodList = list.stream()
                  .collect(Collectors.toUnmodifiableList());


# ✅ Top Java 11 Features with Examples

         Java 11 introduced several new utility methods in the String class:

              public class StringExample {
                public static void main(String[] args) {
                    String s = "  Hello Java 11  ";
            
                    System.out.println(s.isBlank());       // false
                    System.out.println("  \n\t".isBlank()); // true
            
                    System.out.println(s.strip());         // "Hello Java 11" (removes leading/trailing whitespace)
                    System.out.println(s.repeat(2));       // Repeats the string twice
                    s.lines().forEach(System.out::println); // Splits string into lines
                }
            }

2. ✅ Local Variable Type Inference in Lambda Parameters
 
 You can now use var in lambda parameters.
          
           List<String> names = List.of("Alice", "Bob", "Charlie");
          
          names.forEach((var name) -> System.out.println(name.toUpperCase()));

 3. ✅ HTTP Client API (Standard)
          The new HTTP Client (previewed in Java 9) is now fully supported.

                  
                  import java.net.URI;
                  import java.net.http.HttpClient;
                  import java.net.http.HttpRequest;
                  import java.net.http.HttpResponse;
                  
                  public class HttpExample {
                      public static void main(String[] args) throws Exception {
                          HttpClient client = HttpClient.newHttpClient();
                          HttpRequest request = HttpRequest.newBuilder()
                                  .uri(URI.create("https://api.github.com"))
                                  .build();
                  
                          HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
                  
                          System.out.println(response.statusCode());
                          System.out.println(response.body());
                      }
                  }

4. ✅ File readString() and writeString() Methods

          Simplified reading and writing text files.
   
            import java.nio.file.Files;
            import java.nio.file.Path;
            
            public class FileExample {
                public static void main(String[] args) throws Exception {
                    Path path = Path.of("test.txt");
            
                    Files.writeString(path, "Hello Java 11");
                    String content = Files.readString(path);
                    System.out.println(content);
                }
            }

                

# ✅ Java 17 Features with Examples

1. ✅ Sealed Classes
   
Restrict which classes can extend or implement a class/interface.

Example:

    public abstract sealed class Shape permits Circle, Square {
      public abstract double area();
    }

final class Circle extends Shape {}
final class Square extends Shape {}
// class Triangle extends Shape {} ❌ Not allowed unless listed
🔹 Why use it? Enforces control over class hierarchies — useful in domain modeling.

2. ✅ Pattern Matching for instanceof
   
Simplifies type checks and casting in instanceof.

Before Java 17:
        
        if (obj instanceof String) {
            String s = (String) obj;
            System.out.println(s.toLowerCase());
        }

 With Java 17:
            
            
            if (obj instanceof String s) {
                System.out.println(s.toLowerCase());
            }


  3. ✅ Switch Expressions (Standardized)
      
Switch can now return a value and use the -> syntax and yield.

Example:
            String num = "two";
              String result = switch (num) {
                  case "one" -> "one";
                  case "two" -> "two";
                  case "three" -> "three";
                  default -> "unknown";
              };
      
              System.out.println("Result: " + result); 

                
                public class PatternMatchSwitchExample {
                    public static void main(String[] args) {
                        Object input = 42;
                
                        String result = switch (input) {
                            case Integer i -> "It's an Integer: " + (i * 2);
                            case String s  -> "It's a String: " + s.toUpperCase();
                            case null      -> "Input is null";
                            default        -> "Unknown type";
                        };
                
                        System.out.println(result);
                    }
                }
 # Why use Pattern Matching for switch?
           More readable & concise
           No more manual casting
           Safe (Prevents classCostException)
           Easier to extend in the future
 

  4. ✅ Text Blocks Example with JSON


public class JsonTextBlockExample {
    public static void main(String[] args) {
                  String json = """
                      {
                          "name": "Alice",
                          "age": 30,
                          "role": "Developer",
                          "active": true
                      }
                      """;
          
                  System.out.println(json);
              }
          }


5. ✅ Record Classes (finalized in Java 16, widely used in 17)

   
Simplifies data carrier classes (like DTOs).

Example:

          
          public record Person(String name, int age) {}
          
          Person p = new Person("Alice", 30);
          System.out.println(p.name()); // "Alice"
          
6. ✅ JEP 356: Enhanced Pseudo-Random Number Generators
   
Improved and pluggable random number generators.

Example:
            
            RandomGenerator generator = RandomGeneratorFactory.of("L64X128MixRandom").create();
            System.out.println(generator.nextInt());
