
```java
import java.util.LinkedList;
import java.util.List;


class Main{

        public static void main(String[] args) {

            GeometricBody cube = new Cube(2);
            GeometricBody sphere = new Sphere(3);
            GeometricBody parallelepiped = new Parallelepiped(2, 3, 5);

            LinkedList<GeometricBody> bodies = new LinkedList();
            bodies.add(cube);
            bodies.add(sphere);
            bodies.add(parallelepiped);

            System.out.println(cube);
            System.out.println(sphere);

            System.out.println(parallelepiped);

            System.out.printf("One of the biggest volume: %.2f \n", new GeometricBodyController().greatestVolume(bodies));
            System.out.printf("One of the biggest surface: %.2f",  new GeometricBodyController().greatestSurface(bodies));
        }
    }


abstract class GeometricBody {

    abstract double getSurface();

    abstract double getVolume();
    
}

class Cube extends GeometricBody {
    double side;

    public Cube(double side) {
        super();
        this.side = side;
    }

    @Override
    double getSurface() {
        return 6 * Math.pow(side, 2);
    }

    @Override
    double getVolume() {
        return Math.pow(side, 3);
    }

    @Override
    public String toString() {
        return "Cube {" +
                "side= " + side + ", "+
                "surface= " + this.getSurface() + ", "+
                "volume= " + this.getVolume() +
                " }";
    }
}

class Sphere extends GeometricBody {
    double radius;

    public Sphere(double radius) {
        super();
        this.radius = radius;
    }

    @Override
    double getSurface() {
        return 4 * Math.PI * Math.pow(radius, 2);
    }

    @Override
    double getVolume() {
        return 4 / 3 * Math.PI * Math.pow(radius, 3);
    }

    @Override
    public String toString() {
        return "Sphere {" +
                "radius= " + radius + ", "+
                "surface= " + this.getSurface() + ", "+
                "volume= " + this.getVolume() +
                " }";
    }
}

class Parallelepiped extends GeometricBody {
    double length;
    double width;
    double height;

    public Parallelepiped(double length, double width, double height) {
        super();
        this.length = length;
        this.width = width;
        this.height = height;
    }

    @Override
    double getSurface() {
        return 2 * (length * width + width * height + height * length);
    }

    @Override
    double getVolume() {
        return length * width * height;
    }

    @Override
    public String toString() {
        return "Parallelepiped{" +
                "length= " + length + ", " +
                "width= " + width + ", " +
                "height= " + height + ", " +
                "surface= " + this.getSurface() + ", "+
                "volume= " + this.getVolume() +
                " }";
    }
}

class GeometricBodyController {
    double greatestVolume(List<GeometricBody> geometricBodyList) {

        // Java 8 features
        return geometricBodyList.stream()
                .mapToDouble(GeometricBody::getVolume)
                .max().orElse(0);

    }

    double greatestSurface(List<GeometricBody> geometricBodyList) {
        return geometricBodyList.stream()
                .mapToDouble(GeometricBody::getSurface)
                .max().orElse(0);
    }
}
```

