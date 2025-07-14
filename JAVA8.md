
# JAVA 8 Feature

✅ 1. Lambda expressions

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
