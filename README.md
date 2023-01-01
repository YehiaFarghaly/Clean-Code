# Clean-Code
Summary of Clean Code book by 'Robert C. Martin' :book:
### Table of Content :
- [Chapter (2) Meaningful names](#chapter-2-meaningful-names-eyes)
- [Chapter (3) Functions](#chapter-3-functions-eyes)
- [Chapter (4) Comments](#chapter-4-comments-eyes)
___
## Chapter 2 Meaningful names :eyes:
* The variable name should tell why it exists, what it does and how it is used.
* The name that needs a comment then it does not show its intent.
* Do not refer to a grouping of accounts as an accountList even if you put them in a list, better use **accounts** or **accountGroup** or etc..
* In the absence of specific conventions, the variable moneyAmount is indistinguishable from money, customerInfo is indistinguishable from customer, etc…
* Make your names pronounceable as: **generationTimestamp** not genymdhms.
* Single-letter names and numeric constants are not easy to locate across a body of text. For example: **MAX_CLASSES_PER_STUDENT** is easy to be understood but the number 7 could be more troublesome.
* Classes and objects should have noun or noun phrase names not a verb, the first letter of each word should be capital and you should avoid abbreviations
* Methods should have verb names and the first letter of each word is capital except for the first word.
* Pick one word per concept, for example it is confusing to have fetch, retrieve and get as equivalent methods of different classes so just stick to one.
* Avoid using the same word for two purposes. Let’s say we have many classes where add will concatenate two existing Strings. Now let’s say we are writing a new class that has a method that puts its single parameter into a collection. Should we call this method add? No. we can call it **insert** or **append** or etc..
* Remember that the people who read your code will be **programmers**. So go ahead and use computer science (**CS**) terms.
* Imagine that you have variables named firstName, lastName, street, houseNumber, city, state, and zipcode. Taken together it’s pretty clear that they form an address. But what if you just saw the **state** variable being used alone in a method? Would you automatically infer that it was part of an address? Solution is to create a class named **Address**. Then, even the compiler knows that the variables belong to a bigger concept.
___
## Chapter 3 Functions :eyes:
* The first rule of functions is that they should be ~~multi-task~~ **SMALL**. Functions should not be 100 lines long neither 20 lines long. 
* ***FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY***
* It’s hard to make a small switch statement but we can make sure that each switch statement is buried in a low-level class and is never repeated
    ```
   public abstract class Employee {
     public abstract boolean isPayday();
     public abstract Money calculatePay();
     public abstract void deliverPay(Money pay);
      }
          _______________
          
   public interface EmployeeFactory {
     public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
      }
          _______________
          
  public class EmployeeFactoryImpl implements EmployeeFactory {
     public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
       switch (r.type) {
       case COMMISSIONED:
         return new CommissionedEmployee(r) ;
       case HOURLY:
         return new HourlyEmployee(r);
       case SALARIED:
        return new SalariedEmploye(r);
       default:
         throw new InvalidEmployeeType(r.type);
     }
    }
   }
    ```
* Don’t be afraid to make a name long. A long descriptive name is better than a short enigmatic name.
* The ideal number of arguments for a function is **zero**. Next comes **one**, followed closely by **two**. **Three** arguments should be avoided where possible. More than three requires very special justification
* If a function is going to transform its input argument, the transformation should appear as the **return** value. Indeed, **StringBuffer
transform(StringBuffer in)** is better than **void transform(StringBuffer out)**
* Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It
immediately complicates the signature of the method, loudly proclaiming that this function
does more than one thing. It does one thing if the flag is true and another if the flag is false, instead we should have
split the function into two
* When a function seems to need more than two or three arguments, it is likely that some of
those arguments ought to be wrapped into a class of their own
  ```
  Circle makeCircle(double x, double y, double radius);
  Circle makeCircle(Point center, double radius);
  ```
* Output arguments should be avoided. If your function must change the state
of something, have it change the state of its owning object. 
* Try/catch blocks are ugly in their own right. They confuse the structure of the code and
mix error processing with normal processing. So it is better to extract the bodies of the try
and catch blocks out into functions of their own.
```
  try {
   deletePage(page);
    registry.deleteReference(page.name);
    configKeys.deleteKey(page.name.makeKey());
    }
  catch (Exception e) {
    logger.log(e.getMessage());
  }
  ________________________________________________________________________
  
public void delete(Page page) {
 try {
    deletePageAndAllReferences(page);
  }
 catch (Exception e) {
    logError(e);
  }
 }
private void deletePageAndAllReferences(Page page) throws Exception {
 deletePage(page);
 registry.deleteReference(page.name);
 configKeys.deleteKey(page.name.makeKey());
 }
```
* Never dublicate, **Duplication** may be the root of all evil in software.

* >When I write functions, they come out long and complicated. They have lots of
indenting and nested loops. They have long argument lists. The names are arbitrary, and
there is duplicated code. But I also have a suite of unit tests that cover every one of those
clumsy lines of code.
So then I massage and refine that code, splitting out functions, changing names, eliminating duplication. I shrink the methods and reorder them. Sometimes I break out whole
classes, all the while keeping the tests passing.
In the end, I wind up with functions that follow the rules I’ve laid down in this chapter.
I don’t write them that way to start. I don’t think anyone could.     
'The Author'

___

## Chapter 4 Comments :eyes:

