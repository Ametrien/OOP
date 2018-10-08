
#### Task #1 
```
/*Create a program where you can manipulate a monitor object which has color, 
 * dimensions and resolution. Implement actions of creation, update of monitor 
 * properties and comparison between two monitors.*/

public class Monitor {

	private String color;
	private int dimension;// the length of its diagonal
	private int resolutionX;
	private int resolutionY;

	public Monitor() {
		//default constructor
		this.color = "";
		this.dimension = 0;
		this.resolutionX = 0;
		this.resolutionY = 0;
	}
	
	public Monitor(String c, int d, int rX, int rY) {
		//Copy constructor
		this.color = c;
		this.dimension = d;
		this.resolutionX = rX;
		this.resolutionY = rY;
	}
	
	public void setColor(String c) {
		this.color = c;
	}
	
	public String getColor() {
		return this.color;
	}
	
	public void setDimension(int d) {
		this.dimension = d;
	}
	
	public int getDimension() {
		return this.dimension;
	}
	
	public void setResolution(int rX, int rY) {
		this.resolutionX = rX;
		this.resolutionY = rY;
	}
	
	public int getResolutionX() {
		return this.resolutionX;
	}
	
	
	public int getResolutionY() {
		return this.resolutionY;
	}
	
	public boolean compare(Monitor m) {
		return ((this.color).equals(m.color) &&
				(this.dimension== m.dimension) &&
				(this.resolutionX== m.resolutionX) &&
				(this.resolutionY== m.resolutionY)
				);
	}
	
	public void printCaracteristics() {
		System.out.println("Color: " + this.color);
		System.out.println("Dimension: " + this.dimension);
		System.out.println("Rezolution: " + this.resolutionX + "x" + this.resolutionY);
		System.out.println();
	}

	public static void main(String[] args) {
		Monitor monitor = new Monitor();
		monitor.setColor("red");
		monitor.setDimension(27);
		monitor.setResolution(567, 1702);
		monitor.printCaracteristics();
		
		Monitor monitor1 = new Monitor("red", 27, 567, 1702);
		monitor1.printCaracteristics();
		
		Monitor monitor2 = new Monitor("blue", 23, 823, 1890);
		monitor1.printCaracteristics();
		
		System.out.println("Is first monitor equal to second: " + monitor.compare(monitor1));
		System.out.println("Is second monitor equal to third: " + monitor1.compare(monitor2));
		
		
	}

}

```

![Image 1](https://github.com/AnastasiaFAF172/OOP/blob/images/01.png)

#### Task #2

```

/*Create a program where you can create and have some actions to the following objects: 
 * university and student. You should be able to create students that have name, age and 
 * mark from their courses and also to create universities which have name, foundationYear 
 * and a list of students created earlier.
 * In main program you should be able to create 3 universities with some students in it 
 * and calculate the average media between them and print the result in console.*/
public class Task2 {

	public static class Student {
		private String name;
		private int age;
		private float mark;

		public Student() {
			// default constructor
			this.name = "";
			this.age = 0;
			this.mark = 0;
		}

		public Student(String n, int a, float m) {
			// Copy constructor
			this.name = n;
			this.age = a;
			this.mark = m;
		}

		public void setName(String n) {
			this.name = n;
		}

		public String getName() {
			return this.name;
		}

		public void setAge(int a) {
			this.age = a;
		}

		public int getAge() {
			return this.age;
		}

		public void setMark(float m) {
			this.mark = m;
		}

		public float getMark() {
			return this.mark;
		}

		public void printStudent() {
			System.out.println("  Name: " + this.name);
			System.out.println("   Age: " + this.age);
			System.out.printf("   Mark: %.2f", this.mark);
			System.out.println();
		}
	}

	public static class University {
		// name, foundationYear and a list of students
		private String name;
		private int foundationYear;
		private Student[] students;

		public University() {
			// default constructor
			this.name = "";
			this.foundationYear = 0;

		}

		public University(String n, int f) {
			// Copy constructor
			this.name = n;
			this.foundationYear = f;
		}

		public void setName(String n) {
			this.name = n;
		}

		public String getName() {
			return this.name;
		}

		public void setYear(int y) {
			this.foundationYear = y;
		}

		public int getAge() {
			return this.foundationYear;
		}

		public void addStudent(Student[] st) {
			this.students = st.clone();
		}

		public void printUniversity() {
			System.out.println("Name: " + this.name);
			System.out.println("Foundation Year: " + this.foundationYear);
			System.out.println("Students: ");
			for (int i = 0; i < students.length; i++) {
				students[i].printStudent();
			}
			
			System.out.printf("Average mark: %.2f", this.avgMark());
			System.out.println();
			System.out.println();
		}

		public float avgMark() {
			float sum = 0;
			for (int i = 0; i < students.length; i++) {
				sum += students[i].getMark();
			}
			return sum / students.length;
		}

	}

	public static void main(String[] args) {
		Student[] ASEM_stud = new Student[3];
		ASEM_stud[0] = new Student("Connor", 19, (float) 9.52);
		ASEM_stud[1] = new Student("Hank", 20, (float) 7.37);
		ASEM_stud[2] = new Student("Amanda", 21, (float) 9.17);
		University ASEM = new University("ASEM", 1991);
		ASEM.addStudent(ASEM_stud);
		ASEM.printUniversity();

		Student[] USM_stud = new Student[3];
		USM_stud[0] = new Student("Kara", 21, (float) 9.92);
		USM_stud[1] = new Student("Alice", 18, (float) 8.86);
		USM_stud[2] = new Student("Luthor", 22, (float) 6.73);
		University USM = new University("USM", 1946);
		USM.addStudent(USM_stud);
		USM.printUniversity();

		Student[] UTM_stud = new Student[3];
		UTM_stud[0] = new Student("Markus", 20, (float) 9.05);
		UTM_stud[1] = new Student("North", 19, (float) 8.36);
		UTM_stud[2] = new Student("Simon", 21, (float) 9.81);
		University UTM = new University("UTM", 1946);
		UTM.addStudent(UTM_stud);
		UTM.printUniversity();

		float avg = (ASEM.avgMark() + USM.avgMark() + UTM.avgMark()) / 3;
		System.out.printf("Average media: %.2f", avg);

	}

}

```

![Image 2](https://github.com/AnastasiaFAF172/OOP/blob/images/02.png)
