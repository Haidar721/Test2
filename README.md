# Billing System

## Overview

The Order Management System is a Java-based application designed for managing and tracking customer orders in a user-friendly interface. 
## System Architecture

The system follows a layered architecture consisting of three main components:

1. **User Interface (UI)**: The front-end layer that interacts with users, allowing them to input and manage orders.
2. **Business Logic**: This layer contains the core functionalities of the system, managing order creation, deletion, and retrieval.
3. **Data Model**: This includes classes that represent the order data and define the properties and behaviors of the orders.

## Core Components and Modules

### 1. Main Class

- **`Main`**
  - Responsible for launching the application and setting up the main stage.
  - **Method**: `start(Stage primaryStage)`
    ```java
    @Override
    public void start(Stage primaryStage) {
        // Code to set up the primary stage and scene
        primaryStage.setTitle("Order Management System");
        primaryStage.show();
    }
    ```

### 2. Order Class

- **`Order`**
  - Represents an order with attributes such as name, price, quantity, date, and comments.
  - **Constructor**:
    ```java
    public Order(String name, double price, int quantity, Date date, String comment) {
        this.name = name;
        this.price = price;
        this.quantity = quantity;
        this.date = date;
        this.comment = comment;
    }
    ```
  - **Getters**:
    ```java
    public String getName() { return name; }
    public double getPrice() { return price; }
    public int getQnty() { return quantity; }
    public Date getDate() { return date; }
    public String getComment() { return comment; }
    ```

### 3. OrderManager Class

- **`OrderManager`**
  - Handles the addition, removal, and retrieval of orders.
  - **Methods**:
    - `addOrder(Order order)`: Adds a new order to the list.
    - `removeOrder(Order order)`: Removes an existing order from the list.
    - `getOrders()`: Returns a list of all orders.
    ```java
    public void addOrder(Order order) {
        ordersList.add(order);
    }

    public void removeOrder(Order order) {
        ordersList.remove(order);
    }

    public ArrayList<Order> getOrders() {
        return ordersList;
    }
    ```

### 4. UI Class

- **`UI`**
  - Manages the graphical components and interactions.
  - **Method**: `refreshOrders(GridPane innergrid, ArrayList<Order> ordersList, String[] labels, Label amount)`
    - Updates the displayed order list in the UI grid.
    ```java
    private void refreshOrders(GridPane innergrid, ArrayList<Order> ordersList, String[] labels, Label amount) {
        innergrid.getChildren().clear();
        // Code to populate grid with order details
    }
    ```

### 5. Event Handlers

- **Delete Order Functionality**
  - Allows users to delete an order after confirming through a dialog.
  - **Snippet**:
    ```java
    deleteOrder.setOnAction(new EventHandler<ActionEvent>() {
        @Override
        public void handle(ActionEvent avt) {
            // Confirmation alert code
        }
    });
    ```

## Code Snippets and Examples

### Adding an Order

To add an order, create an instance of the `Order` class and use the `OrderManager` to add it:

```java
Order newOrder = new Order("Pizza", 12.99, 2, new Date(), "Extra cheese");
orderManager.addOrder(newOrder);
```

### Viewing Orders
Orders are displayed in the user interface within a grid layout. Each order shows the following details:

#### Name: The name of the item ordered.
#### Price: The price of the item.
#### Quantity: The number of items ordered.
#### Total: The total cost (price multiplied by quantity).
#### Comment: Any additional comments related to the order.

### Deleting an Order
To delete an order, the user can click the "Delete Order" button next to the respective order in the UI. This action prompts a confirmation dialog. If the user confirms, the order will be removed from the list:
``` java
deleteOrder.setOnAction(new EventHandler<ActionEvent>() {
    @Override
    public void handle(ActionEvent avt) {
        Alert alert = new Alert(AlertType.CONFIRMATION);
        alert.setTitle("Confirm Order Deletion");
        alert.setHeaderText("Confirm Order Deletion");
        alert.setContentText("Are you sure you want to delete this order?");

        Optional<ButtonType> result = alert.showAndWait();
        if (result.get() == ButtonType.OK) {
            // Code to remove the order
        }
    }
});
```
## License
This project is licensed under the MIT License.
© 2017-2024 All rights reserved. Projectworlds LLP
