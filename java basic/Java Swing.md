1 Use invokeLater() to enqueue the UI update operations to EDT(event dispatching thread) --Schedule a job for the event-dispatching thread: creating and showing this application's GUI.(For thread safety, this method should be invoked from the event-dispatching thread)

2 Create a new thread to process image

3 After image processed use invokeLater() again to enqueue the UI update operations to EDT
```
package components;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

/* TopLevelDemo.java requires no other files. */
public class TopLevelDemo {
    /**
     * Create the GUI and show it.  For thread safety,
     * this method should be invoked from the
     * event-dispatching thread.
     */
    private static void createAndShowGUI() {
        //Create and set up the window.
        JFrame frame = new JFrame("TopLevelDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //Create the menu bar.  Make it have a green background.
        JMenuBar greenMenuBar = new JMenuBar();
        greenMenuBar.setOpaque(true);
        greenMenuBar.setBackground(new Color(154, 165, 127));
        greenMenuBar.setPreferredSize(new Dimension(200, 20));

        //Create a yellow label to put in the content pane.
        JLabel yellowLabel = new JLabel();
        yellowLabel.setOpaque(true);
        yellowLabel.setBackground(new Color(248, 213, 131));
        yellowLabel.setPreferredSize(new Dimension(200, 180));

        //Set the menu bar and add the label to the content pane.
        frame.setJMenuBar(greenMenuBar);
        frame.getContentPane().add(yellowLabel, BorderLayout.CENTER);

        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        //Schedule a job for the event-dispatching thread:
        //creating and showing this application's GUI.
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }
        });
    }
}
```
>Although Swing's model architecture is sometimes referred to as a Model-View-Controller (MVC) design, it really **isn't. **Swing components are generally implemented so that the **view and controller are indivisible**, implemented by a single UI object provided by the look and feel. The Swing model architecture is more accurately described as a **separable model architecture**. If you're interested in learning more about the Swing model architecture, see [A Swing Architecture Overview](http://www.oracle.com/technetwork/java/architecture-142923.html), an article in *The Swing Connection*.
see my github project [seam carver](https://github.com/HoweZZH/SeamCarving).

**References:**
https://docs.oracle.com/javase/tutorial/uiswing/examples/components/TopLevelDemoProject/src/components/TopLevelDemo.java
