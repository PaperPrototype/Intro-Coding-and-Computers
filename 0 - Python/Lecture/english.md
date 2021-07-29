# Instructions
In real life we give people instructions on how to do something. In computers we can do the same thing using "code". 

Code is just instructions. One of the hardest problems, and most time consuming problems, is searching. 

We can write a searching algorithm using code. This algorithm has to not miss anything! So we just tell it to look at each item one by one.

Code actually looks a lot like english, although a bit more robotic. Lets start with some fake code. We are searching for a baseball.

```
Look at current item
If current item is baseball
    give baseball
Else if current item not baseball
    go to next item
    start over
```

This "code" assumes we have every item in one long line. It goes through each item until it finds what we are looking for.

But what if the item we are looking for isn't in our "one long line" of items! If this was real computer code, then the computer would probably crash! Or the computer would endlessly keep searching.

We call this code "bug". "Bugs" in computer programming are surprisingly common.

To fix this "bug" we have to change the code to expect this possibility.

```
Look at current item
If current item is NOTHING
    stop searching, exit
If current item is baseball
    give baseball
Else if current item not baseball
    go to next item
    start over
```

Now we can expect this possibility and avoid this dumb problem. At this point one thing is obvious "computers are dumb". They are not intuitive like humans. They do EXACTLY what we tell them. Like some dumb idiot who doesn't stop walking until he falls of the cliff and... dies. This is what happens often in computers when you get an "error".



