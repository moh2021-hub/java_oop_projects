

Enumerations#

```java
// definition of enumerations used in elevator system

enum ElevatorState {

IDLE,

UP,

DOWN

}

  

enum Direction {

UP,

DOWN

}

  

enum DoorState {

OPEN,

CLOSE

}
```

Button
```java
public abstract class Button {

private boolean status;

  

public pressDown();

public abstract boolean isPressed();

}

  

public class DoorButton extends Button {

  

public boolean isPressed() {

// Definition

}

}

  

public class HallButton extends Button {

private Direction buttonSign;

  

public boolean isPressed() {

// definition

}

}

  

public class ElevatorButton extends Button {

private int destinationFloorNumber;

  

public boolean isPressed() {

// definition

}

}
```

Elevator panel and hall panel #

```java
public class ElevatorPanel {

private List<ElevatorButton> floorButtons;

private DoorButton openButton;

private DoorButton closeButton;

}

  

public class HallPanel {

private HallButton up;

private HallButton down;

}
```

Display
```java
public class Display {

private int floor;

private int capacity;

private Direction direction;

  

public void showElevatorDisplay();

public void showHallDisplay();

}
```


Elevator car #

```java
public class ElevatorCar {

private int id;

private Door door;

private ElevatorState state;

private Display display;

private ElevatorPanel panel;

  

public void move();

public void stop();

public void openDoor();

public void closeDoor();

}
```

Door and floor 

```java
public class Door {

private DoorState state;

public boolean isOpen();

}

  

public class Floor {

private List<Display> display;

private List<HallPanel> panel;

public boolean isBottomMost();

public boolean isTopMost();

}



```

Elevator system and building #

```java
public class ElevatorSystem {

private Building building;

public void monitoring();

public void dispatcher();

  

// Private constructor to prevent direct instantiation

private ElevatorSystem() {

// Initialize the ElevatorSystem

}

// The ElevarSystem is a singleton class that ensures it will have only one active instance at a time

private static ElevatorSystem system = null;

// Created a static method to access the singleton instance of ElevatorSytem class

public static ElevatorSystem getInstance() {

if (system == null) {

system = new ElevatorSystem();

}

return system;

}

}

  

public class Building {

private List<Floor> floor;

private List<ElevatorCar> elevator;

  

private static Building building = null;

public static Building getInstance() {

if (building == null) {

building = new Building();

}

return building;

}

}
```

