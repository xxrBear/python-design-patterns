# 简单工厂模式

## 简介

简单工厂模式不是它不是 GoF 23 个正式设计模式之一，但在实际开发中非常常用，尤其是小型应用场景，当需要根据不同条件创建不同的对象时，一个工厂类根据传入参数决定创建哪一种产品（实例化逻辑集中在一个类中）

## 示例

```python
class Animal:
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

class AnimalFactory:
    @staticmethod
    def create_animal(animal_type: str) -> Animal:
        if animal_type == "dog":
            return Dog()
        elif animal_type == "cat":
            return Cat()
        else:
            raise ValueError(f"Unknown animal type: {animal_type}")
```

## 优缺点

简单工厂方法很简单，利用工厂类来实现子类的创建，它很适合一些小型的代码块任务，但是它也有缺点，它的实现违反了开放-封闭原则（即对修改关闭，对扩展开放），想一想，如果我们要增加一个动物类，我们需要修改`create_animal`方法，这并不是最佳实践
