# 物件導向程式設計(0bject-Oriented Programming)
- [參考資料](https://www.geeksforgeeks.org/python-oops-concepts/)
- [Python OOPS 測驗](https://www.geeksforgeeks.org/quizzes/python-oops-quiz/)

## 類別(Class)與物件(0bject)
- 類別(Class)
  - 類別是物件的集合。
  - 類別(Class)是用於創建物件的藍圖。
  - 類別(Class)定義了物件(object| instance |實例）可以具有的一組`屬性(attributes)`和`方法(methods)`。
  - 類別(Class)由關鍵字 class 創建。 ==> class Dog
  - 屬性是屬於類別的變數。
  - 屬性與方法的存取==>使用點 （.） 運算符==>Myclass.Myattribute
- 物件(0bject)
  - Object 是 Class 的實例|物件。
  - 它表示Class的特定實現並保存自己的數據。
  - 物件包括：
    - 狀態(State)：它由`屬性`表示，並反映對象的屬性。
    - 行為(Behavior)：它由物件的`方法`表示，並反映物件對其他對象的回應。
    - 標識(Identity)|名字：它為物件提供唯一`名稱`。
  - 建立物件 ==> 物件實例化
    - 在 Python 中創建物件==> 實例化一個類別以創建該類別的新實例。 
```python
# ---------------------------定義類別 ---------------------------------------
class Dog:
    species = "Canine"  # 類別屬性(Class attribute)|Class Variable : 定義在所有方法外面|所有物件共用的類別屬性

## __init__方法：每一個類別都要有|創建新物件時初始化 name 和 age 屬性
## 又稱建構子|constructor|建構函數
    def __init__(self, name, age):
        self.name = name  # 物件屬性(Instance attribute)|Instance Variables
        self.age = age  # 物件屬性(Instance attribute)|Instance Variables
## self 參數 ==>該參數是對 current 實例
## 您可以隨便稱呼它(例如myself)，但它必須是__init__函數的第一個參數
## __init__ ==> python 魔術方法(magic method) 特殊定義的

# 物件屬性(Instance attribute)|Instance Variables ==>每個物件都維護自己的實例變數副本，獨立於其他物件
# 在 __init__ 方法中定義

# ----------------------建立物件---------------------------
dog1 = Dog("Buddy", 3)  # Create an instance of Dog
dog2 = Dog("Charlie", 5)  # Create another instance of Dog

# ----------------------物件運行---------------------------
print(dog1.name, dog1.age, dog1.species)  # 物件屬性與類別屬性的存取
print(dog2.name, dog2.age, dog2.species)  # 物件屬性與類別屬性的存取
print(Dog.species)  # 類別屬性的存取
```
## Python `Encapsulation|封裝`
- 封裝是將資料（屬性| Data Member）和方法（函數）捆綁在一個類別中，並限制對某些元件的存取。
- 封裝類型：
  - Public Members(公共成員)：誰都可以存取。
  - Protected Members（保護成員）：類別及其子類別可存取。==> self.`_`breed
  - Private Members（私有成員）：只能在類別中存取。==>  self.`__`age
```python
class Dog:
    def __init__(self, name, breed, age):
        self.name = name  # 公共成員
        self._breed = breed  # 保護成員
        self.__age = age  # 私有成員

    # Public method
    def get_info(self):
        return f"Name: {self.name}, Breed: {self._breed}, Age: {self.__age}"

    # 針對 Private Members（私有成員）設計的get方法(getter)與set方法(setter)
    def get_age(self):
        return self.__age

    def set_age(self, age):
        if age > 0:
            self.__age = age
        else:
            print("Invalid age!")

# 建立物件
dog = Dog("Buddy", "Labrador", 3)

# 存取公共成員
print(dog.name)  

# 存取保護成員
print(dog._breed)  # Accessible but discouraged outside the class

# 存取私有成員 ==> 要使用特別設計的get方法
print(dog.get_age())

# 修訂私有成員 ==> 要使用特別設計的set方法 
dog.set_age(5)
print(dog.get_info())
```


## 類別繼承|Inheritance ==> 類別與類別的關係1
- 允許一個類別（子類別）獲取另一個類別（父類別）的屬性和方法。
- 它支援分層分類並促進`代碼重用(code use)`。
- 繼承類型：
  - 單一繼承(Single Inheritance)：子類別繼承自單個父類別。
  - 多重繼承(Multiple Inheritance)：一個子類別繼承自多個父類別。
  - 多層繼承(Multilevel Inheritance)：子類別繼承自父類別，而父類別又繼承自另一個類別(阿公類別)。
  - 分層繼承(Hierarchical Inheritance)：多個子類別繼承自單個父類別。
  - 混合繼承(Hybrid Inheritance)：兩種或多種類型的繼承的組合。
```python
# 單一繼承(Single Inheritance)：子類別(Labrador)繼承自單個父類別(Dog)
class Dog:
    def __init__(self, name):
        self.name = name

    def display_name(self):
        print(f"Dog's Name: {self.name}")

class Labrador(Dog):  # 單一繼承
    def sound(self):
        print("Labrador woofs")

# 多層繼承(Multilevel Inheritance)
class GuideDog(Labrador):  # Multilevel Inheritance
    def guide(self):
        print(f"{self.name}Guides the way!")

# 多重繼承(Multiple Inheritance)：一個子類別繼承自多個父類別 ==> GoldenRetriever(Dog, Friendly)
class Friendly:
    def greet(self):
        print("Friendly!")

class GoldenRetriever(Dog, Friendly):  # 多重繼承(Multiple Inheritance)
    def sound(self):
        print("Golden Retriever Barks")

# Example Usage
lab = Labrador("Buddy")
lab.display_name()
lab.sound()

guide_dog = GuideDog("Max")
guide_dog.display_name()
guide_dog.guide()

retriever = GoldenRetriever("Charlie")
retriever.display_name()
retriever.greet()
retriever.sound()
```
## 抽象類別 | abstract class
```python
# 載入abc
from abc import ABC, abstractmethod

# 定義抽象類別
class Animal(ABC):
    
    @abstractmethod
    def sound(self):
        pass  # This is an abstract method, no implementation here.

# 定義子類別 ==> 繼承父類別Animal(這是一個抽象類別)
class Dog(Animal):

# 子類別繼承抽象類別時，必須實作所有標記為抽象的方法，否則會引發TypeError    
    def sound(self):
        return "Bark"  # Providing the implementation of the abstract method

# 建立物件
dog = Dog()
print(dog.sound())  # Output: Bark
```


## `資料抽象|Data Abstraction`
- 資料抽象==>隱藏內部實作細節，只公開必要的功能。
- 它有助於專注於 「做什麼」 而不是 「如何做」。
- 資料抽象類型：
  - 部分資料抽象|Partial Abstraction:：抽象類別包含有`抽象方法(abstract methods)`和`具體方法(concrete methods)`。
  - 完全資料抽象|Full Abstraction：抽象類別只有`抽象方法(abstract methods)`（如介面）。
```python
from abc import ABC, abstractmethod

class Dog(ABC):  # Dog抽象類別
    def __init__(self, name):
        self.name = name

    @abstractmethod
    def sound(self):  # 抽象方法(abstract methods)
        pass

    def display_name(self):  # 具體方法(abstract methods)
        print(f"Dog's Name: {self.name}")

class Labrador(Dog):  # Partial Abstraction
    def sound(self):
        print("Labrador Woof!")

class Beagle(Dog):  # Partial Abstraction
    def sound(self):
        print("Beagle Bark!")

# Example Usage
dogs = [Labrador("Buddy"), Beagle("Charlie")]
for dog in dogs:
    dog.display_name()  # Calls concrete method
    dog.sound()  # Calls implemented abstract method
```
# Python Polymorphism|多態性
- 多態性允許方法具有相同的名稱，但根據物件的上下文而具有不同的行為。
- 可以通過`方法覆寫(method overriding)`或`方法重載(method overloading)`來實現。
- 多態性的類型
  - 編譯時多態性|Compile-Time Polymorphism：這種類型的多態性是在程式編譯期間確定的。它允許具有相同名稱的方法或運算符根據其輸入參數或用法做出不同的行為。它通常稱為方法或運算子重載。
  - 運行時多態性|Run-Time Polymorphism：這種類型的多態性是在程式執行期間確定的。當子類為其父類中已定義的方法提供特定實現時，就會發生這種情況，通常稱為方法覆蓋。
```python
# Parent Class
class Dog:
    def sound(self):
        print("dog sound")  # Default implementation

# Run-Time Polymorphism: Method Overriding
class Labrador(Dog):
    def sound(self):
        print("Labrador woofs")  # Overriding parent method

class Beagle(Dog):
    def sound(self):
        print("Beagle Barks")  # Overriding parent method

# Compile-Time Polymorphism: Method Overloading Mimic
class Calculator:
    def add(self, a, b=0, c=0):
        return a + b + c  # Supports multiple ways to call add()

# Run-Time Polymorphism
dogs = [Dog(), Labrador(), Beagle()]
for dog in dogs:
    dog.sound()  # Calls the appropriate method based on the object type


# Compile-Time Polymorphism (Mimicked using default arguments)
calc = Calculator()
print(calc.add(5, 10))  # Two arguments
print(calc.add(5, 10, 15))  # Three arguments
```

## 方法覆蓋|overridding
- https://www.geeksforgeeks.org/method-overriding-in-python/
- 在 Python 中，方法覆蓋是指子類別中的方法與其父類別中的方法具有相同的名稱、相同的參數和相同的返回類型，但提供不同的實現。
- 這允許子類別修改或擴展 super-class 方法的行為。
- 要覆蓋方法，子類別必須繼承自超類別，並創建一個與超類別方法具有相同名稱和參數數量的方法。
```python
# Python program to demonstrate 
# Defining parent class 
class Parent(): 
	
	# Constructor 
	def __init__(self): 
		self.value = "Inside Parent"
		
	# Parent's show method 
	def show(self): 
		print(self.value) 
		
# Defining child class 
class Child(Parent): 
	
	# Constructor 
	def __init__(self): 
		super().__init__()  # Call parent constructor
		self.value = "Inside Child"
		
	# Child's show method 
	def show(self): 
		print(self.value) 
		
# Driver's code 
obj1 = Parent() 
obj2 = Child() 

obj1.show()  # Should print "Inside Parent"
obj2.show()  # Should print "Inside Child"
```
## 重載| Overloading
- https://www.geeksforgeeks.org/python-method-overloading/
- 在 Python 中，重載是指定義名稱相同但參數不同的方法或函數的能力。
- 重載有兩種主要類型：
  - 方法重載(Method Overloading)：這允許一個類具有多個名稱相同但參數不同的方法。要執行的方法由傳遞的參數的數量和類型決定。
  - 運算子重載(Operator Overloading)：這允許通過重新定義運算符調用的方法來修改運算元（如 +、- 等）的行為，使它們能夠使用使用者定義的類型。
- 總的來說，重載允許根據輸入參數將相同的方法名稱用於不同的功能，從而提高了代碼的可重用性和可讀性
```python
# First product method.
# Takes two argument and print their
# product


def product(a, b):
    print(`A888888`)
    p = a * b
    print(p)

# Second product method
# Takes three argument and print their
# product


def product(a, b, c):
    print(`A888168`)
    p = a * b*c
    print(p)

# Uncommenting the below line shows an error
# product(4, 5)


# This line will call the second product method
product(4, 5, 5)
```
## 類別與類別的關係2 ==> use a 
- https://ithelp.ithome.com.tw/articles/10269231
- https://blog.visual-paradigm.com/tw/what-are-the-six-types-of-relationships-in-uml-class-diagrams/
- UML Class Diagram(類別圖)的六種類別關係
  - 繼承（Generalization / Inheritance）
  - 實現/實現（Realization / Implementation）
  - 組合（Composition）
  - 聚合（Aggregation）
  - 關聯（Association）
  - 依賴 （Dependency）
```python

```

```python

```

```python

```
