The Static Keyword

The 'static' keyword can be used as a variable, a method, a block, or a nested class.

1) Static variable
o	Belongs to the class and not to an object
o	Can be invoked without creating an instance of a class: <class-name>.<variable-name>
o	Can be shared by all instances of the class ('Global' variable)

2) Static method
o	Belongs to the class
o	Can be invoked without creating an instance of a class
o	Can only directly access static data
o	Cannot use this and super
o	Cannot be overridden (static methods would be resolved at compile time)
o	For factory methods: static Circle createCircle(...)
o	For methods that access/mutate static fields

static int a = 10; 
int b = 20; 
static void m1() { 
   a = 20;
   b = 10; // compilation error 
   m2();  // compilation error
   System.out.println(super.a); // compiler error  
}
void m2() { }

3) Static block
o	Initialize static fields that can’t be done via =
o	Executed before the main method

class MyIntegers {
static List<Integer> integers = new ArrayList<>();
integers.add(1) // compilation error
static { // successfully compiled
integers.add(1);
}
}

4) Static nested classes
o	Only inner classes can be static; top-level classes cannot be made static
o	Can be instantiated without instantiating its outer class
o	Can only access static data of the outer class

class OuterClass {
   static String msg = “GeeksForGeeks”;
   
   static class NestedStaticClass {
      void printMessage() { System.out.println(msg); }
      // If msg is non-static, compiler error will result
   }

   class InnerClass {
      void display() { System.out.println(msg); }
   }

   public static void main(String args[]) {
      OuterClass.NestedStaticClass printer =
         new OuterClass.NestedStaticClass();
      OuterClass outer = new OuterClass();
      OuterClass.InnerClass inner = outer.new InnerClass();
   }
}
