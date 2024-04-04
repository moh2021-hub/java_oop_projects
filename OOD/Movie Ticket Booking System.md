
```java
// Enumerations

enum PaymentStatus {

PENDING,

CONFIRMED,

DECLINED,

REFUNDED

}

  

enum BookingStatus {

PENDING,

CONFIRMED,

CANCELLED,

DENIED,

REFUNDED

}

  

enum SeatStatus {

AVAILABLE,

BOOKED,

RESERVED

}
```

Actors 

```java
// Person is an abstract class

public abstract class Person {

private String name;

private String address;

private String phone;

private String email;

}

  

public class Customer extends Person {

private List<Bookings> bookings; // List of bookings

// booking here refers to an instance of the Booking class

public boolean createBooking(Booking booking);

public boolean updateBooking(Booking booking);

public boolean deleteBooking(Booking booking);

}

  

public class Admin extends Person {

// show here refers to an instance of the ShowTime class

public boolean addShow(Show show);

public boolean updateShow(Show show);

public boolean deleteShow(Show show);

public boolean addMovie(Movie movie);

public boolean deleteMovie(Movie movie);

}

  

public class TicketAgent extends Person {

// booking here refers to an instance of the Booking class

public boolean createBooking(Booking booking);

}```

Seat
```java

// Seat is an abstract class

public abstract class Seat {

// Data members

private String seatNo;

private SeatStatus status; // Refers to the SeatStatus enum

  

// Member functions

public boolean isAvailable();

public abstract void setSeat();

public abstract void setRate();

}

  

public class Platinum extends Seat {

private double rate;

public void setSeat() {

// definition

}

public void setRate() {

// definition

}

}

  

public class Gold extends Seat {

private double rate;

public void setSeat() {

// definition

}

public void setRate() {

// definition

}

}

  

public class Silver extends Seat {

private double rate;

public void setSeat() {

// definition

}

public void setRate() {

// definition

}

}
```

Movie, showtime, and movie ticket
```java

public class Movie {

// Data members

private String title;

private String genre;

private Date releaseDate;

private String language;

private int duration;

private List<ShowTime> shows;

}

  

public class ShowTime {

// Data members

private int showId;

// The Date datatype represents and deals with both date and time

private Date startTime;

private Date date;

private int duration;

private List<Seat> seats;

// Displays the list of available seats

public void showAvailableSeats();

}

  

public class MovieTicket {

// Data members

private int ticketId;

private Seat seat;

private Movie movie;

private ShowTime show;

}
```

City, cinema, and hall #

```java

public class City {

// Data members

private String name;

private String state;

private int zipCode;

private List<Cinema> cinemas;

}

  

public class Cinema {

// Data members

private int cinemaId;

private List<Hall> halls;

private City city;

}

  

public class Hall {

// Data members

private int hallId;

private List<ShowTime> shows;

  

// Returns list of shows

public List<ShowTime> findCurrentShows();

}
```

Payment 

```java
// Payment is an abstract class

public abstract class Payment {

// Data members

private double amount;

  

// The Date datatype represents and deals with both date and time.

private Date timestamp;

private PaymentStatus status;

  

public abstract boolean makePayment();

}

  

public class Cash extends Payment {

public boolean makePayment() {

// functionality

}

}

  

public class CreditCard extends Payment {

// Data members

private String nameOnCard;

private String cardNumber;

private String billingAddress;

private int code;

  

public boolean makePayment() {

// functionality

}

}
```


Notification #


```java
// Notification is an abstract class

public abstract class Notification {

private int notificationId;

// The Date datatype represents and deals with both date and time.

private Date createdOn;

private String content;

  

// person here refers to an instance of the Person class

public abstract void sendNotification(Person person);

}

  

public class EmailNotification extends Notification {

// person here refers to an instance of the Person class

public void sendNotification(Person person) {

// functionality

}

}

  

public class PhoneNotification extends Notification {

// person here refers to an instance of the Person class

public void sendNotification(Person person) {

// functionality

}

}
```


Booking #

```java
public class Booking {

// Data members

private int bookingId;

private int amount;

private int totalSeats;

  

// The Date datatype represents and deals with both date and time.

private Date createdOn;

  

// BookingStatus enum

private BookingStatus status;

// Instances of classes

private Payment payment;

private ShowTime show;

private List<MovieTicket> tickets;

private List<Seat> seats;

}
```


Search and catalog#


```java
public interface Search {

public List<Movie> searchMovieTitle(String title);

public List<Movie> searchMovieLanguage(String language);

public List<Movie> searchMovieGenre(String genre);

public List<Movie> searchMovieReleaseDate(Date date);

}

  

public class Catalog implements Search {

HashMap<String, List<Movie>> movieTitles;

HashMap<String, List<Movie>> movieLanguages;

HashMap<String, List<Movie>> movieGenres;

  

// The Date datatype represents and deals with both date and time.

HashMap<Date, List<Movie>> movieReleaseDates;

  

public List<Movie> searchMovieTitle(String title) {

// functionality

}

  

public List<Movie> searchMovieLanguage(String language) {

// functionality

}

  

public List<Movie> searchMovieGenre(String genre) {

// functionality

}

  

public List<Movie> searchMovieReleaseDate(Date date) {

// functionality

}

}


```

