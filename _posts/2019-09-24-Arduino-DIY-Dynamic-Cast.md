---
published: false
---
Arduino doesn't have dynamic cast because Real Time Type Info (RTTI) is disabled by the compiler to save memory.

You can theoretically reenable it if you mess with the compiler settings, but this isn't an option if you are writing code that needs to be easily buildable by people who don't want to touch their arduino compiler settings.

Another way is to write your own dynamic casting functionality using prime number factorization to track polymorphism inheritance. Enter DIY Dynamic Cast.

Note: this should not be used, it's just a fun trick. If you think you need dynamic cast, there's usual a design pattern that will let you avoid it and make your code cleaner in the process.

### Idea

The basic idea is that for each class that needs dynamic casting, we will assign it an integer id. This id will be the product of its parent's id and the next prime number.

For example, say we had a Dog class and a subclass of Dog called Lab. Our Dog class would get the first prime number assigned to it as an id (multiplied by 1 because Dog has no parents). Lab would have an id of 3\*2 = 6 (the next prime is 3).

``` 
class Dog {
		static int id = 2
	}
    
    class Lab {
 		static int id = 2 * nextPrime() // nextPrime() -> 3
	}
    
```


If we need to check if an instance of Dog is actually an upcasted instance of Lab, we can just check if the id of the dog instance is divisible by the id of the Lab class.

``` 
if (dog.id % Lab.id == 0) {
       
}
```

We could also check upcasts the same way. Because each class has a unique prime multiplied into it's id tree the id of the object instance O is **only** divisible by the id of a class C if O is an instance of C or inherits from C.

### Implementation
    
This isn't useful unless we can find a way to automatically assign id's to the classes that need them.

We need a function to get the next prime number that has never been used: getNextPrime().

Then we need a function that calculates the type_id from the parent id and the prime.

getChildTypeId(int parentId)

Finally, we need a DynamicClass parent class that will define the implementation of a <code>static const int id</code> for the class.
