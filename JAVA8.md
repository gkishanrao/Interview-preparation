
# JAVA 8 Feature

# ✅ 1. Lambda expressions

          Java
          // Traditional way to sort a list
          Collections.sort(names, new Comparator<String>() {
              @Override
              public int compare(String s1, String s2) {
                  return s1.compareTo(s2);
              }
          });
          
          // Using a lambda expression
          Collections.sort(names, (s1, s2) -> s1.compareTo(s2));



# ✅ 2. Functional interfaces

                    Interfaces with a Single Abstract Method (SAM): Functional interfaces are key for lambda expressions and are interfaces that contain only one abstract method. 
                    They can have any number of default or static methods

       ✅ A functional interface is an interface that contains exactly one abstract method, but it can also have multiple default and static methods.                    
                              
                              @FunctionalInterface
                              interface ZeroParameter {
                                  void display();
                              }
                              
                              public class Geeks {
                                  public static void main(String[] args)
                                  {
                                      // Lambda expression with zero parameters
                                      ZeroParameter zeroParamLambda = ()
                                          -> System.out.println(
                                              "This is a zero-parameter lambda expression!");
                              
                                      // Invoke the method
                                      zeroParamLambda.display();
                                  }
                              }


             Using Predicate 
             
                 List<Integer> list= Arrays.asList(1,2,3,4,5);
                 list.stream().filter(t->t%2==0).forEach(t->System.out.println("print Even:"+t));
                                      (predicate)

# ✅ 3. Functional interfaces

 # Why we need stream?
        Functioninal programming
        Reduce boilar plate code
        Bulk Operation

        
        
                                      
                              
