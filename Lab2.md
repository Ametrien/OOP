#### Task #1 
```java


/**
 * Write a class Box and instatiate an object via its constructor. The Box
 * object should have three instance variables of floating number type(double):
 * height, width, depth; It should be possible to instantiate box object in 3
 * ways:
 * 
 * without parameters (every attribute is instantiated to 1) With 1 parameter
 * (every attribute is instantiated with that parameter) With 3 parameters for
 * each attribute. The box must have also 2 methods for calculation of its
 * surface area and volume.
 */
 
public class Box {
	private double height;
	private double width;
	private double depth;

	public Box() { // without parameters
		height = 1;
		width = 1;
		depth = 1;
	}

	public Box(double value) { // with 1 parameter
		height = value;
		width = value;
		depth = value;
	}

	public Box(double height, double width, double depth) { // with 3 parameter
		this.height = height;
		this.width = width;
		this.depth = depth;
	}

	public double area() { // calculation of its surface area
		return (6 * (height * width));
	}

	public double volume() { // calculation of its volume
		return (height * width * depth);
	}

	public static void main(String[] args) {
		Box box1 = new Box();
		Box box2 = new Box(2);
		Box box3 = new Box(3,4,5);
		
		System.out.println("Area of first box: " + box1.area() + " cm2");
		System.out.println("Volume of first box: " + box1.volume() + " cm3");
		System.out.println();
		System.out.println("Area of second box: " + box2.area() + " cm2");
		System.out.println("Volume of second box: " + box2.volume() + " cm3");
		System.out.println();
		System.out.println("Area of third box: " + box3.area() + " cm2");
		System.out.println("Volume of third box: " + box3.volume() + " cm3");
		
	}
}

```

![Image 1](https://github.com/AnastasiaFAF172/OOP/blob/images/03.png)

#### Task #2

```java


/**
 * Create a class Queue and instantiate 2 objects of this type. Each queue
 * should have as state the number of elements from it and can be created via
 * constructors of 2 types - with parameter and without it. Implement add and
 * get methods for adding elements to the queue and extraction of them.
 * 
 * Also implement two methods which should determine if the queue is empty or
 * full. (isEmpty(), isFull()).
 */
 
public class Queue {
    private ObjectBox head;
    private ObjectBox tail;
    private int size;
 
    public Queue(){
    	head = null;
    	tail = null;
    	size = 0;
    }
    
    public Queue(int s){
    	head = null;
    	tail = null;
    	if(s >= 0) size = s;
    	else size = 0;
    }
    
    public void push(Object obj) { 
        ObjectBox ob = new ObjectBox();
        ob.setObject(obj);
        if (head == null) {
            head = ob;
        } else {
            tail.setNext(ob);
        }
        tail = ob;
        size++;
    }
 
   
    public Object get(int index) {
        if(size == 0 || index >= size || index < 0) {
            return null;
        }
        ObjectBox current = head;
        int pos = 0;
        while(pos < index) {
            current = current.getNext();
            pos++;
        }
        Object obj = current.getObject();
        return obj;
    }
    
    public int size() {
        return size;
    }
    
    public boolean isEmpty() {
        return (size == 0);
    }
    
    public boolean isFull() {
        return (size == 10);
    }
    
    private class ObjectBox
    {
        private Object object; 
        private ObjectBox next;
 
        public Object getObject() {
            return object;
        }
 
        public void setObject(Object object) {
            this.object = object;
        }
 
        public ObjectBox getNext() {
            return next;
        }
 
        public void setNext(ObjectBox next) {
            this.next = next;
        }
    }
    public static void main(String[] args) {
    	Queue q1 = new Queue();
    	System.out.println("Queue is empty? "+q1.isEmpty());
    	q1.push("1");
    	q1.push("2");
    	System.out.println("Queue is empty? "+q1.isEmpty());
    	System.out.println("Elements of Queue: "+q1.get(0));
    	System.out.println("Elements of Queue: "+q1.get(1));
    	Queue q2 = new Queue(10);
    	System.out.println();
    	System.out.println("Queue2 is full? "+q2.isFull());
    }
}

```
![Image 1](https://github.com/AnastasiaFAF172/OOP/blob/images/04.png)
