

```java
// Enumerations

enum ProductType {

CHOCOLATE,

SNACK,

BEVERAGE,

OTHER

}
```

state 
```java
// State is an interface

public interface State {

// Interface method (does not have a body)

public void insertMoney(VendingMachine machine, double amount);

public void pressButton(VendingMachine machine, int rackNumber);

public void returnChange(double amount);

public void updateInventory(VendingMachine machine, int rackNumber);

public void dispenseProduct(VendingMachine machine, int rackNumber);

}

public class NoMoneyInsertedState implements State {

@override

public void insertMoney(VendingMachine machine, double amount) {

// changes state to MonenInsertedState

}

public void pressButton(VendingMachine machine, int rackNumber) {}

public void returnChange(double amount) {}

public void updateInventory(VendingMachine machine, int rackNumber) {}

public void dispenseProduct(VendingMachine machine, int rackNumber) {}

}

  

public class MoneyInsertedState implements State {

@override

public void insertMoney(VendingMachine machine, double amount) {}

public void pressButton(VendingMachine machine, int rackNumber) {

// check if product item is available

// validate money

// change state to DispenseState

}

public void returnChange(double amount) {}

public void updateInventory(VendingMachine machine, int rackNumber) {}

public void dispenseProduct(VendingMachine machine, int rackNumber) {}

}

  

public class DispenseState implements State {

@override

public void insertMoney(VendingMachine machine, double amount) {}

public void pressButton(VendingMachine machine, int rackNumber) {}

public void returnChange(double amount){}

public void updateInventory(VendingMachine machine, int rackNumber) {}

public void dispenseProduct(VendingMachine machine, int rackNumber) {

// dispense product

// change state to NoMoneyInsertedState

}

}
```

Product, rack and inventory#

```java
public class Product {

private String name;

private int id;

private double price;

private ProductType type;

}

  

public class Rack {

private int productId;

private int rackNumber;

public boolean isEmpty();

}

  

public class Inventory {

private int noOfProducts;

private List<Product> products;

  

public void addProduct(int productId, int rackId);

public void removeProduct(int productId, int rackId);

}
```


Vending machine#

```java
public class VendingMachine {

private State currentState;

private double amount;

private int noOfRacks;

private List<Rack> racks;

private List<int> availableRacks;

  

// The VendingMachine is a Singleton class that ensures it will have only one active instance at a time

private static VendingMachine vendingMachine = null;

  

// Created a private constructor to add a restriction (due to Singleton)

private VendingMachine();

  

// Created a static method to access the singleton instance of VendingMachine

public static VendingMachine getInstance() {

if (vendingMachine == null) {

vendingMachine = new VendingMachine();

}

return vendingMachine;

}

  

public void insertMoney(double amount) {}

public void pressButton(int rackNumber) {}

public void returnChange(double amount) {}

public void updateInventory(int rackNumber) {}

public void dispenseProduct(int rackNumber) {}

public int getProductIdAtRack(int rackNumber) {}

}
```

