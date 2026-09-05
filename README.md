# Methods

Return a primitive value -> a copy of the value is returned 

Return an object -> a reference to the object is returned instead of a copy of it

Example 1

Code:
```java
class Car {
    String color;

    Car(String color) {
        this.color = color;
    }
}

public class Main {
    static Car getCar(Car car) {
        return car;
    }

    public static void main(String[] args) {
        Car myCar = new Car("red");

        Car anotherCar = getCar(myCar);

        System.out.println(anotherCar.color);
        System.out.println(myCar);
        System.out.println(anotherCar);
    }
}
```

Return:
```
red
Car@1dbd16a6
Car@1dbd16a6
```

Example 2

Code:
```java
class CarLot {
    Car carInLot;
    public CarLot(Car givenCar) {
        carInLot = givenCar;
    }

    public Car returnACar() {
        // return Car object
        return carInLot;
    }

    public static void main(String[] args) {
        Car myCar = new Car("red", 70);
        System.out.println(myCar); 
        CarLot myCarLot = new CarLot(myCar);
        System.out.println(myCarLot.returnACar());
    }
}
```

Return:
```
Car@2f333739
Car@2f333739
```

> [!NOTE]
This happens because println() calls the toString() method when given an object.
Every Java class inherits a toString() method from Object, unless the class overrides it.
The default implementation in Object returns a string containing the object's class name and hash code:
```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```