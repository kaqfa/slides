# Getting Wet

### Array Manipulation in Java

Created By [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### The Very Begining

All Java Program need PSVM (public static void main) method.

So, let us create one.

```java
Class FirstClass{

	public static void main(String [] args){
		System.out.println("Hello of Everything");
	}
}
```

---

### First Other Class

- Create a Java class that do a basic math calculation, and has these methods:
  - int plus(int val1, int val2)
  - int minus(int val1, int val2)
  - double multiply(int val1,int val2)
  - double division(int val1, int val2)
  - double power(int val1, int val2)
- Test the class in Main class

---

### Dive into Array

- Create a Java class that do a basic manipulation to array
- The class consist of following attributes:
  - private int marks [];
  - private String names [];
- and also has following methods:
  - void arrayDeclaration(int arrSize)
  - void setMark(int index, int value)
  - void setName(int index, String value)
  - int getMark(int index)
  - int getName(int index)

--

### Constructor of Class

Create a Class Contructor to make sure that array class is properly declared before used.

--

### Check, Min, and Max 

Add following methods to the array Class:

- boolean markExist(int index) : check if the mark of that index is already inserted with some value or not.
- boolean nameExist(int index) : check if the name of that index is already inserted with some values or not.
- int findMaxMark() : find the highest value in array of marks
- int findMixMark() : find the lowest value in array of marks

--

### Validate Input dan Random Input

- Modify the setMark() method to make sure that it will only accept a value between 0 - 100
- Create a ```void fullfill()``` method that insert random integer (between 0 - 100) to all of marks slots
  - it detect the length of array first, and then insert the values by using loop
  - you can use Math.random() to generate random number
  - you can use varName.length() to get length of array
- Create a ```void printAllMarks()``` to print all of values in marks array

--

### Sort the Array

Create a method to sort array of marks using BubleSort Algorithm

---

# THE END

### By Fahri Firdausillah / fahrifirdaus.web.id