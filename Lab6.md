Implement the classes in any OOP progamming language according to the following class diagram:

![Image 1](https://www.uml-diagrams.org/examples/class-example-hospital-organization.png)

![Image 2](https://github.com/AshleyBlair/OOP/blob/images/Organization.png)

AdministrativeStaff.java
 
```java
package com.utm.app;

public class AdministrativeStaff implements Staff {
}
```
Department.java

```java
package com.utm.app;

public interface Departament extends Hospital{
}
```
Doctor.java

```java
package com.utm.app;

public class Doctor implements OperationsStaff {
    String speciality = "";
    String locations = "";
}
```

FrontDeskStaff.java

```java
package com.utm.app;

public class FrontDeskStaff extends AdministrativeStaff {
}
```

Hospital.java

```java
package com.utm.app;

public interface Hospital {
    String name = "";
    String address = "";
    String phone = "";
}
```

Nurse.java

```java
package com.utm.app;

public class Nurse implements OperationsStaff {
}
```
OperationsStaff.java

```java
package com.utm.app;

public interface OperationsStaff extends Patient, Staff {
}
```

Patient.java
```java
package com.utm.app;

public interface Patient extends Person {
    String id = "";
    String sickness = "";
    String prescriptions = "";
    String allergies = "";
    String specialReqs = "";
    Date accepted = new Date(2018, 10, 10); // deprecated constructor

}
```

Person.java
```java
package com.utm.app;

import java.util.Date;

public interface Person {
    String title = "";
    String givenTitle = "";
    String midleTitle = "";
    String familyTitle = "";
    String name = title + " " + givenTitle + " " + midleTitle + " " + familyTitle;
    Date birthDate = new Date(1998, 04, 04); // deprecated constructor
    char gender = 'f';
    String homeAddress = "";
    String phone = "";
}
```

Receptionist.java

```java
package com.utm.app;

public class Receptionist extends FrontDeskStaff {
}
```

Staff.java

```java
package com.utm.app;

public interface Staff extends Departament, Person {
    Date joined = new Date(2017, 12, 07); // deprecated constructor
    String education = "";
    String certification = "";
    String languages = "";
}
```

Surgeon.java

```java
package com.utm.app;

public class Surgeon extends Doctor {
}
```

SurgicalTehnologist.java

```java
package com.utm.app;

public class SurgicalTehnologist extends Tehnologist {
}
```
TehnicalStaff.java

```java
package com.utm.app;

public interface TehnicalStaff extends Staff {
}
```

Tehnician.java
```java
package com.utm.app;

public class Tehnician implements TehnicalStaff {
}
```

Tehnologist.java
```java
package com.utm.app;

public class Tehnologist implements TehnicalStaff {
}
```

