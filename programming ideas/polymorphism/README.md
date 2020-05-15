# Polymorphism

## What is polymorphism?
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
  private:
    int student_population;

  public:
      // overwriting default constructor, takes a population parameter
    Shape(int population) {
      student_population = population;
    }
      
    virtual void stats() {
      return student_population;
    }
}
```