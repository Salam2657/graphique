package salam;
import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class LTEAdvancedGUI extends Application {

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("LTE-Advanced Network Configuration");

        // Creating components
        Label title = new Label("LTE-Advanced Network Configuration");
        title.setStyle("-fx-font-size: 18px; -fx-font-weight: bold;");

        ImageView imageView = new ImageView(new Image("file:C:\\Users\\HP\\OneDrive\\Documents\\NetBeansProjects\\LTE\\src\\salam\\unnamed.png"));
        imageView.setFitHeight(100);
        imageView.setFitWidth(100);

        Label bandwidthLabel = new Label("Bande Passante (MHz):");
        TextField bandwidthField = new TextField();
        Label latenceLabel = new Label(" Latence (ms):");
        TextField latenceField = new TextField();
        Label usersLabel = new Label("Nombre d'Utilisateurs:");
        TextField usersField = new TextField();

        Label coverageLabel = new Label("Couverture Géographique (km²):");
        TextField coverageField = new TextField();

        Label capacityLabel = new Label("Capacité (Gbps):");
        TextField capacityField = new TextField();

        Label modulationCodingLabel = new Label("Modulation-Codage:");
        ComboBox<String> modulationCodingComboBox = new ComboBox<>();
        modulationCodingComboBox.getItems().addAll("QPSK", "16QAM", "64QAM");

        Label mimoLabel = new Label("Antennes - MIMO:");
        ComboBox<String> mimoComboBox = new ComboBox<>();
        mimoComboBox.getItems().addAll("2x2", "4x4", "8x8");

        Label qosLabel = new Label("Qualité de Service (QoS):");
        TextField qosField = new TextField();

        Button saveButton = new Button("Valider");

        // GridPane for layout
        GridPane grid = new GridPane();
        grid.setPadding(new Insets(20, 20, 20, 20));
        grid.setVgap(10);
        grid.setHgap(10);
        grid.setAlignment(Pos.CENTER);
        grid.setStyle("-fx-background-color: lightblue;");

        grid.add(title, 0, 0, 2, 1);
        grid.add(imageView, 0, 1, 2, 1);
        grid.add(bandwidthLabel, 0, 2);
        grid.add(bandwidthField, 1, 2);
        grid.add(latenceLabel, 0, 9);
        grid.add(latenceField, 1, 9);
        grid.add(usersLabel, 0, 3);
        grid.add(usersField, 1, 3);
        grid.add(coverageLabel, 0, 4);
        grid.add(coverageField, 1, 4);
        grid.add(capacityLabel, 0, 5);
        grid.add(capacityField, 1, 5);
        grid.add(modulationCodingLabel, 0, 6);
        grid.add(modulationCodingComboBox, 1, 6);
        grid.add(mimoLabel, 0, 7);
        grid.add(mimoComboBox, 1, 7);
        grid.add(qosLabel, 0, 8);
        grid.add(qosField, 1, 8);
        grid.add(saveButton, 1, 10);

        // Creating the scene and setting it to the stage
        Scene scene = new Scene(grid, 500, 600);
        primaryStage.setScene(scene);
        primaryStage.show();

        // Event handling for the save button
        saveButton.setOnAction(e -> {
            String bandwidth = bandwidthField.getText();
            String latence = latenceField.getText();
            String users = usersField.getText();
            String coverage = coverageField.getText();
            String capacity = capacityField.getText();
            String modulationCoding = modulationCodingComboBox.getValue();
            String mimo = mimoComboBox.getValue();
            String qos = qosField.getText();

            System.out.println("Configuration sauvegardée:");
            System.out.println("Bande Passante: " + bandwidth + " MHz");
            System.out.println("Nombre d'Utilisateurs: " + users);
            System.out.println("Couverture Géographique: " + coverage + " km²");
            System.out.println("Capacité: " + capacity + " Gbps");
            System.out.println("Modulation-Codage: " + modulationCoding);
            System.out.println("Antennes - MIMO: " + mimo);
            System.out.println("Qualité de Service: " + qos);
            System.out.println("Latence: " + latence + " ms");
        });
    }

    public static void main(String[] args) {
        launch(LTEAdvancedGUI.class, args);
    }
}

