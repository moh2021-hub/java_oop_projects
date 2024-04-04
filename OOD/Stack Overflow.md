```java
enum AccountStatus {

ACTIVE,

BLOCKED,

DISABLED

}

  

enum QuestionStatus {

ACTIVE,

CLOSED,

FLAGGED,

BOUNTIED

}

  

enum ClosingDetail {

COMMUNITY_SPECIFIC_REASON,

DUPLICATE,

NEEDS_CLARITY,

NEEDS_MORE_FOCUS,

OPINION_BASED

}
```


account 
```java
public class Account {

private String accountId;

private String username;

private String password;

private String name;

private String email;

private int phone;

private AccountStatus status;

  

public boolean resetPassword();

}
```

User, admin, moderator, and guest#

```java
public class User {

private int reputationPoints;

private Account account;

private List<Badge> badges;

  

public boolean createQuestion(Question question);

public boolean addAnswer(Question, question, Answer answer);

public boolean createComment(Comment comment);

public boolean createTag(Tag tag);

public void flagQuestion(Question question);

public void flagAnswer(Answer answer);

public void upvote(int id);

public void downvote(int id);

public void voteToCloseQuestion(Question question);

public void voteToDeleteQuestion(Question question);

public void acceptAnswer(Answer answer);

}

  

public class Admin extends User {

public boolean blockUser(User user);

public boolean unblockUser(User user);

public void awardBadge(User user, Badge badge);

}

  

public class Moderator extends User {

public void closeQuestion(Question question);

public void reopenQuestion(Question question);

public void deleteQuestion(Question question);

public void restoreQuestion(Question question);

public void deleteAnswer(Answer answer);

}

  

public class Guest {

public void registerAccount();

}
```


Question, answer, comment, and bounty#

```java
public class Question {

private int id;

private String title;

private String content;

private User createdBy;

private int upvotes;

private int downvotes;

private int viewCount;

private int score;

private int voteCount;

private Date creationDate;

private Date modificationDate;

private QuestionStatus status;

private ClosingDetails closingReason;

private Bounty bounty;

  

private List<Tag> tags;

private List<Comment> comments;

private List<Answer> answers;

private List<User> followers;

  

public void addComment(Comment comment);

public void addBounty(Bounty bounty);

}

  

public class Comment {

private int id;

private String content;

private int flagCount;

private int upvotes;

private Date creationDate;

private User postedBy;

}

  

public class Answer {

private int id;

private String content;

private int flagCount;

private int voteCount;

private int upvotes;

private int downvotes;

private boolean isAccepted;

private Date creationTime;

private User postedBy;

  

private List<Comment> comments;

private List<User> followers;

  

public void addComment(Comment comment);

}

  

public class Bounty {

private int reputationPoints;

private Date expiryDate;

public boolean updateReputationPoints(int reputation);

}
```


Badge, tag, and tag list

```java
public class Badge {

private String name;

private String description;

}

  

public class Tag {

private String name;

private String description;

}

  

public class TagList {

private HashMap<Tag, int> tagsCount;

public void incrementTagCount();

public void decrementTagCount();

}
```


Notification 
```java
public class Notification {

private int notificationId;

private Date createdOn;

private String content;

  

public boolean sendNotification(Account account);

}
```


Search catalog and interface#

```java
public interface Search {

public List<Question> searchByTags(String name);

public List<Question> searchByUsers(String name);

public List<Question> searchByWords(String words);

}

  

public class SearchCatalog implements Search {

private HashMap<String, List<Tag>> questionsUsingTags;

private HashMap<String, List<User>> questionsUsingUsers;

private HashMap<String, List<String>> questionsUsingWords;

  

public List<Question> searchByTags(String name) {

// functionality

}

  

public List<Question> searchByUsers(String name) {

// functionality

}

  

public List<Question> searchByWords(String words) {

// functionality

}

}
```



```java
```

