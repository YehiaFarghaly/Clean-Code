# Clean-Code
Summary of Clean Code book by 'Robert C. Martin'
### Table of Content :
* [Chapter (2) Meaningful names](#chapter-2-meaningful-names)


## Chapter 2 Meaningful names
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






