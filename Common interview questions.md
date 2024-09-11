- What is `Method Overloading` vs `Method Overriding`?
	- Overloading allow two classes to have the same name, as long as they have different parameters, be it in type or number.
	- Overriding relies on inheritance, the class that extends a superclass can overload the default signatures of its methods.

- What are the differences between `Heap` and `Stack` memory?
	- Stack memory is a fixed memory space allocated to each individual program.
	- The Heap space is allocated dynamically in the application, it can expand or shrink depending the processes being run.

- Explain the expected output of the following segments:
	`System.out.println(100 + 100 + "Keep on coding");
	`System.out.println("Keep on coding" + 100 + 100);
	- When there are integer and strings being concatenated Java casts it all to a string so:
		- "200Keep on coding" as a string
		- "Keep on coding100100" as a string

- What are shallow copy and deep copy?
	- Shallow copy -> creating a new instance of the object by using clone() or copying the values of the object directly from the original. In this way changes on the ''copy'' reflect on the original since its pointer still points to the original .
	- Deep copy -> creates a new instance of the object by coping not only the fields but the objects referenced by the fields too, recursively. This can be achieved by overriding the clone() method to clone the original using its constructor for example.

- What is the `Garbage Collector` and how does it work?
	- The garbage collector function is to free up memory that is being allocated to a resource that it is not being used anymore. It keeps track of pointers to see if any of them are out of scope and de-alocates it. Nowadays the GC is multithread, meaning it doesn't pause the application when cleaning up resources, it stops each thread separately. It also doesn't affect the execution of the program.

- What are the differences between constructor and method of a class in Java?
	- A constructor is, like the name says, a method for constructing an object it is called implicitly. Methods are explicitly called do to something. Also a constructor is a method but not every method is a constructor.

- Explain the `this` keyword in Java?
	- This refers to scope of the current object, for example when you have a constructor that accepts parameters to define a property of the object, this is used to declare a property of the object.

- What is an abstract class?
	- An abstract class cannot be instantiated, it is used as an abstraction for other classes to extend. Eg: I have the Enemy class, the class Ghost extends Enemy but there is no need for me to have a concrete instance of Enemy since I'm using it more as a concept, so I make the Enemy class abstract. 

- Explain the `super` keyword in Java
	- Super refers to 'super class', when we want to refer to something in the super class from the child class we use 'super'

- Why are generic used in Java?
	- A generic is used when we want something to receive a myriad of different types. Eg: `ArrayList<E>()` says that it is an array list that can be of any type. We can also limit generics by using the `implements`  or `extends` keywords. Eg: `List<E extends MyObject>()` give us a list that can be of any type that extends MyObject.
	
- How is the final keyword applied differently between variables, methods and classes?
	- variables -> adding final means that the value will never change;
	- methods -> adding final means that the method cannot be overwritten;
	- classes -> adding final means that the class cannot be inherited or have sub classes;

- What is `protected?
	- It allows methods, variables or classes to be accessed from within the same package but not from outside of it. Eg: Class A and B are in the same package and class C is in another, class A is protected, so this means that class B can access it but C cannot.

- What is the difference between `equals()` and `==` in Java?
	- `equals()` is a method while `==` is a comparison operator. `==` checks if both sides point to the same memory location while `equals()` evaluates the content of each side.

- Is Java "pass by reference" or "pass by value"?
	- Java is "pass by value". This means that when you pass an argument to a method, you are passing a **copy** of the value, not the actual object or primitive. However, how this works depends on whether you are dealing with **primitives** or **objects**.
	- primitives -> Java makes a copy of the value and passes it to the method. The original value remains the same.
	- objects -> Java passes a copy of the reference of the object, not the actual object. This means that inside the method you are still working with the same object in memory. Modifying the object in this way affects the original object. But you cannot reassign the reference because it is just a copy

- What is a `Singleton` class and how do you ensure a class is a `Singleton?
	- A `singleton` its a class where only one instance of that class can exist. This is made by ensuring that the constructor is private and creating a method that returns the instance of the class;
```
	public class Singleton {
		private static Singleton singleton = new Singleton();
		
		private Singleton() {}

		public static Singleton getInstance(){
			returns singleton;
		}
	}
	
	///usage
	///both instances refer to the same singleton
	
	Singleton singleton1 = Singleton.getInstance();
	Singleton singleton2 = Singleton.getInstance();
```

- What is`Composition`? 
	- A composition is the use of an object inside another object, or a property of an object being used inside another object.

- Explain static block
	- It gets executed before at the time of class loading.  Meaning it runs before the main method.
	```
	static {
		System.out.println("Hello world")
	}
	```
	- This run on the Main class would be processed before the main() method for example.

- Why is the `remove()` method faster in the linked list than in an array?
	- In an array when you remove an item you need to shift the position of all the remaining ones. On a linked list you have nodes pointing to a reference of the next element, removing a reference just makes the affected pointer change instead of the whole list.
	
- How does the size of `ArrayList` grow dynamically? And also state how it is implemented internally
	- When the initial array reach its limit it copies itself and doubles its size. 

- What is a `Comparator` and `Comparable`?
	- Both specify how to sort collections of data.
	-  Comparable ->  its an interface that has the `compareTo(Object 0)` method which can be use to specify what to compare to.
	- Comparator ->  its a class that uses a generic to implement the object into its `compare(Object a, Object b)` method.