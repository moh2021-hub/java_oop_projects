
```java
// definition of enumerations used in the Amazon Locker service

public enum LockerSize {

EXTRA_SMALL,

SMALL,

MEDIUM,

LARGE,

EXTRA_LARGE,

DOUBLE_EXTRA_LARGE

}

public enum LockerState {

CLOSED,

BOOKED,

AVAILABLE

}
```


Item and Order#

```java
public class Item {

private String itemId;

private int quantity;

}

  

public class Order {

private String orderId;

private List<Item> items;

private String deliveryLocation;

}
```


Package and LockerPackage#

```java
public class Package {

private String packageId;

private double packageSize;

private Order order;

  

public void pack();

}

  

public class LockerPackage extends Package {

private int codeValidDays;

private String lockerId;

private String packageId;

private String code;

private Date packageDeliveryTime;

  

public boolean isValidCode();

public boolean verifyCode(String code);

}

```


Locker and LockerLocation#

```java
public class Locker {

private String lockerId;

private LockerSize lockerSize;

private String locationId;

private LockerState lockerState;

  

public boolean addPackage();

public boolean removePackage();

}

  

public class LockerLocation {

private String name;

private List<Locker> lockers;

private double longitude;

private double latitude;

private Date openTime;

private Date closeTime;

}
```


LockerService and Notification#

```java
public class LockerService {

private List<LockerLocation> locations;

  

// The LockerService is a Singleton class that ensures it will have only one active instance at a time

private static LockerService lockerService = null;

// Created a static method to access the Singleton instance of LockerService class

public static LockerService getInstance() {

if (lockerService == null) {

lockerService = new LockerService();

}

return lockerService;

}

}

  

public class Notification {

private String customerId;

private String orderId;

private String lockerId;

private String code;

  

public void send();

}



```

