
Parking lot classes#
```java
// Enumeration

enum PaymentStatus {

COMPLETED,

FAILED,

PENDING,

UNPAID,

REFUNDED

}

  

enum AccountStatus {

ACTIVE,

CLOSED,

CANCELED,

BLACKLISTED,

NONE

}

  

// Custom Person data type class

public class Person {

private String name;

private String address;

private String phone;

private String email;

}

  

// Custom Address data type class

public class Address {

private int zipCode;

private String address;

private String city;

private String state;

private String country;

}
```


Parking spots#

```java
// ParkingSpot is an abstract class

public abstract class ParkingSpot {

private int id;

private boolean isFree;

private Vehicle vehicle;

  

public boolean getIsFree();

public abstract boolean assignVehicle(Vehicle vehicle);

public boolean removeVehicle(){

// definition

}

}

  

public class Handicapped extends ParkingSpot {

public boolean assignVehicle(Vehicle vehicle) {

// definition

}

}

  

public class Compact extends ParkingSpot {

public boolean assignVehicle(Vehicle vehicle) {

// definition

}

}

  

public class Large extends ParkingSpot {

public boolean assignVehicle(Vehicle vehicle) {

// definition

}

}

  

public class Motorcycle extends ParkingSpot {

public boolean assignVehicle(Vehicle vehicle) {

// definition

}

}
```


Vehicle

```java
// Vehicle is an abstract class

public abstract class Vehicle {

private int licenseNo;

public abstract void assignTicket(ParkingTicket ticket);

}

  

public class Car extends Vehicle {

public void assignTicket(ParkingTicket ticket) {

// definition

}

}

  

public class Van extends Vehicle {

public void assignTicket(ParkingTicket ticket) {

// definition

}

}

  

public class Truck extends Vehicle {

public void assignTicket(ParkingTicket ticket) {

// definition

}

}

  

public class MotorCycle extends Vehicle {

public void assignTicket(ParkingTicket ticket) {

// definition

}

}
```

Account#

```java
public abstract class Account {

// Data members

private String userName;

private String password;

private Person person; // Refers to an instance of the Person class

private AccountStatus status; // Refers to the AccountStatus enum

  

public abstract boolean resetPassword();

}

  

public class Admin extends Account {

// spot here refers to an instance of the ParkingSpot class

public boolean addParkingSpot(ParkingSpot spot);

// displayBoard here refers to an instance of the DisplayBoard class

public boolean addDisplayBoard(DisplayBoard displayBoard);

// entrance here refers to an instance of the Entrance class

public boolean addEntrance(Entrance entrance);

// exit here refers to an instance of the Exit class

public boolean addExit(Exit exit);

  

// Will implement the functionality in this class

public boolean resetPassword() {

// definition

}

}

  

public class ParkingAttendant extends Account {

public boolean processTicket(String ticketNumber);

  

// Will implement the functionality in this class

public boolean resetPassword() {

// definition

}

}
```

Display board and parking rate#


```java
public class DisplayBoard {

// Data members

private int id;

private Map<String, List<ParkingSpot>> parkingSpots;

  

// Constructor

public DisplayBoard(int id) {

this.id = id;

this.parkingSpots = new HashMap<>();

}

// Member function

public void addParkingSpot(String spotType, List<ParkingSpot> spots);

public void showFreeSlot();

}

  

public class ParkingRate {

// Data members

private double hours;

private double rate;

  

// Member function

public void calculate();

}
```

Entrance and exit#

```java
public class Entrance {

// Data members

private int id;

  

// Member function

public ParkingTicket getTicket();

}

  

public class Exit {

// Data members

private int id;

  

// Member function

public void validateTicket(ParkingTicket ticket){

// Perform validation logic for the parking ticket

// Calculate parking charges, if necessary

// Handle the exit process

}

}
```

Parking ticket#

```java
public class ParkingTicket {

private int ticketNo;

private Date timestamp;

private Date exit;

private double amount;

private boolean status;

  

// Following are the instances of their respective classes

private Vehicle vehicle;

private Payment payment;

private Entrance entrance;

private Exit exitIns;

}
```

Payment

```java
// Payment is an abstract class

public abstract class Payment {

private double amount;

private PaymentStatus status;

private Date timestamp;

  

public abstract boolean initiateTransaction();

}

  

public class Cash extends Payment {

public boolean initiateTransaction() {

// definition

}

}

  

public class CreditCard extends Payment {

public boolean initiateTransaction() {

// definition

}

}


```


Parking lot#

```java
public class ParkingLot {

private int id;

private String name;

private String address;

private ParkingRate parkingRate;

  

private HashMap<String, Entrance> entrance;

private HashMap<String, Exit> exit;

  

// Create a hashmap that identifies all currently generated tickets using their ticket number

private HashMap<String, ParkingTicket> tickets;

  

// The ParkingLot is a singleton class that ensures it will have only one active instance at a time

// Both the Entrance and Exit classes use this class to create and close parking tickets

private static ParkingLot parkingLot = null;

  

// Created a private constructor to add a restriction (due to Singleton)

private ParkingLot() {

// Call the name, address and parking_rate

// Create initial entrance and exit hashmaps respectively

}

  

// Created a static method to access the singleton instance of ParkingLot

public static ParkingLot getInstance() {

if (parkingLot == null) {

parkingLot = new ParkingLot();

}

return parkingLot;

}

  

public boolean addEntrance(Entrance entrance){}

public boolean addExit(Exit exit){}

  

// This function allows parking tickets to be available at multiple entrances

public ParkingTicket getParkingTicket(Vehicle vehicle) {}

  

public boolean isFull(ParkingSpot type){}

}
```