# Packages

## Learning Goals

- Create and use packages

## Introduction

We have briefly mentioned packages in passing before in previous lessons,
like the lesson on access modifiers. Let's talk more about packages now
and how to use them in Java.

## Packages in Java

Every time we have created a class so far, we have not specified a "package" for
it. In Java, **packages** are used to organize classes into "namespaces". Think
of a namespace as a bucket filled with seashells. Every seashell collected in
the bucket is different from all the other shells inside. The same can be said
about classes inside a package. Every class must have a name that is unique
within the package.  However, it is possible for
classes in different packages to have the same name.

Let's say a company, The Acme Corp, wants to implement a student grading
functionality, and I, The Dunder Mifflin company, also want to implement a
student grading functionality. We both have the brilliant idea to create a
class named `StudentGradeTranslator` to help translate numerical grades into letter grades.

If Java only had a single namespace for all the classes that all the programmers
in the world ever wanted to create, then a lot of class names would collide for people
who wanted to implement similar functionality, like our 2 companies in the
example above.

By convention, package names usually start with the reverse of a company's
domain name. E.g. `com.acme` and `com.dundermifflin` for the 2 fictional
companies in our example. From there, most companies package their classes based
on the systems and sub-systems they represent. So my `StudentGradeTranslator`
class may end up in a package named `com.dundermifflin.grading` while the
Acme's class may end up in a package named `com.acme.education`.

Here are the main things you should know about packages in Java:

1. A package definition is not required for a class in Java - without one, the
   class belongs to the default namespace. Note: this is not recommended for any
   classes you will share with other developers/companies, as it is likely to
   create confusion and potential name collisions.
2. When a class belongs to a certain package, the package definition must be the
   first instruction in the class' source code and follow this format: `package
   <package-name>;`. Let's see what this would look like in the code:

    ```java
    package com.dundermifflin.grading;
    
    public class StudentGradeTranslator {
        // Contents of the StudentGradeTranslator class
    }
    ```

3. Note that the rest of the class definition remains the same.
4. Anyone who would want to use my class would have to import it using the
   **fully qualified class name**, which starts with the package name
   followed by a "." and the name of the class. For my example, I could import
   my `StudentGradeTranslator` class which resides in the
   `com.dundermifflin.grading` package with the following `import` statement:
   `import com.dundermifflin.grading.StudentGradeTranslator`.
5. All classes within the same package can see and use each other without
   needing an `import` statement. This means, if I were to have other classes
   in the `com.dundermifflin.grading` package I would not need to import my
   `StudentGradeTranslator` class into those classes since they are all under
   the same package.
6. As we have seen in the lesson on access modifiers, packages play a part in
   how classes, variables, methods, and constructors can access one another.
   The default access modifier allows variables, methods, and constructors in a
   class to be visible to any other classes in the same package. This means, if
   we were to define a method without an access modifier attached to it, classes
   within the same package could directly access that method.

It should also be noted that the **default package** in Java is the `java.lang`
package. Therefore, every program in Java uses this package and any classes
within this package will not need to be imported.

## Directory Structure

Although the Java Language Specification does not require this, 
Java often relies on hierarchical file systems for managing files
and the package name relates to the directory structure in which the class resides.
This means a class is stored in a directory with a relative path matching the package name.
Thus, the `StudentGradeTranslator` class would be stored in the directory structure
`com/dundermifflin/grading`.


```java
package com.dundermifflin.grading;

public class StudentGradeTranslator {
    // Contents of the StudentGradeTranslator class
}
```

![directory structure](https://curriculum-content.s3.amazonaws.com/6676/java-multipleclasses/directorystructure.png)

## Resources

[Java Packages](https://docs.oracle.com/javase/tutorial/java/package/index.html)