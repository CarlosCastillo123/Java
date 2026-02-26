# Part 1
## 1)Where is x stored?
x is is stored in the stack because it is a primative data type
## 2)Where is s1 stored?
The refrence to the s1 object is stored in the stack and the data is stored in the heap.
## 3) Where is the Student object stored?
The Student object's reference is in the stack and the data is in the heap.
## 4) Why does x remain 10 after modify()?
x remains 10 because x is stored in the local scope ad the function happens outside the scope
## 2) Why does s1.age change?
The location of age is referenced and the function modifies the object directly

# Part 2
## 1) How many objects are created?
one object in the heap
## 2) How many references exist?
Two reference exists 
## 3) Why does modifying s2 affect s1?
The code references the same object

# Part 3
## 1) How many objects are created?
There are 2 objects in created
## 2) Which object becomes eligible for garbage collection?
s1 becomes eligible for garbage collection
## 3) At what line does that happen?
This happens right after s1 = s2
## 4) Does Java immediately delete it?
Not ecatly Java performs garbage collection whenever it tries to free up memory
# Part 4
Why are these objects NOT garbage collected?
These objects are not garbage collected becasue they do not 
What would you change to fix this?

Modify the code to prevent the leak.
