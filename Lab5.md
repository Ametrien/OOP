A.java
```java
package University.lab5;

/**
 * Task1
 * Create 10 classes with their names as first 10 aphabetical letters (A, B, C, D, ... , J).
 * Each next class inherits from previous letter class (ex: B inherits from A, C inherits from B ...).
 * 
 * Each class should have their own String property with corresponding letter as their refference
 * (ex: A - public String a; public B - String b; ... J - public String j;).
 * 
 * Create by an object of each class type and print it in console in a clever way (such that to be clear each objects states).
 */

public class A {
    protected String a;
    protected X x = new X("X from A");

    public A(String txt, X x) {
        this.a = txt;
        System.out.println("Constructor " + a);

    }
}
```

B.java
```java
package University.lab5;

public class B extends  A{
    protected String b;
    public B(String txt){
        super(txt, new X("X from B"));
        this.b = txt;
        System.out.println("Constructor " + b);

    }
}
```

C.java
```java
package University.lab5;

public class C extends  B{
    protected String c;
    public C(String txt){
        super(txt);
        this.c = txt;
        System.out.println("Constructor " + c);
    }
}
```

D.java
```java
package University.lab5;

public class D extends C{
    protected String d;
    protected X x = new X("X from D");
    public D(String txt){
        super(txt);
        this.d = txt;
    }
}
```

E.java
```java
package University.lab5;

public class E extends D{
    protected String e;
    public E(String txt){
        super(txt);
        this.e = txt;
        System.out.println("Constructor " + e);
    }
}
```

F.java
```java
package University.lab5;

public class F extends E{
    protected String f;
    public F(String txt){
        super(txt);
        this.f = txt;
        System.out.println("Constructor " + f);
    }
}
```

G.java
```java
package University.lab5;

public class G extends F{
    protected String g;
    public G(String txt){
        super(txt);
        this.g = txt;
        System.out.println("Constructor " + g);
    }
}
```

H.java
```java
package University.lab5;

public class H extends G {
    protected String h;
    private X x = new X("X from H");
    public H(String txt){
        super(txt);
        this.h = txt;
        System.out.println("Constructor " + h);
    }
}
```

I.java
```java
package University.lab5;

public class I extends H {
    protected String i;
    public I(String txt){
        super(txt);
        this.i = txt;
        System.out.println("Constructor " + i);
    }
}
```

J.java
```java
package University.lab5;

public class J extends I {
    protected String j;
    public J(String txt){
        super(txt);
        this.j = txt;
        System.out.println("Constructor: " + j);
    }

    public static void main(String[] args) {
        A classA = new A("from A", new X("from X"));
        B classB = new B("from B");
        C classC = new C("from C");
        D classD = new D("from D");
        E classE = new E("from E");
        F classF = new F("from F");
        G classG = new G("from G");
        H classH = new H("from H");
        I classI = new I("from I");
        J classJ = new J("from J");
    }
}
```


X.java
```java
package University.lab5;

public class X {
    private String x;
    public X(String txt){
        this.x = txt;
        System.out.println("Constructor " + x);
    }
}
```
