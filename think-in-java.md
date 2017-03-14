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