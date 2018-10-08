
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
