#Java tips

## interface:
> 不影响父类，只影响子类

## java reflection:
> Judge the class of an object in running time.

### Class class
> Every class have a Class class which contains the methods name, variables name and other necessary informations.

how to get?

* object.getClass()
* forName() 
    
    > Class static method.

* object.class 
    
    > if object is basic type(int, float), use .TYPE instead.

## The diff between classpath and buildpath
> 1. Classpath is the conventional way to tell the Java compiler and the Java runtime where to find compiled classes. It is typically a sequence of JAR file names and directory names.
> 2. Buildpath is the way that IDE specifies the relationship between the 'modules' or 'projects' that make up this application. The IDE uses this to figure out the classpath and sourcepath for compiling the Java Code, and the classpath for running it.

## java and factory:

* simple factory mode:
* factory methods mode:
```java
//abstract production character.
public interface Moveable {
    void run(){}
}
//specific production character.
public class Plane implements Moveable{
    @override
    public void run() {
        System.out.println("Plane...")
    }
}
public class Broom implements Moveable {
    @override
    public void run() {
        System.out.println("Broom...")
    }
}
//abstract factory
public abstract class VehicleFactory {
    abstract Moveable create();
}
//specific factory
public class PlaneFactory implements VehicleFactory{
    @override
    public Moveable create() {
        return new Plane();
    }
}
public class BroomFactory implements VehicleFactory{
    @override
    public Moveable create() {
        return new Broom()
    }
}
//Test class
public class Test {
    public static void main(String [] args){
        VehicleFactory factory = new BroomFactory();
        Moveable m = factory.create();
    }
}
```
* abstract factory mode:
> benefit: Maybe your codes have many `var = new Plane()`. when you change your codes to `var = new Plane_1()` it would cause much work. By using factory, you only need to change factory. `Vehicle v = f.createVehicle();`don't need being changed.
```java
//abstract production character
public interface Moveable {
    void run(){}
}
//specific production character
public class Plane implements Moveable {
    @override
    public void run() {
        System.out.println("Plane...")
    }
}
public class Broom implements Moveable {
    @override
    public void run() {
        System.out.println("Broom...")
    }
}
//abstract factory
public abstract class AbstractFactory() {
    public abstract Vehicle createVehicle();
    public abstract Weapon createWeapon();
    public abstract Food createFood();
}
//specific factory
public class DeafaultFactory extends AbstractFactory {
    @override
    public Vehicle createVehicle() {
        return new Car();
    }
    @override
    public Food createFood() {
        return new Apple();
    }
    @override
    public Weapon createWeapon() {
        return new AK47();
    }
}
public class Test {
    public static void main() {
        AbstractFactory f = new DefaultFactory();
        Vehicle v = f.createVehicle();
        v.run();
        Weapon w = f.createWeapon();
        w.shoot();
        Food a = f.createFood();
        s.eat();
    }
}
```