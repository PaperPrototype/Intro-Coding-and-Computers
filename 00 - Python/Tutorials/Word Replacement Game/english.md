We will make a game where we ask the user (you) for a verb, noun and adjective (a word that describes a noun, eg. big, pretty, blue), then insert those words into a random sentence or story.

Make a new repl. Select the Python programming language. Name it "word replacement".

Now lets get those words from the user. 

(write the following code)
```py
# get input
verb = input("verb: ")
noun = input("noun: ")
adjective = input("adjective: ")
```

Now we can combine the words with a simple sentence!

(change your code to look like the following)
```py
# get input
verb = input("verb: ")
noun = input("noun: ")
adjective = input("adjective: ")

# print simple sentence
print("My dog ate my", adjective, noun, "so I had to go", verb, "and buy some food again.")
```

Now run this program! It will ask you for a verb noun and adjective. Once you finish giving the program those words, it will print out a (funny'ish) story!