We'll  make a program that asks us for a verb, a noun, and a adjective, and a pronoun. Then we'll insert those into a story to get some wacky funny stories!

At this point you could probably figure out how to do this yourself XD, but I'll tell you all the answers to ease your mind.

Make a new repl. Select the C language. Call it "story time". 

First lets make a function to ask the user a question and get an answer.

Delete the code inside of main and add the function hint.

(change your code to the following)
```c
#include <stdio.h>

void ask(char* question, char answer[20]);

int main(void) {
	
}
```

Now we can actually make the `ask` function below main.

(add the ask function below main)
```c
// ... snip ... ("main" removed for shortness)

void ask(char* question, char answer[20])
{
	printf("%s", question);
	scanf("%s", answer);
}
```

Ask literally `printf`'s the `question` you provide, then `scanf` stores it in an `asnwer` address variable (although we have to make sure the asnwer variable already has at least enough room for 20 char's).

Now we can use `ask` in main to get a verb and store it an array/address to an array.

(change your code to the following)
```c
// .. snip

int main(void) {
	char verb[20];
    ask("verb: ", verb);
}

// .. snip
```

Now we can use the `verb` variable and insert it into a story inside of `printf`! We'll also get a noun from the user.

(change your code to the following)
```c
// .. snip

int main(void) {
	char verb[20];
    ask("verb: ", verb);

	char noun[20];
    ask("noun: ", noun);

	printf("I was %s with my %s", verb, noun);
}

// .. snip
```

Run this code using the play button! Type something random and see what our program prints out!

Although, I will say this story wasn't super interesting. Your challenge (homework) is to come up with a weird story that could turn out... well... funnier than this! 

I decided to let you make the stories, rather than coaching you throught one, so you get to have fun with it!