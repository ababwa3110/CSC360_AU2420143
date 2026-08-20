# JavaFX Shape Examples

## Square

```java
import javax.swing.*;
import java.awt.*;

public class square2 extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.setColor(Color.DARK_GRAY.darker());
        g2d.setStroke(new BasicStroke(3));
        int size = 150;
        int x = (getWidth() - size) / 2;
        int y = (getHeight() - size) / 2;
        g2d.drawRect(x, y, size, size);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("square2");
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setSize(400, 400);
            frame.add(new square2());
            frame.setVisible(true);
        });
    }
}
```

## Rectangle

```java
import javax.swing.*;
import java.awt.*;

public class rectangle2 extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.setColor(Color.DARK_GRAY.darker());
        g2d.setStroke(new BasicStroke(3));
        int width = 200;
        int height = 100;
        int x = (getWidth() - width) / 2;
        int y = (getHeight() - height) / 2;
        g2d.drawRect(x, y, width, height);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new JFrame("rectangle2");
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setSize(400, 400);
            frame.add(new rectangle2());
            frame.setVisible(true);
        });
    }
}
```
