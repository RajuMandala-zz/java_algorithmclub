<h1>Search</h1>
We have two approaches
<ul>
  <li>Linear Search</li>
  <li>Binary Search</li>
</ul>

<h2> Linear Search </h2>
Linear search takes **O(n)** for searching an item in the given set of items, where n is the size of items.

A simple example of searching a number in the array of numbers,

```java
public boolean search(int key, int[] values) {
	for (int x: values) {
		if(key == x) {
			return true;
		}	
	}
	return false;
}
```

This is Simple. What if we want to search a name in the array of names of type String. Thanks to **Generics**, we don't have to write another function. We can change the above method to,
```java
public boolean search(T key, T[] values) {
	for (T x: values) {
		if(key == x) {
			return true;
		}		
	}
	return false;
}
```
So far, we are doing good with the primitive types. But what if we want to search whether student exists in the array of student objects? Does our generic methodstill hold good for this condition? let's test the application
```java
Student[] students = {new Student(1,"Raju"), new Student(2,"Rahul")};
LinearSearchApp<Student> obj = new LinearSearchApp<>();
System.out.println(obj.search(new Student(1,"Raju"), students));
```

Since we have the Student with "Raju", we expect the above program to print, true. But it prints **false**. Because if you check the **if** condition in the method, we are using == for comparision.

**==** returns true if and only if both variables refer to the same object. Here, I want to compare my objects based on the content of my Student object. How can i do that? by using **equals**. 
```java
public boolean search(T key, T[] values) {
	for (T x: values) {
		if(key.equals(x)) {
			return true;
		}	
	}
	return false;
}
```
Since we used **equals** now, it should print **true**. Run the program now. OMG it prints **false** again. Why? Default equals() method return true iff two objects are exactly same i.e. they are pointing to the same memory address. As we created a new object in our search method call(i.e. obj.search(**new Student(1,"Raju")**, students)), it will point to a different. So to overcome this situation, Make sure your **Student** object is overriding the equals method in Student class.
