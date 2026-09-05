# Methods

| Return type | What is returned |
|---|---|
| Primitive | The primitive value |
| Object | A reference to the object |

> [!IMPORTANT]
> Returning an object does **not** return a copy of the object.
> The returned reference refers to the same object.

<table>
<tr>
<th>Example</th>
<th>Code</th>
<th>Return</th>
</tr>
<tr>
<td><strong>Example 1</strong></td>
<td>
<pre><code class="language-java">class Car {
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
}</code></pre>
</td>
<td>
<pre><code>red
Car@1dbd16a6
Car@1dbd16a6</code></pre>
</td>
</tr>
<tr>
<td><strong>Example 2</strong></td>
<td>
<pre><code class="language-java">class CarLot {
    Car carInLot;
    public CarLot(Car givenCar) {
        carInLot = givenCar;
    }
    public Car returnACar() {
        return carInLot;
    }
    public static void main(String[] args) {
        Car myCar = new Car("red", 70);
        System.out.println(myCar);
        CarLot myCarLot = new CarLot(myCar);
        System.out.println(myCarLot.returnACar());
    }
}</code></pre>
</td>
<td>
<pre><code>Car@2f333739
Car@2f333739</code></pre>
</td>
</tr>
</table>

> [!NOTE]
> This happens because println() calls the toString() method when given an object.
> 
> Every Java class inherits a toString() method from Object, unless the class overrides it.
> 
> The default implementation in Object returns a string containing the object's class name and hash code:
> 
> ```java
> public String toString() {
>     return getClass().getName() + "@" + Integer.toHexString(hashCode());
> }
> ```