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

**==** returns true if and only if both variables refer to the same object. I want to compare my objects based on the content of my Student. How can i do that? **equals** comes to the rescue.
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
