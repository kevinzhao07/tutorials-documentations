# Polymorphism

## What is Polymorphism?
As a student studying computer science, I've always heard the term "polymorphism" thrown around and hailed for its importance in object oriented programming. However, I never really 100% understood what it was.   

**Polymorphism** comes from two roots in Greek:
- *poly-* meaning many (ex. *poly*gon: many sided, *poly*gamy: many lovers)
- *morph-* meaning changing (ex. meta*morph*osis: to change shape)

To put it simply, polymorphism is **the ability for an object to take on many different forms**. In programming, we see many child objects belonging to a centralized parent object that may have functions with the same name, but different behaviors. 

## Example of Polymorphism
Straying away from the "classic" example of shapes, we can observe an `University` parent class and all the classes that inerhit from it:
- *University of Michigan*
- *Harvard University*
- *Cornell University*
> each are examples of an `University` object, but they take on many different forms and even have different function executions. 

With polymorphism, even though all are `University` objects, they are allowed to have different underlying data. That only makes sense-- `Harvard University` will not rely on `University of Michigan` for student population data and vice versa. This is why polymorphism is useful; it relates common objects of similar classes together, while allowing them to keep their data separate. 

## Example in Code (C++)
```cpp
class University {
  public:
    University() {}
      
    // virtual keyword is there to allow overwriting by derived classes
    virtual void chant() {
      return "We are a great college!" << endl;
    }
}; // don't forget this semicolon
```

Above is an example of a simple class. We have ideas of making this our parent `University` class and will have other classes `extend` this one. Following an example using polymorphism, we can derive hypothetical classes:

```cpp
// the ":" that the UniversityOfMichigan class is derived from the parent class University
class UniversityOfMichigan: public University {
  public:
    UniversityOfMichigan() {}

    // notice now the function header is the same!
    virtual void chant() {
      return "Forever Go Blue!" << endl;
    }
}

// the ":" shows that the HarvardUniversity class is derived from the parent class University
class HarvardUniversity: public University {
  public:
    HarvardUniversity() {}

    // notice now the function header is the same!
    virtual void chant() {
      return "Michigan of the East!" << endl;
    }
}

// the ":" shows that the CornellUniversity class is derived from the parent class University
class CornellUniversity: public University {
  public:
    CornellUniversity() {}

    // notice now the function header is the same!
    virtual void chant() {
      return "We're the best Ivy!" << endl;
    }
}
```
After seeing these three derived classes, a valid concern is to say, what is the point of polymorphism? We are still creating 3 separate classes and implementing different `chant()` functions for each. 

## Advantages 
Here we have our main functions, and output when we run the function:
```cpp
int main() {

  // our base class object declaration
  University *uni;

  // three derived class declarations
  UniversityOfMichigan mich;
  HarvardUniversity harvard;
  CornellUniversity cornell;

  // we are allowed to assign derived classes TO base classes 
  uni = &mich;
  uni->chant();

  uni = &harvard;
  uni->chant();

  uni = &cornell;
  uni->chant();

  return 0;
}

OUTPUT:
"Forever Go Blue!" // this is from UniversityOfMichigan
"Michigan of the East!" // this is from HarvardUniversity
"We're the best Ivy!" // this is from CornellUniversity 
```

> `uni = &mich;` is allowed in polymorphism because this exhibits **upcasting**. More importantly, `UniversityOfMichigan` is-a `University`.

In this example, we have an object `uni`, which is of the `University` class (the base class). We also defined 3 more other objects, one from each derived class. Because of the downcasting mentioned before, we are allowed to assign a `derived` class **to** a `base` class. When we call `uni`'s `chant()`, we get the `chant()` functions defined by each individual `derived` class. Essentially, this assignment overwrites our base's virtual `chant()` function, and we can use the `derived` classes' uniquely defined `chant()`.  

The importance comes from the fact that each of these functions are still *named* the same `chant()`. Though we have completely different classes, we need not specify function names as `MichiganChant()`, `HarvardChant()`, etc. The advantages of this comes from working with these derived classes and only having to keep track of function and value names inside the base class. When we are given the object `uni` in our case, we do not know if it is of the `base` class `University` or if it is any of the `dervied` classes. But, because we are using polymorphism, we do not care. We expect `chant()` to always give the correct answer. For this small example, it may seem unneccessary, but in more complex applications polymorphism is a necessity. 

> we use polymorphism every day without realizing. when we type `3 + 4.0`, we're assuming the `+` operator can adjust itself with different data types of `integer` and `float`. 