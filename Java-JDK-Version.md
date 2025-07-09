
✅ # Java 5.0

✅ Enhanced For Loop-Iteration over collection and arrays.

         for (String list:arrList){
            //do something
         }
      
✅  Generics- Enabled type safety in collection and methods 

            Public class HashMap<K,V> extends  AbstractMap<K,V>

            
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
