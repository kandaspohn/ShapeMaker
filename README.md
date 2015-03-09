# ShapeMaker
Shape Maker Lab for Java I
//this is my first attempt at using GitHub
//I am new to programming in java (or any program) so bear with my lack of understanding

//So I need to add stuff to this program, but I'm a little stuck
//Here are some things I need to add:
/*•	Add in switches for choosing and setting colors for the pen and fill.  These colors should be passed to the object to be drawn as we did with pre-set colors.
•	Add at least two more shapes to the menu.  Each shape would be added to the original switch for the shape choices.  To add them you must do the following:
o	Create a separate class similar to the Circle class we used.  This class should have all of the functionality that was imbedded in the Circle class.
o	Create the appropriate methods in the ShapeMaker class to gather information from the user and to draw the shape.
*/


//driver class

package circledraw;
import javax.swing.*;
import java.awt.*;


/**
 *
 * @author kevin.spohn.7382
 */
public class CircleDraw {

    
     JFrame mainWindow;
     Container contentPane;
    public static void main(String[] args) {
      
        CircleDraw circle = new CircleDraw();
        circle.start();
        
    }   
     public CircleDraw(){
         mainWindow = new JFrame("Shape Maker");
         mainWindow.setSize(500, 400);
         mainWindow.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
         mainWindow.setVisible(true);
         contentPane = mainWindow.getContentPane();
         contentPane.setBackground(Color.white);
     }
     public void start(){
         int shape;
         //display menu of shapes
         //get user's choice
         //based on choice, call methods to get input about shape
         Circle circle = new Circle();
         getCircleInfo(circle);
         drawCircle(circle);
         
     }
     public void drawCircle(Circle c){
         Graphics graphicsContent = contentPane.getGraphics();
         c.draw(graphicsContent);
     }
     public void getCircleInfo(Circle c){
         double radius = Double.parseDouble(JOptionPane.showInputDialog(mainWindow,
         "Enter the radius of your circle"));
         c.setRadius(radius);
         //display a menu for pen color
         //get user choice
         
         c.setPenColot(Color.red);
         //display menu for fill color
         c.setFillColor(Color.blue);
         int x = Integer.parseInt(JOptionPane.showInputDialog(mainWindow, "Enter upper left x-coordinate"));
         c.setX(x);
         int y = Integer.parseInt(JOptionPane.showInputDialog(mainWindow, "Enter upper left y-coordinate"));
         c.setY(y);
     }
        
        
    }
    
    //Circle Class
    
    package circledraw;
import java.awt.*;
/**
 *
 * @author kevin.spohn.7382
 */
public class Circle {
    
    //data members
    private double dblRadius;
    final public double PI = 3.142;
    private int xcoord, ycoord;
    Color penColor, fillColor;
    
    //constructor
    public Circle(){
    
    }
    public Circle(double radius){
        setRadius(radius);
        penColor = Color.GREEN;
        fillColor = Color.ORANGE;
        //set default locations
        xcoord = 0;
        ycoord = 0;
                
    }
    //other methods
    public double getArea(){
        return PI * dblRadius * dblRadius;
        //return PI * Math.pow(dblRadius, 2);
    }
    
    public double getCircumference(){
        return 2 * PI * dblRadius;
    }
    
    public void setRadius(double rad){
        dblRadius = 0;
        if(rad > 0){
            dblRadius = rad;
        }
    }
    public void setFillColor(Color fill){
        fillColor = fill;
    }
    public void setPenColot(Color pen){
        penColor = pen;
    }
    public void setX(int x){
        xcoord = 0;
        if(x>0){
            xcoord = x;
        }
    }
    public void setY(int y){
        ycoord = 0;
        if (y>0){
            ycoord = y;
        }
    }
    public void draw(Graphics g){
        int width = (int)dblRadius * 2;
        int height = (int)dblRadius * 2;
        
        g.setColor(penColor);
        g.drawOval(xcoord, ycoord, width, height);
        g.setColor(fillColor);
        g.fillOval(xcoord, ycoord, width, height);
        g.dispose();
    }
}
