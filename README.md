SOLID principle are:
* Single Responsibilty principle:
  The Single Responsibility Principle requires that a class should have only one job. So if a class has more than one responsibility, it becomes coupled. A change to one responsibility results to modification of the other responsibility.

  ```python
     class Area:
    def __init__(self,length,breadth,radius):
        self.length=length
        self.breadth=breadth
        self.radius=radius

    def Circle(self):
        print("Area of circle:",2*3.14*self.radius)   

    def Rectangle(self):
        print("Area of Rectangle:",self.length*self.length)   

a=Area(6,5)
a.Circle         ```
 
  Here Class Area is responsible for both calculating area of both circle and Rectangle.But it isnot Good practise according to Single  Responsibility principle because each class should have unique responsibility.


```python
  class Circle:
    def __init__(self,radius):
      self.radius=radius

   def area(self):
     print("Area of circle:",2*3.14*self.radius)

  c=Circle(6)  
  c.area()
   

  class Rectangle(self,length,breadth):
    def __init__(self,length,breadth):
      self.length=length
      self.breadth=breadth

    def show(self):
      print("Area of Rectangle:",self.length*self.breadth)
  R=Rectangle(6,5)
  R.show()   
  ```

  Here two class are created for each unique responsiblity that are for creating area of circle and rectangle.


* The Open-Closed Principle (OCP):
open-closed principle states that software entities should be ready for extension and closed for modification.For example:
```Python
  class security:
    def check(self,person):
      if person==child:
        print("man")
      if  person == adult:
        print("adult") 
    return person    

    def register(self,image):
      if person==child:
        print("register child")
      if person==adult:
        print("register adult")  
   
      

```
But we want add if person==old circle 
```Python
class security:
    def check(self,person):
      if person==child:
        print("man")
      if  person == adult:
        print("adult") 

      if person== old:
        print("old")  
    return person    

    def register(self,image):
      if person==child:
        print("register child")
      if person==adult:
        print("register adult")  
  
   
      

```


then that is bad practise  according open and closed principle because class are closed for modification. In software there are line and line code if change in code can lead to the carsh of software to avoid this open and closed principle comes.improvisation above code according open-closed principle:

```python
   from abc import ABC,abstractmethod

  class check(ABC):
    @abstarctmethod
    def check_person(self,person):
      pass  

  class register(ABC):
    @abstarctmethod
    def register_person(self,face):
      pass   


  class child(Check,register):
    def check_person(self,person):
      print("Child")

    def register_person(self,face):
        print("child register") 

  class adult(Check,register):
    def check_person(self,person):
      print("adult")

    def register_person(self,face):
        print("adult register") 

  class old(Check,register):
    def check_person(self,person):
      print("old")

    def register_person(self,face):
        print("old register") 
        

```


















* The Liskov Substitution Principle (LSP):

The Liskov Substitution Principle states that any subclass object should be substitutable for the superclass object from which it is derived. This semantic relationship often called behavioral subtyping, is applied to develop more correct, extendable, and reusable software.For example:

```python
    class School:
      def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study") 

     def Uniform():
       print("Uniform required")    


    class Collage(School):
      def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study") 

     def Uniform():
       print("Uniform required")    

    class WebPoint(School):
      def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study") 

     def Uniform():
       print("Uniform required")    
       
```

According to the Liskov principle object of parent should be replaceable by the object of child class.But i webpoint class There is no uniform so uniform method dosenot suit for the web point.So the child class  object of Webpoint cannot replace base class.

```python
 class School:
      def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study") 
class Uniform(School):
  def uniform():
    print("Uniform")

class Collage(Unifrom):
      def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study") 

     def Uniform():
       print("Uniform required") 


class Webpoint(School):
   def assignment():
        print("ASSIgnment")

      def Time():
        print("Time to study")




```





* The Interface Segregation Principle (ISP):

The Interface Segregation Principle States that if there are more interface then problem will be more.
In the field of software engineering, the interface-segregation principle (ISP) states that no code should be forced to depend on methods it does not use.In the field of software engineering, the interface-segregation principle (ISP) states that no code should be forced to depend on methods it does not use.
For example of breaking Interface Segregation pricnciple:

```python
   class animal():
     def leg(self):
       raise NotImplementedError

     def hand(self):
       raise NotImplementedError

     def tail(self):
       raise NotImplementedError

   class cow(animal):
     def leg(self):
          print("Leg")
     def hand(self):
       print("Hand")

     def tail(self):
       print("tail")

   class man(animal):
     def leg(self):
       print("Leg")

     def hand(self):
       Print("Hand")

     def tail(self):
       raise NotImplementedError
    
```
Here Class man derived from class animal but def tail doesnot comes to meet which fails the ISP.So to implement ISP in above code like the following style:

```python
from abc import ABC,abstarctmethod


  class lowerbody():
    @abstarctmethod
    def leg(self):
       pass

    class uperbody():
    @abstarctmethod
    def hand(self):
       pass


   class back():
    @abstarctmethod
    def tail(self):
       pass

  class Cow(leg,hand,tail) :
    def leg(self):
       print("Leg")

    def hand(self):
       print("Hand")

    def tail(self):
       print("tail")
   
   
  class Man(leg,hand) :
    def leg(self):
       print("Leg")

    def hand(self):
       print("Hand")

```

* The Dependency inversion Principle (DIP):

Dependency inversion principle is one of the principles on which most of the design patterns are build upon. Dependency inversion talks about the coupling between the different classes or modules. It focuses on the approach where the higher classes are not dependent on the lower classes instead depend upon the abstraction of the lower classes. The main motto of the dependency inversion is Any higher classes should always depend upon the abstraction of the class rather than the detail.

```python
class Manager(object):
	def __init__(self):
		self.developers=[]
		self.designers=[]
		self.testers=[]

	def addDeveloper(self,dev):
		self.developers.append(dev)
		
	def addDesigners(self,design):
		self.designers.append(design)
		
	def addTesters(self,testers):
		self.testers.append(testers)

	
class Developer(object):
	def __init__(self):
		print "developer added"
	
class Designer(object):
	def __init__(self):
		print "designer added"
	
class Testers(object):
	def __init__(self):
		print "tester added"
	
if __name__ == "__main__":
	a=Manager()
	a.addDeveloper(Developer())
	a.addDesigners(Designer())

```
