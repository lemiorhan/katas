EJECTED TRANSACTIONS

SCENARIO

You are provided with a list of transactions representing consumers' purchases.
Each transaction can be either approved or rejected based on total sum of approved purchases the consumer made so far.

Specifically the transaction is rejected if total sum of purchases would increase above a certain number - creditLimit. Otherwise the transaction is approved.

Your task is to process the list of transactions and return list of the rejected ones.

INPUT

You should write a function called findRejectedTransactions, which takes as input a list
of transactions to process and a creditLimit integer.
List<String> findRejectedTransactions(List<String> transactions, int creditLimit);


Transactions are provided in a CSV format. An example transaction may look this:
"John,Doe,john@doe.com,30,TR000"

Each transaction contains consumer details as well as an amount and an id:

first name
last name
email
amount
transaction id

You should expect all the transactions being valid and containing all of the information listed above.

Additionally there is a creditLimit >= 0 defined that is equal to all the consumers.

OUTPUT

The function should return a list of Strings listing the transactions that supposed to be rejected if the transactions were to be processed in a sequential manner following the initial order of elements.

A consumer is uniquely identified by all three of first name, last name and email,
i.e. two persons with equal names but different emails have separate credit line.

EXAMPLES

findRejectedTransactions([], 0) returns empty list []

findRejectedTransactions(["John,Doe,john@doe.com,200,TR0001"], 200) returns empty list [] - the only John Doe's transaction is approved

findRejectedTransactions(["Jane,Doe,jane@doe.com,201,TR0001"], 200) returns [TR0001] - the only Jane Doe's transaction is rejected since its amount 201 is greater than creditLimit = 200

findRejectedTransactions(["Jane,Doe,jane@doe.com,199,TR0001", "Jane,Doe,jane@doe.com,2,TR0002"], 200) returns [TR0002] as approving the second transaction would make the credit limit exceeded









DISC SPACE

SCENARIO

You've been assigned to a task force aiming to develop a new generation of hard disk drives.
One of the key components you will work on, is responsible for storing the data on the drive.

We need of a function that can determine if a certain file can be stored in given a disk block in one chunk. In order to tell that there must be at least fileSize number of contiguous free disk sectors in a given block.

You are given Set<Integer> occupiedSectors where each element is a sector between 1 and blockSize that is already occupied by some other data. The sectors are free to be written to otherwise.

Return a boolean stating if it is possible to store the file in the given block.

Although it is an early experimental development phase, please keep in mind that, it is undesired to have the so-far-excellent disk performance degraded by way-too-slow isWritable method execution.

INPUT

Method signature:

boolean isWritable(int blockSize, int fileSize, Set<Integer> occupiedSectors)

Constraints:

1. blockSize will be between 1 and 1,000,000, inclusive.
2. fileSize will be between 1 and blockSize, inclusive.
3. occupiedSectors will contain between 1 and 100,000 elements, inclusive.
4. Each element of occupiedSectors will be between 1 and blockSize, inclusive.
5. Elements of occupiedSectors will be distinct.
6. Expected execution time is below 10 seconds.

OUTPUT

A boolean result telling if it is possible to store the file on a given disk block.

EXAMPLES

isWritable(1, 1, []) returns true as there is exactly 1 free sector which is enough to store the file of size 1
isWritable(1, 1, [1]) returns false as there's no free disk space at all
isWritable(4, 2, [1, 4]) returns true as the file of size 2 can be stored on sectors 2 and 3










DISC SPACE

SCENARIO

Functional Smooothies Inc. is releasing a new smoothie machine that will make the best icy fruit beverages of all time.

According to Wikipedia: A smoothie (occasionally spelled smoothee or smoothy) is a thick, cold beverage made from pureed raw fruit blended with ice cream or frozen yogurt along with other ingredients such as crushed ice, fruit juice, sweeteners, dairy products, nuts, seeds, etc.

In order to sell the machine to smoothie vendors all over the world, Functional Smooothies needs to ensure that the machine takes all dietary preferences and allergies into account. They have hired you to write the software for the machine.

The software has a menu of standard smoothie options, including the ingredients for each drink. When a customer places their order, they supply a list of zero or more dietary restrictions that must be honoured. Your software will print out a list of the ingredients that the smoothie operator needs to put into the machine.

Menu: The menu options, along with the ingredients needed for each are as follows.

1. Classic: strawberry, banana, pineapple, mango, peach, honey
2. Freezie: blackberry, blueberry, black currant, grape juice, frozen yogurt
3. Greenie: green apple, lime, avocado, spinach, ice, apple juice
4. Just Desserts: banana, ice cream, chocolate, peanut, cherry


INPUT

You should write a function called ingredients, which takes as input a string containing item from the menu and optionally one or more ingredients to omit from the smoothie, separated by commas.

Restricted ingredients have to be preceded by - sign, as opposed to the ones that should be added. As adding new ingredients is not supported yet, any input with additional ingredients is considered invalid.

Note that in a very rare cases of the user input processor mechanical failures, there order might be lost or arrive empty to the software.





OUTPUT

The function should return a string listing the ingredients that the operator needs to put in. To make it more convenient for the operator, the ingredients should be listed in alphabetical order and separated by commas in the string returned from the function.

In case of input being invalid an IllegalArgumentException should be thrown. Smoothie with no ingredients is represented as "".


EXAMPLES

if a customer orders a Classic but is allergic to strawberry and peanuts, your function will be called with the argument "Classic,-strawberry,-peanut" should return "banana,honey,mango,peach,pineapple". Note that it is valid have the allergens not present in the ordered smoothie. Requesting Classic with additional chocolate "Classic,chocolate" should result in IllegalArgumentException being thrown. Same result should apply for requesting a smoothie that is not present in the menu "Vitamin smoothie".


