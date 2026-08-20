# JavaFX Shape Examples

## Square

```java
import javax.swing.*;
import java.awt.*;

public class square2 extends JPanel {
    protected void paintComponent(Graphics g) {
        g.drawRect(125, 125, 150, 150);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("square2");
        frame.setSize(400, 400);
        frame.add(new square2());
        frame.setVisible(true);
    }
}
```

## Rectangle

```java
import javax.swing.*;
import java.awt.*;

public class rectangle2 extends JPanel {
    protected void paintComponent(Graphics g) {
        g.drawRect(100, 150, 200, 100);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("rectangle2");
        frame.setSize(400, 400);
        frame.add(new rectangle2());
        frame.setVisible(true);
    }
}
```
