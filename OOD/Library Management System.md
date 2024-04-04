

```java
// definition of enumerations used in library management system

enum BookFormat {

HARDCOVER,

PAPERBACK,

AUDIOBOOK,

EBOOK,

NEWSPAPER,

MAGAZINE,

JOURNAL

}

  

enum BookStatus {

AVAILABLE,

RESERVED,

LOANED,

LOST

}

  

enum ReservationStatus {

WAITING,

PENDING,

CANCELED,

NONE

}

  

enum AccountStatus {

ACTIVE,

CLOSED,

CANCELED,

BLACKLISTED,

NONE

}
```



### Address and person

```java
public class Address {

private String streetAddress;

private String city;

private String state;

private int zipCode;

private String country;

}

  

public class Person {

private String name;

private Address address;

private String email;

private String phone;

}
```

User#

```java
// User is an abstract class

public abstract class User {

private String id;

private String password;

private AccountStatus status;

private Person person;

private LibraryCard card;

  

public abstract boolean resetPassword();

}

  

public class Librarian extends User {

public boolean addBookItem(BookItem bookItem);

public boolean blockMember(Member member);

public boolean unBlockMember(Member member);

public boolean resetPassword() {

// definition

}

public boolean addBookItem(BookItem bookItem) {

// definition

}

}

  

public class Member extends User {

private Date dateOfMembership;

private int totalBooksCheckedOut;

  

public boolean reserveBookItem(BookItem bookItem);

private void incrementTotalBooksCheckedOut();

public boolean checkoutBookItem(BookItem bookItem);

private void checkForFine(String bookItemId);

public void returnBookItem(BookItem bookItem);

public boolean renewBookItem(BookItem bookItem);

public boolean resetPassword() {

// definition

}

}
```


Book reservation, book lending and fine #

```java
public class BookReservation {

private String itemId;

private Date creationDate;

private ReservationStatus status;

private String memberId;

  

public static BookReservation fetchReservationDetails(String bookItemId);

}

  

public class BookLending {

private String itemId;

private Date creationDate;

private Date dueDate;

private Date returnDate;

private String memberId;

private BookReservation bookReservation;

private User user;

  

public static boolean lendBook(String bookItemId, String memberId);

public static BookLending fetchLendingDetails(String bookItemId);

}

  

public class Fine {

private Date creationDate;

private String bookItemId;

private String memberId;

  

public static void collectFine(String memberId, long days);

}
```


Book and rack #

```java
// User is an abstract class

public abstract class Book {

private String isbn;

private String title;

private String subject;

private String publisher;

private String language;

private int numberOfPages;

private BookFormat bookFormat;

private List<Author> authors;

}

  

public class BookItem extends Book {

private String id;

private boolean isReferenceOnly;

private Date borrowed;

private Date dueDate;

private double price;

private BookStatus status;

private Date dateOfPurchase;

private Date publicationDate;

private Rack placedAt;

  

public boolean checkout(String memberId);

public void setPlacedAt(Rack rack) {

// definition

}

public void setAddedBy(Librarian librarian) {

// definition

}

}

  

public class Rack {

private int number;

private String locationIdentifier;

private List<BookItem> bookItems;

public void addBookItem(BookItem bookItem) {

// definition

}

}
```


Notification#

```java
// User is an abstract class

public abstract class Notification {

Private String notificationId;

Private Date creationDate;

Private String content;

private BookLending bookLending;

private BookReservation bookReservation;

  

public abstract boolean sendNotification();

}

  

public class PostalNotification extends Notification {

private Address address;

  

public boolean sendNotification(){

// definition

}

}

  

public class EmailNotification extends Notification {

private String email;

  

public boolean sendNotification(){

// definition

}

}
```


Search and catalog#
```java
public interface Search {

// Interface method (does not have a body)

public List<Book> searchByTitle(String title);

public List<Book> searchByAuthor(String author);

public List<Book> searchBySubject(String subject);

public List<Book> searchByPublicationDate(Date publishDate);

}

  

public class Catalog implements Search {

private HashMap<String, List<Book>> bookTitles;

private HashMap<String, List<Book>> bookAuthors;

private HashMap<String, List<Book>> bookSubjects;

private HashMap<String, List<Book>> bookPublicationDates;

  

public List<Book> searchByTitle(String query) {

// definition

}

public List<Book> searchByAuthor(String query) {

// definition

}

public List<Book> searchBySubject(String query) {

// definition

}

public List<Book> searchByPublicationDate(String query) {

// definition

}

}


```

### Library

```java
public class Library

{

private String name;

private Address address;

  

// Private constructor to prevent external instantiation

private Library() {}

  

public Address getAddress();

  

// The Library is a singleton class that ensures it will have only one active instance at a time

private static Library library = null;

  

// Created a static method to access the singleton instance of Library class

public static Library getInstance ()

{

if (library == null)

{

library = new Library ();

}

return library;

}

}
```

