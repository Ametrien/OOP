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
	// Указатель на первый элемент
    private ObjectBox head;
    // Указатель на последний элемент
    private ObjectBox tail;
    // Поле для хранения размера очереди
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
    
    public void push(Object obj) { // добавление элемента
        // Сразу создаем вспомогательный объект и помещаем новый элемент в него
        ObjectBox ob = new ObjectBox();
        ob.setObject(obj);
        // Если очередь пустая - в ней еще нет элементов
        if (head == null) {
            // Теперь наша голова указывает на наш первый элемент
            head = ob;
        } else {
            // Если это не первый элемент, то надо, чтобы последний элемент в очереди
            // указывал на вновь прибывший элемент
            tail.setNext(ob);
        }
        // И в любом случае нам надо наш "хвост" переместить на новый элемент
        // Если это первый элемент, то "голова" и "хвост" будут указывать на один и тот же элемент
        tail = ob;
        // Увеличиваем размер нашей очереди
        size++;
    }
 
   
    public Object get(int index) {
        // Если нет элементов или индекс больше размера или индекс меньше 0
        if(size == 0 || index >= size || index < 0) {
            return null;
        }
        // Устанавлваем указатель, который будем перемещать на "голову"
        ObjectBox current = head;
        // В этом случае позиция равну 0
        int pos = 0;
        // Пока позиция не достигла нужного индекса
        while(pos < index) {
            // Перемещаемся на следующий элемент
            current = current.getNext();
            // И увеличиваем позицию
            pos++;
        }
        // Мы дошли до нужной позиции и теперь можем вернуть элемент
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
        return (size == 10); // я подумала, что возьму за основу классический LinkedList, а там по умолчанию 10 эл-тов с возможностью динамического расширения
        //я хз как иначе проверить полная ли очередь, тк это динамическая структура данных
    }
    
    // Наш вспомогательный класс будет закрыт от посторонних глаз, для хранения элементов очереди 
    private class ObjectBox
    {
        // Поле для хранения объекта
        private Object object; // Object подходит для хранения любых типов данных, тк он является суперклассом для всех типов данных
        // Поле для указания на следующий элемент в цепочке.
        // Если оно равно NULL - значит это последний элемент
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
