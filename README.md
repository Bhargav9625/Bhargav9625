import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.*;
import javafx.stage.Stage;

public class Main extends Application {

    private RadioButton eatInRadio, takeawayRadio, deliveryRadio;
    private TextArea menuTextArea;
    private Button confirmButton;

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Order");

        // Order type selection
        ToggleGroup orderTypeGroup = new ToggleGroup();
        eatInRadio = new RadioButton("Eat In");
        eatInRadio.setToggleGroup(orderTypeGroup);
        takeawayRadio = new RadioButton("Takeaway");
        takeawayRadio.setToggleGroup(orderTypeGroup);
        deliveryRadio = new RadioButton("Delivery");
        deliveryRadio.setToggleGroup(orderTypeGroup);

        VBox orderTypeBox = new VBox(10, eatInRadio, takeawayRadio, deliveryRadio);
        orderTypeBox.setPadding(new Insets(10));
        orderTypeBox.setBorder(new Border(new BorderStroke(null, BorderStrokeStyle.SOLID, null, new BorderWidths(1))));

        // Menu display
        menuTextArea = new TextArea();
        menuTextArea.setEditable(false);
        menuTextArea.setPrefHeight(200);
        menuTextArea.setText("Menu:\n1. Pizza - $10\n2. Burger - $8\n3. Salad - $6");

        // Confirmation button
        confirmButton = new Button("Confirm Order");
        confirmButton.setOnAction(e -> confirmOrder());

        VBox layout = new VBox(10, orderTypeBox, menuTextArea, confirmButton);
        layout.setPadding(new Insets(10));

        primaryStage.setScene(new Scene(layout, 300, 300));
        primaryStage.show();
    }

    private void confirmOrder() {
        if (eatInRadio.isSelected()) {
            System.out.println("Order type: Eat In");
        } else if (takeawayRadio.isSelected()) {
            System.out.println("Order type: Takeaway");
        } else if (deliveryRadio.isSelected()) {
            System.out.println("Order type: Delivery");
        } else {
            System.out.println("Please select an order type.");
        }
    }

    public static void main(String[] args) {
        launch(args);
    }
}
