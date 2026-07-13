### Big O

Big-O describes how the work grows as the iput grows. It ignores constants and small terms and asks: if the input doubles, what happens to the running time? 

Think of n as the "number of items"

1. O(1) - Constant
- same work no matter how big n is. 
e.g reading arr[5]

2. O (log n) - logarithmic
- work grows slowly; doubling n adds one step.
e.g search in a balanced BST

3. O(n) - linear 
- work grows in step with n
e.g scanning a list once. 

4. O (n log n) - linearithmoc 
- a bit worse than linear
e.g good sorting algorithms

5. O (n^2) - quadratic 
- doubling n quadruples the work 
e.g comparing every pair

The mental test: count how many times the input gets touched as n grows


### Back to the Basics
Big-O is answering one problem. In an easy english example, we're saying, *If the amoint stuff I'm dealing with gets much bigger, is my method going to to a crawl?*

It's not a stopwatch measuring seconds but rather it describes how the effort grows as the amount stuff grows. Two methods might both feel instant on a small amount of data. The real question Big-O answers is what happens when the data gets huge. 

1. O(1) - Constant
- The job: "What's the first name on the register?" You glance at the top line and you're done. Whether the register holds 5 names or 5,000, it's one look. The work never changes as the list grows. That's O(1) — the size of the pile is irrelevant to you. Reading arr[5] is the same idea: you jump straight to that spot without wading through anything.

2. O (log n) - logarithmic (aka the clever one)
- The job: "Is 'Grace' on the register?" — but this time the names are in alphabetical order. You don't start at the top. You open to the middle. Is Grace before or after that name? If she's after it, you throw away the entire first half and never look at it again. Then you go to the middle of what's left and throw away half again. Every step deletes half the remaining names. Here's the magic: if the register suddenly doubled in size, you'd need only one extra step. Halving is brutally fast — a list of 1,000 names takes about 10 steps, and a million names takes about 20. That's why searching a balanced BST is so cheap: the tree is built so you can halve like this. The catch is that it only works if things are kept in order.

3. O(n) - linear 
- The job: "Read out every name." Now you have no shortcut you touch each name exactly once. Twice as many students, twice as long. The work grows in lockstep with the list. Scanning once, counting items, summing a column of numbers: all O(n).

4. O (n log n) - linearithmic 
- The job: "Sort the shuffled register into alphabetical order." You still have to handle every name — that's the n part — but a smart sort does it in rounds, pairing and merging, and the number of rounds is only log n because each round doubles the size of the sorted chunks. So it's n work done log n times: n × log n. Concretely, 8 names take 3 rounds; a million names take about 20. It lands just a single step above plain linear — nowhere near the explosion of O(n²) — which is why it's the standard price of a good sort. Reach for this description whenever something has to be put in order.

5. O (n^2) - quadratic 
- The job: "Find any duplicate names by comparing each name against every other name." For the first name, you check it against all the others. For the second name, all the others again. For every single name, you sweep the whole list — a loop inside a loop. The trap: double the list and the work roughly quadruples. 10 names is about 100 comparisons; 20 names is about 400; 100 names is 10,000. It balloons. (A party where everyone shakes hands with everyone works the same way — double the guests, roughly quadruple the handshakes.) O(n²) is perfectly fine for small piles and genuinely dangerous for big ones.


#### What is the point of Big-O
**Will this still work when the input gets bigger**
It compares the method not the machine. It ignores constants and hardware - so what's left is astatement about the approach itself. 

It predicts behavior you haven't test. 
Your code works fine on 100 rows today. Big-O lets you reason about 100 million rows without running it — because you know the shape of the growth. An O(n) method that handles a thousand items in a blink will handle a billion in about a billion times the work; an O(n²) one will quietly become unusable somewhere you never checked. You're forecasting the future of the program from its structure alone.

It tells you where the pain will come from. 
As the input grows, the biggest term swamps everything else — a millionfold n² dwarfs any n term beside it — so Big-O keeps only the dominant part. It's a spotlight on the thing that will eventually hurt, and it ignores the rest so you can see it.


#### Summary for this document is
Big-O notation is a way of classifying how an algorithm's running time (or memory) grows as its input grows — naming the shape of that growth — while ignoring constants and small terms

O(1) — constant. Work never changes with input size. Grab the first name off the register: one look, whether it holds 5 names or 5,000. e.g. reading arr[0].

O(log n) — logarithmic. Each step throws away half of what's left, so doubling the input adds only one step. Find a name in a sorted register by always splitting to the middle; a million names takes about 20 steps. Only works if things are kept in order.

O(n) — linear. Work grows in lockstep with the input — touch each item once. Read out every name; twice as many names, twice as long. e.g. scanning a list once.

O(n log n) — linearithmic. You still handle every item (the n), but a smart method works in rounds, and there are only log n rounds because each round doubles the size of the sorted chunks — so n work done log n times. Sort a shuffled register: 8 names take 3 rounds. Sits just above linear. e.g. a good sorting algorithm like merge sort.

O(n²) — quadratic. For every item you sweep the whole list — a loop inside a loop — so doubling the input roughly quadruples the work. Find duplicate names by comparing each against every other; 10 names ≈ 100 comparisons, 20 ≈ 400. Fine for small inputs, dangerous for big ones. e.g. comparing every pair.
