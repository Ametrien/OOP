![Image 1](https://www.uml-diagrams.org/examples/class-example-hospital-organization.png)

![Image 2](https://github.com/AshleyBlair/OOP/blob/images/Organization.png)

AdministrativeStaff.java
 
``` 
package com.utm.app;

public class AdministrativeStaff implements Staff {
}
```
Department.java

```
package com.utm.app;

public interface Departament extends Hospital{
}
```
Doctor.java

```
package com.utm.app;

public class Doctor implements OperationsStaff {
    public void doSmth(){
        System.out.println("Hello from Doctor" );
    }
}
```

FrontDeskStaff.java

```
package com.utm.app;

public class FrontDeskStaff extends AdministrativeStaff {
}
```

Hospital.java

```
package com.utm.app;

public interface Hospital {
    String name = "";
    String address = "";
    String phone = "";
}
```

Nurse.java

```
package com.utm.app;

public class Nurse implements OperationsStaff {
}
```
OperationsStaff.java

```
package com.utm.app;

public interface OperationsStaff extends Patient, Staff {
}
```

Patient.java
```
package com.utm.app;

public interface Patient extends Person {
}
```

Person.java
```
package com.utm.app;

import java.util.Date;

public interface Person {
    String title = "";
    String givenTitle = "";
    String midleTitle = "";
    String familyTitle = "";
    String name = title + " " + givenTitle + " " + midleTitle + " " + familyTitle;
    Date birthDate = new Date(2018, 04, 04); // deprecated constructor
    char gender = 'f';
    String homeAddress = "";
    String phone = "";
}
```

Receptionist.java

```
package com.utm.app;

public class Receptionist extends FrontDeskStaff {
    public static void main(String[] args) {
        Doctor d = new Doctor();
        d.doSmth();
    }
}
```

Staff.java

```
package com.utm.app;

public interface Staff extends Departament, Person {
}
```

Surgeon.java

```
package com.utm.app;

public class Surgeon extends Doctor {
}
```

SurgicalTehnologist.java

```
package com.utm.app;

public class SurgicalTehnologist extends Tehnologist {
}
```
TehnicalStaff.java

```
package com.utm.app;

public interface TehnicalStaff extends Staff {
}
```

Tehnician.java
```
package com.utm.app;

public class Tehnician implements TehnicalStaff {
}
```

Tehnologist.java
```
package com.utm.app;

public class Tehnologist implements TehnicalStaff {
}
```

