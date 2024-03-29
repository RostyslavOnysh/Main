# Producer Extends : 
For the code examples in this article, we'll use a simple data model with a User base class and two classes that extend it: Operator and Customer.
## It's important to understand that the PECS rule must be applied from the collection's point of view.
 In other words, if we iterate through a List and process its elements, the list will act as a producer for our logic:
 ```java
 public void sendEmails(List<User> users) {
    for (User user : users) {
        System.out.println("sending email to " + user);
    }
}
```

Now, let's assume we want to use the sendEmail method for a List of Operators. The Operator class extends User, so we might expect it to be a simple, straightforward method call. But, unfortunately, we'll get a compilation error:
To solve the problem, we can update the sendEmail method following the PECS rule. Because the list of users is a producer for our logic, we'll use the extends keyword:
```java
public void sendEmailsFixed(List<? extends User> users) {
    for (User user : users) {
        System.out.println("sending email to " + user);
    }
}
```
As a result, we can now easily call the method for lists of any generic type, as long as they inherit from the User class:
```java
List<Operator> operators = Arrays.asList(new Operator("sam"), new Operator("daniel"));
List<Customer> customers = Arrays.asList(new Customer("john"), new Customer("arys"));

sendEmailsFixed(operators);
sendEmailsFixed(customers);
```

# Consumer Supers
When we are adding elements to a collection, we become the producer, and the list will act as a consumer. Let's write a method that receives a list of Operators and adds two more elements to it:
```java
private void addUsersFromMarketingDepartment(List<Operator> users) {
    users.add(new Operator("john doe"));
    users.add(new Operator("jane doe"));
}
```

This is will work perfectly if we pass a list of Operators. But, if we want to use it to add the two operators to a list of Users, we'll get, yet again, a compilation error:
Therefore, we need to update the method and make it accept a collection of Operators or predecessors of it, using the super keyword:

```java 
private void addUsersFromMarketingDepartmentFixed(List<? super Operator> users) {
    users.add(new Operator("john doe"));
    users.add(new Operator("jane doe"));
}
```

#  Producing and Consuming

There might be cases where our logic needs to both read and write to the collection. In this case, the Collection will be, 
at the same time, both a producer and a consumer.
The only way to handle these scenarios is to use the base class, without any of the keywords:
```java
private void addUsersAndSendEmails(List<User> users) {
    users.add(new Operator("john doe"));
    for (User user : users) {
        System.out.println("sending email to: " + user);
    }
}
```
# Conclusion

In this article, we've discussed the Produce Extends Consumer Supers rule and learned how to apply it while working with Java collections.
We explored various usages where collections were producers or consumers of our logic. After that, we learned that if a collection is doing both, this can signal a code smell in our design.
