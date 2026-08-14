# JavaFX Shape Examples

## Square

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.layout.StackPane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Rectangle;
import javafx.stage.Stage;
public class square extends Application {
    @Override
    public void start(Stage primaryStage) {
        Rectangle square = new Rectangle(150, 150);
        square.setFill(Color.TRANSPARENT);
        square.setStroke(Color.DARKBLUE);
        square.setStrokeWidth(3);
        StackPane root = new StackPane(square);
        Scene scene = new Scene(root, 400, 400);
        primaryStage.setTitle("Square");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```

## Rectangle

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.layout.StackPane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Rectangle;
import javafx.stage.Stage;
public class rectangle extends Application {
    @Override
    public void start(Stage primaryStage) {
        Rectangle rectangle = new Rectangle(150, 50);
        rectangle.setFill(Color.TRANSPARENT);
        rectangle.setStroke(Color.DARKBLUE);
        rectangle.setStrokeWidth(3);
        StackPane root = new StackPane(rectangle);
        Scene scene = new Scene(root, 400, 400);
        primaryStage.setTitle("Square");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```
