---
published: true
---
Arduino doesn't have dynamic cast because Real Time Type Info (RTTI) is disabled by the compiler to save memory.

You can theoretically reenable it if you mess with the compiler settings, but this isn't an option if you are writing code that needs to be easily buildable by people who don't want to touch their arduino compiler settings.

Another way is to write your own dynamic casting functionality using prime number factorization to track polymorphism inheritance. Enter DIY Dynamic Cast.

Note: this should not be used, it's just a fun trick. If you think you need dynamic cast, there's usual a design pattern that will let you avoid it and make your code cleaner in the process.

### Idea

The basic idea is that for each class that needs dynamic casting, we will assign it an integer id. This id will be the product of its parent's id and the next prime number.

For example, say we had a Dog class and a subclass of Dog called Lab. Our Dog class would get the first prime number assigned to it as an id (multiplied by 1 because Dog has no parents). Lab would have an id of 3\*2 = 6 (the next prime is 3).

``` c++
class Dog {
		static int id = 2
	}
    
    class Lab {
 		static int id = 2 * nextPrime() // nextPrime() -> 3
	}
    
```


If we need to check if an instance of Dog is actually an upcasted instance of Lab, we can just check if the id of the dog instance is divisible by the id of the Lab class.

``` c++
if (dog.id % Lab::id == 0) {
       return true;
}
return false;
```

We could also check upcasts the same way. Because each class has a unique prime multiplied into it's id tree the id of the object instance O is **only** divisible by the id of a class C if O is an instance of C or inherits from C.

### Implementation
    
This isn't useful unless we can find a way to automatically assign ids to the classes that need them.

We need a function to get the next prime number that has never been used: getNextPrime().

Then we need a function that calculates the type_id from the parent id and the prime.

getChildTypeId(int parentId)

Finally, we need a DynamicClass parent class that will define the implementation of a `static const int id` for the class.

``` c++
class DynamicClass {
	static const int id = 1;
}
```

And then for convenience, some macros that does the neccessary work to generate a dynamic child class.

``` c++

#define DYNAMIC_CLASS public DynamicClass {  \
public: \
    static const int id; \
private:

#define END_DYNAMIC_CLASS(classname, parent)\
};\
\
const int classname::id(getChildTypeId(parent::id));

```

The first macro helps ensure that our type has an id and the second calculates the id. This calculation needs to be done outside of the class.

Now we can create a dynamic cast template function to cast something if it is in the inheritance tree and return a nullptr or error otherwise.

``` c++ 

template <class T, class V>
T* Dynamic_Cast(V* obj) {
    // check if the object is in the inheritance prime tree
    if (obj -> id % T::id == 0) {
        //cast object
        return (T*)obj;
    }
    //otherwise return a null pointer
    return nullptr;
}

```

Trying it out:

``` c++

class myDynamicClass : DYNAMIC_CLASS
	int myInt;
    int mySecondInt;
    void myFunc(int arg1, int arg2){ 
        Serial.println(arg1);
        Serial.println(arg2); 
    };

    template <typename T, typename V>
    void Foo(T i, V b) {};
END_DYNAMIC_CLASS(myDynamicClass, DynamicClass)

  
   
class myChildDynamicClass : public myDynamicClass, DYNAMIC_CLASS
public:
	int myThirdInt;
END_DYNAMIC_CLASS(myChildDynamicClass, myDynamicClass)

int main() {
	myDynamicClass* hiddenChild = new myChildDynamicClass()
      
    myDynamicClass* parent = new myDynamicClass()
      
    myDynamicChildClass* child = Dynamic_Cast<myDynamicChildClass>(hiddenChild);
  	myDynamicChildClass* badCast = Dynamic_Cast<myDynamicChildClass>(parent);
  
  	if (badCast != nullptr) {
      return 0;
    }
  
  	if (child != nullptr) {
      return 2;
    }
  	
  	return 1;
}
```

This will successfully cast only in the second case, since `badCast.id = 3` is not divisible by 		`myChildDynamicClass::id = 15`.