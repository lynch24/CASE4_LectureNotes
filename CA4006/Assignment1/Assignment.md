# CA4006
## Problem specification:
- A bookstore is open 24 hours a day, 365 days a year. The bookstore has multiple sections such as fiction, horror, romance, fantasy, poetry, and history.

-  Time in the bookstore is measured in ticks. There are 1000 ticks in a day. Every 100 ticks (on average) a delivery is made of 10 books, with a random number of books for each of the above categories (totaling 10) e.g., 4 for horror, 2 for poetry, 1 for history, etc.

- When a delivery of books arrives, they are put into a box, where an assistant who works in the bookstore can put (stock) the books into their respective sections (assuming they are not busy). Only one person (e.g. assistant) can take books from the box at the same time. Once they are finished another assistant can take books from the box. Each assistant can carry up to 10 books at once. 

- Every 10 ticks (on average) a customer will buy a book from one of the sections (randomly). If the section is empty, the customer will wait until a book for that section becomes available. This means there may be times where a particular section does not contain any books, and the customer will wait until a book for that section is available.  

- It takes an assistant 10 ticks to walk from where the deliveries arrive to a particular section (e.g., to the fiction section), and 1 tick extra for every book they are carrying to that section. Additionally, for every book they put on the shelf, it takes 1 tick. In this example, it would take 20 ticks for an assistant to carry 10 books to the fiction section, and another 10 ticks to stock that section with all 10 books. If they return to the delivery area where books arrive from any section, it will take 10 ticks. 

- If an assistant is carrying books to stock multiple sections, it will take them 10 ticks to walk from one section to another section to begin stocking that section plus 1 tick for every remaining book (to be stocked) that they are carrying. For example, they may stock some books in the fiction section first, and then carry the remaining books to another section. When they are finished, they return to the delivery area to see if there are more books to be stocked, if not, they wait. The journey from any section back to the delivery area where books arrive takes 10 ticks. You can assume that it takes 0 ticks for an assistant to  take books from the box.

- Note: Given that 100 books arrive (on average) per day to the bookstore, and 100 books will be bought (on average) per day by customers, there will be times where some sections may not contain any books. In these instances, customers will need to wait for the book to be available
## Task:
- Design a software system to simulate the concurrent operation of the bookshop. Assume that books are the resources, and the different activities are conducted in threads e.g., assistants, customers, etc. 


Example of output:

```
<Tick count> <Thread ID> Deposited a box of books 
<Tick count> <Thread ID> Assistant-1 collected 7 books: 4 POETRY, 3 FICTION
<Tick count> <Thread ID> Assistant-1 began stocking POETRY section with 4 books
<Tick count> <Thread ID> Assistant-3 finished stocking FICTION section with 3 books
<Tick count> <Thread ID> Customer-7 collected a HISTORY book having waited 90 TICKS
<Tick count> <Thread ID> Assistant-1 finished stocking POTERY section with 4 books
```

- Output the a log like above in a file: “output.dat”

- Ensure that it is clear and easy to follow. Interesting/noteworthy excerpts of this should be discussed in your 5-minute video (see below).
## Deliverables and instructions for submission: 
- The assignment is a two person project, worth 25% of the overall module mark and has to be programmed in Java. Submission is through Loop. You are required to submit a zip containing: 

- All your source files: unless instructed otherwise. I assume that I should be able to compile your code with “javac “ and execute it with “java ”. Don’t count on me to install non-standard libraries! 

- A short PDF design documentation (5 pages max) - which may also get you some partial credit if I cannot get your program to execute as it should. The report should (among other things) describe/provide: 

- what aspects of the project you got working / not working / partly working

- how you divided the work between you 

- how to compile and run the code (on Linux/Ubuntu) e.g., if there is a config file to change parameters

- what are the considered tasks/dependencies in your program 

- what patterns/strategies did you use to manage concurrency 

- how your solution addresses issues like fairness, prevention of starvation etc. 

- A demo video (5 min max) describing the structure of your code and the working of your application (demonstration of interesting execution scenarios is important). NOTE: if your video is larger than 80MB then you cannot upload it to Loop. You will need to put it on Google drive and include a link to at the beginning of your design document. 

- A completed plagiarism declaration form which is signed by both of you. 

## Grading 
- A minimal version of the project: 
- To pass the assignment, it could be created following these assumptions: 

- A delivery of 10 books is made with a probability of .01 every tick. 

- Bookshelf capacity is unlimited 

- 1 bookstore assistant

- 3 book sections e.g., fiction, history and scifi.


## A good project: 
- The specifications above are a minimum requirement to pass this assignment. For good work, I expect: 

- More than 1 assistant 

- Prioritising stocking books in certain sections based on customers waiting/empty sections (to minimise customer wait time)

- Bookshelves with a limited capacity

- Real-time reporting on the number of threads executing/number of jobs being performed 


## An excellent project: 
- The project would need to contain higher forms of creativity that go beyond a good project e.g., 

- Breaks taken by assistants (e.g., every 200-300 ticks an assistant will take a break of 150 ticks). 

- Configurable parameters (e.g., number of assistants, number of book sections, control of probabilities of customer purchase behaviour, etc.) 

- Ability to make the application move faster or slower (i.e., changing the mapping between tics and time) 

- Nice GUIs 

- Analysis of tradeoffs between different statistics like average waiting for customers vs amount of time each assistant spent working, etc


## Some other points:
- If a delivery of 10 books arrives every 100 ticks, the probability that a delivery of books will arrive in 1 tick is 1/100. You can simulate this using one of Java’s random functions e.g.:

- Random randgen = new Random(seed); //  set a seed to replicate behaviour

- your_wait_ticks ( 2 * randgen.nextDouble() * 100 )

- The idea here is that there will be differing times between book deliveries, but the average wait time will converge to 100 (on average).

- You can assume each section of the book store begins with 1 book.

- Remember: A key purpose of this assignment is for groups to be able to demonstrate they understand issues related to concurrency, and how they can be addressed. Use this as an opportunity to showcase what you have learned.

- Code should be commented.

- Suitable annotations should be used e.g., @GuardedBy, @Override, etc 

