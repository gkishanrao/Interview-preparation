# Decorate and butlder design patterns
To dynamically add behavior or responsibilities to an object without modifying its structure or class.

            // Component interface
            interface Coffee {
                String getDescription();
                double cost();
            }
            
            // Concrete component
            class SimpleCoffee implements Coffee {
                public String getDescription() { return "Simple Coffee"; }
                public double cost() { return 2.0; }
            }
            
            // Abstract decorator
            abstract class CoffeeDecorator implements Coffee {
                protected Coffee decoratedCoffee;
                public CoffeeDecorator(Coffee coffee) { this.decoratedCoffee = coffee; }
            }
            
            // Concrete decorators
            class MilkDecorator extends CoffeeDecorator {
                public MilkDecorator(Coffee coffee) { super(coffee); }
                public String getDescription() { return decoratedCoffee.getDescription() + ", Milk"; }
                public double cost() { return decoratedCoffee.cost() + 0.5; }
            }
            
            class SugarDecorator extends CoffeeDecorator {
                public SugarDecorator(Coffee coffee) { super(coffee); }
                public String getDescription() { return decoratedCoffee.getDescription() + ", Sugar"; }
                public double cost() { return decoratedCoffee.cost() + 0.2; }
            }
            
              public class CoffeeShop {
                  public static void main(String[] args) {
                      Coffee coffee = new SimpleCoffee();
                      coffee = new MilkDecorator(coffee);  // Add milk
                      coffee = new SugarDecorator(coffee); // Add sugar
              
                      System.out.println(coffee.getDescription()); // Simple Coffee, Milk, Sugar
                      System.out.println(coffee.cost());           // 2.7
                  }
              }


# 🏗️ Builder Design Pattern
✅ Purpose:

To construct complex objects step by step, especially when objects have many optional parameters.
                  
                  class House {
                      private final int rooms;
                      private final boolean hasGarage;
                      private final boolean hasSwimmingPool;
                  
                      // Private constructor
                      private House(Builder builder) {
                          this.rooms = builder.rooms;
                          this.hasGarage = builder.hasGarage;
                          this.hasSwimmingPool = builder.hasSwimmingPool;
                      }
                  
                      public static class Builder {
                          private int rooms = 1;
                          private boolean hasGarage = false;
                          private boolean hasSwimmingPool = false;
                  
                          public Builder rooms(int rooms) {
                              this.rooms = rooms;
                              return this;
                          }
                  
                          public Builder garage() {
                              this.hasGarage = true;
                              return this;
                          }
                  
                          public Builder pool() {
                              this.hasSwimmingPool = true;
                              return this;
                          }
                  
                          public House build() {
                              return new House(this);
                          }
                      }
                  
                      @Override
                      public String toString() {
                          return rooms + " room(s), Garage: " + hasGarage + ", Pool: " + hasSwimmingPool;
                      }
                  }

          # 🧪 Usage:


                public class BuilderTest {
                    public static void main(String[] args) {
                        House customHouse = new House.Builder()
                                .rooms(4)
                                .garage()
                                .pool()
                                .build();
                
                        System.out.println(customHouse);
                        // Output: 4 room(s), Garage: true, Pool: true
                    }
                }
