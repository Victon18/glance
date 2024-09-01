# oops
```python
def print_house_info(houses):
    print([house.no_of_windows for house in houses])
    print([house.color for house in houses])
    print([house.roof_color for house in houses])
    print([house.window_size for house in houses])
    print("--------")

class House:
    no_of_windows = 2
    breadth = 2500
    width = 5000

    def __init__(self, color, window_size):
        self.color = color
        self.window_size = window_size
        self.roof_color = "red"
        self.height = 5000  # added this attribute

    def __del__(self):
        print("house destroyed", id(self))

    def do_paint_job(self, new_color):
        self.color = new_color

    def get_data(self):
        return self.color, self.roof_color, self.window_size, self.find_area(self.width, self.height)
    # static method
    @staticmethod
    def find_area(length, breadth):
        return length * breadth
    # class method
    @classmethod
    def red_house(cls,window_size):
        return cls("red", window_size)
    # magic methods
    def __add__ (self, other):
        return self.find_area(self.width, self.breadth) + self.find_area(other.width, other.breadth)
    def __str__ (self):
        return f"House [ {self.get_data()} ]"
    def __repr__ (self):
        return f"<House [ [self.get_data] ]>"

houses = [House.red_house("sm"), House("blue", "lg"), House("green", "md")]
print_house_info(houses)
houses[1].do_paint_job("maroon")
print(houses[1].get_data())
print(House.find_area(100, 100))
print(houses[1].find_area(100, 100))
print(str(houses[1]))
print(houses[0]+houses[1])
```
# ecapsulation
```python
# nested class
import uuid
class Vehicle:
    class English:
        def __init__(self, size):
            self.engine_size = size
        def power(self):
            return self.engine_size*2
    def __init__(self, name, model, color, engine_size):
        self.name = name
        self.model = model
        self.color = color
        self.engine_size = engine_size
        #private attribute
        self.__model_id = uuid.uuid4()
    # property
    @property
    def id(self):
        return str(self.__model_id)
    # setter
    @id.setter
    def id(self,new_id):
        self.__model_id = new_id + "--- new"
    #getter
    def model_info(self):
        return f"{self.name}({self.model}) -- {self.color}"
    # setter
    def set_color(self,new_color):
        self.color = new_color

car = Vehicle("toyoyta","suv","white")
print(car.id)
print(car.model_info())

print(car.color)
car.set_color("cyan")
print(car.color)

print(car.id)
car.id = "dsbab"
print(car.id1)

```
# inheritence
```python
class Animal:
    def __init__(self, health, strength, speed):
        self.health = health
        self. strength = strength
        self.speed = speed

    def eat(self, replenishment):
        self.heath += replenishment
class Fish:
    def __init__(self):
        self.no_of_fins = 6

    def breath(self):
        pass
class Lion(Animal):
    def __init__(self, pack_no):
        # overriding
        super().__init__(100,500,20)
        self.no_of_lioness = pack_no
    def sleep(self):
        print("lion slept")
        print("lion woke")
class Whale(Animals, Fish):
    def __init__(self, multiplier):
        self.health = 10000
        self.strength = 500
        self. speed = 50
        self.no_of_fins = 2
        self.size_multiplier = multiplier

    def eat(self, no_of_shrimp):
        self.health += no_of_shrimp*2

    def kill_kraken(self):
        print("kraken killed")

animal = Whale(10)
print(animal.strength, animal.health, animal.speed)

animal.eat(100)
animal.kill_kraken()
animal.breadth()

print(animal.strength, animal.health, animal.speed)
```
# abstraction
blueprint of a class
```python
from abc import ABC, abstractmethod

class Mob(ABC):
    def __init__(self, health, speed):
        self.health = health
        self.speed = speed
    @abstractmethod
    def move(self):
        pass
    @abstractmethod
    def kill(self):
        pass
    @abstractmethod
    def revive(self):
        pass
class Zombie(Mob):
    def __init__(self):
        super().__init__(100,24)
    def move(self):
        print(" zombie Moved")
    def kill(self):
        print("Zombie killed")
    def revive(self):
        print("Zombie revived")
class Creeper(Mob):
    def __init__(self):
        super().__init__(56,10)
    def move(self):
        print("Creeper Moved")
    def kill(self):
        print("Creeper killed")
    def revive(self):
        print("Creeper revived")
```
# composition

