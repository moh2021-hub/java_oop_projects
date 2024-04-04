
```java
// Enumeration

enum Suit {

HEART,

SPADE,

CLUB,

DIAMOND

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

private String streetAddress;

private String city;

private String state;

private int zipCode;

private String country;

}
```

card 

```java
public class Card {

private Suit suit;

private int faceValue;

  

public Card(Suit suit, int faceValue);

}
```


Deck and shoe #

```java
public class Deck {

private List<Card> cards;

  

public Deck();

public List<Card> getCards();

}

  

public class Shoe {

private List<Deck> decks;

private int numberOfDecks;

  

public Shoe(int numberOfDecks, List<Deck> decks) {

// 1. createShoe();

// 2. shuffle();

}

public void createShoe();

public void shuffle();

public Card dealCard();

}

```

Hand 

```java
public class Hand {

private List<Card> cards;

  

public Hand(Card card1, Card card2);

public int getScores();

public void addCard(Card card);

}
```


Players
```java
public abstract class Player {

private String id;

private String password;

private double balance;

private AccountStatus status;

private Person person;

private Hand hand;

  

public void addHand(Hand hand);

public void removeHand(Hand hand);

public abstract boolean resetPassword();

public void addToHand(Hand hand);

}

  

public class BlackjackPlayer extends Player {

private int bet;

private int totalCash;

  

public BlackjackPlayer(Hand hand);

public void placeBet(int bet);

public boolean resetPassword(){

// definition

}

}

  

public class Dealer extends Player {

private Hand hand;

  

public int getTotalScore();

public boolean resetPassword(){

// definition

}

}
```

Blackjack controller and game view #

```java
public class BlackjackController {

public boolean validateAction();

}

  

public class BlackjackGameView {

public void playAction(String action, Hand hand);

}
```

Blackjack game #

```java
public class BlackjackGame {

private Player player;

private Dealer dealer;

private Shoe shoe;

private final int MAX_NUM_OF_DECKS = 4;

  

public BlackjackGame(BlackjackPlayer player, Dealer dealer);

public void playAction(String action, Hand hand);

public void hit(Hand hand);

public void stand();

public void start();

}
```

