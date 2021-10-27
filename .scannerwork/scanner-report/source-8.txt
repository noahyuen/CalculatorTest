package com.example.demo;

import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.fxml.FXMLLoader;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.layout.HBox;
import javafx.scene.layout.Priority;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {

    String currentArg1 = null;
    String currentArg2 = null;
    String currentOperand = null;
    boolean startNewEquation = true;
    public static final String divError = "Div By Zero Error";

    @Override
    public void start(Stage stage) throws IOException {
        stage.setTitle("Calculator");
        // create VBox (temporary)
        VBox root = new VBox();
        // set scene
        Scene scene = new Scene(root, 200, 170);
        stage.setScene(scene);
        stage.setResizable(false);
        // create currentDisplay label
        Label currentDisplay = new Label("Start Calculating");
        currentDisplay.setPrefWidth(200);
        currentDisplay.setPrefHeight(40);
        // inset: top, right, bottom, left
        currentDisplay.setPadding(new Insets(0, 0, 0, 5));
        // create buttons
        Button button0 = new Button("0");
        Button button1 = new Button("1");
        Button button2 = new Button("2");
        Button button3 = new Button("3");
        Button button4 = new Button("4");
        Button button5 = new Button("5");
        Button button6 = new Button("6");
        Button button7 = new Button("7");
        Button button8 = new Button("8");
        Button button9 = new Button("9");
        Button buttonDecimal = new Button(".");
        Button buttonClear = new Button("AC");
        Button buttonNegative = new Button("+/-");
        Button buttonModulo = new Button("%");
        Button buttonDivide = new Button("/");
        Button buttonMultiply = new Button("X");
        Button buttonSubtract = new Button("-");
        Button buttonAdd = new Button("+");
        Button buttonEquals = new Button("=");

        // set button widths
        button0.setPrefWidth(50);
        button1.setPrefWidth(50);
        button2.setPrefWidth(50);
        button3.setPrefWidth(50);
        button4.setPrefWidth(50);
        button5.setPrefWidth(50);
        button6.setPrefWidth(50);
        button7.setPrefWidth(50);
        button8.setPrefWidth(50);
        button9.setPrefWidth(50);
        buttonDecimal.setPrefWidth(50);
        buttonClear.setPrefWidth(50);
        buttonNegative.setPrefWidth(50);
        buttonModulo.setPrefWidth(50);
        buttonDivide.setPrefWidth(50);
        buttonMultiply.setPrefWidth(50);
        buttonSubtract.setPrefWidth(50);
        buttonAdd.setPrefWidth(50);
        buttonEquals.setPrefWidth(50);

        // create HBoxes
        HBox row1 = new HBox();
        HBox row2 = new HBox();
        HBox row3 = new HBox();
        HBox row4 = new HBox();
        HBox row5 = new HBox();

        // set HBox children
        row1.getChildren().addAll(buttonClear, buttonNegative, buttonModulo, buttonDivide);
        row2.getChildren().addAll(button7, button8, button9, buttonMultiply);
        row3.getChildren().addAll(button4, button5, button6, buttonSubtract);
        row4.getChildren().addAll(button1, button2, button3, buttonAdd);
        row5.getChildren().addAll(button0, buttonDecimal, buttonEquals);
        // set VBox children
        root.getChildren().addAll(currentDisplay, row1, row2, row3, row4, row5);

        // set functionality for clear button
        buttonClear.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                currentDisplay.setText("Start Calculating");
                // reset arguments and current operand
                currentArg1 = null;
                currentOperand = null;
                currentArg2 = null;
            }
        });

        // set functionality for operands
        buttonAdd.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // if all args and operands are valid, compute equation
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        startNewEquation = true;
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }
                // if no operand is None, set current Operand
                if (currentOperand == null && currentArg1 != null) {
                    startNewEquation = false;
                    currentOperand = "+";
                    currentDisplay.setText(currentDisplay.getText() + "+");
                }
            }
        });

        buttonSubtract.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // if all args and operands are valid, compute equation
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        startNewEquation = true;
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }
                // if no operand is None, set current Operand
                if (currentOperand == null && currentArg1 != null) {
                    startNewEquation = false;
                    currentOperand = "-";
                    currentDisplay.setText(currentDisplay.getText() + "-");
                }
            }
        });

        buttonDivide.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // if all args and operands are valid, compute equation
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        startNewEquation = true;
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }
                // if no operand is None, set current Operand
                if (currentOperand == null && currentArg1 != null) {
                    startNewEquation = false;
                    currentOperand = "/";
                    currentDisplay.setText(currentDisplay.getText() + "/");
                }
            }
        });

        buttonMultiply.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // if all args and operands are valid, compute equation
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        startNewEquation = true;
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }
                // if no operand is None, set current Operand
                if (currentOperand == null && currentArg1 != null) {
                    startNewEquation = false;
                    currentOperand = "X";
                    currentDisplay.setText(currentDisplay.getText() + "X");
                }
            }
        });

        buttonModulo.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // if all args and operands are valid, compute equation
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        startNewEquation = true;
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }
                // if no operand is None, set current Operand
                if (currentOperand == null && currentArg1 != null) {
                    startNewEquation = false;
                    currentOperand = "%";
                    currentDisplay.setText(currentDisplay.getText() + "%");
                }
            }
        });

        // set functionality for equals button
        buttonEquals.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // set StartNewEquation to True
                startNewEquation = true;
                // check if arg1, operand and arg2 are present
                if (currentArg1 != null && currentOperand != null && currentArg2 != null) {
                    double answer = calculate(currentArg1, currentOperand, currentArg2);
                    if (answer == Double.POSITIVE_INFINITY) {
                        currentDisplay.setText(divError);
                        currentArg1 = null;
                        currentOperand = null;
                        currentArg2 = null;
                    } else {
                        currentDisplay.setText(Double.toString(answer));
                        currentArg1 = Double.toString(answer);
                        currentOperand = null;
                        currentArg2 = null;
                    }
                }

            }
        });

        // set functionality for number buttons
        button0.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "0";
                    currentDisplay.setText("0");
                } else if (currentOperand == null) {
                    currentArg1 += "0";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "0";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "0";
                    currentDisplay.setText(currentDisplay.getText() + "0");
                }
            }
        });

        button1.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "1";
                    currentDisplay.setText("1");
                } else if (currentOperand == null) {
                    currentArg1 += "1";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "1";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "1";
                    currentDisplay.setText(currentDisplay.getText() + "1");
                }
            }
        });

        button2.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "2";
                    currentDisplay.setText("2");
                } else if (currentOperand == null) {
                    currentArg1 += "2";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "2";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "2";
                    currentDisplay.setText(currentDisplay.getText() + "2");
                }
            }
        });

        button3.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "3";
                    currentDisplay.setText("3");
                } else if (currentOperand == null) {
                    currentArg1 += "3";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "3";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "3";
                    currentDisplay.setText(currentDisplay.getText() + "3");
                }
            }
        });

        button4.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "4";
                    currentDisplay.setText("4");
                } else if (currentOperand == null) {
                    currentArg1 += "4";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "4";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "4";
                    currentDisplay.setText(currentDisplay.getText() + "4");
                }
            }
        });

        button5.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "5";
                    currentDisplay.setText("5");
                } else if (currentOperand == null) {
                    currentArg1 += "5";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "5";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "5";
                    currentDisplay.setText(currentDisplay.getText() + "5");
                }
            }
        });

        button6.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "6";
                    currentDisplay.setText("6");
                } else if (currentOperand == null) {
                    currentArg1 += "6";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "6";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "6";
                    currentDisplay.setText(currentDisplay.getText() + "6");
                }
            }
        });

        button7.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "7";
                    currentDisplay.setText("7");
                } else if (currentOperand == null) {
                    currentArg1 += "7";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "7";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "7";
                    currentDisplay.setText(currentDisplay.getText() + "7");
                }
            }
        });

        button8.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "8";
                    currentDisplay.setText("8");
                } else if (currentOperand == null) {
                    currentArg1 += "8";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "8";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "8";
                    currentDisplay.setText(currentDisplay.getText() + "8");
                }
            }
        });

        button9.setOnAction(new EventHandler<ActionEvent>() {
            public void handle(ActionEvent actionEvent) {
                // check if StartNewEquation is True
                if (startNewEquation) {
                    startNewEquation = false;
                    currentArg1 = "9";
                    currentDisplay.setText("9");
                } else if (currentOperand == null) {
                    currentArg1 += "9";
                    currentDisplay.setText(currentArg1);
                } else if (currentArg2 == null) {
                    currentArg2 = "9";
                    currentDisplay.setText(currentDisplay.getText() + currentArg2);
                } else {
                    currentArg2 += "9";
                    currentDisplay.setText(currentDisplay.getText() + "9");
                }
            }
        });

        // show stage
        stage.show();
    }

    private static double calculate(String arg1, String operand, String arg2) {
        double argument1 = Double.parseDouble(arg1);
        double argument2 = Double.parseDouble(arg2);
        if (operand.equals("+")) {
            // addition
            return argument1 + argument2;
        } else if (operand.equals("-")) {
            // subtraction
            return argument1 - argument2;
        } else if (operand.equals("X")) {
            // multiplication
            return argument1 * argument2;
        } else if (operand.equals("/")) {
            // division
            if (argument2 == 0) {
                return Double.POSITIVE_INFINITY;
            } return argument1 / argument2;
        } else {
            // modulo divide
            if (argument2 == 0) {
                return Double.POSITIVE_INFINITY;
            } return argument1 % argument2;
        }

    }

    public static void main(String[] args) {
        launch();
    }
}