Spellchecker that uses a Dictionary

Explain dictionary data structure then...
We could store in a list, then sort the list, then search the list to see if the word is in the dictionary, but often you just make a really good data-structure, then add stuff to that structure in a sorted way


# Naming bool functions

(beautiful boolean function)
```c
if (isAlpha(character) == true)
{
	// is alphabetical
}
```

Imagine if we had called this function `notAlpha`...

(horifying boolean function)
```c
if (notAlpha(character) != true)
{
	// is alphabetical
}
```

Now that is pretty confusing! In math 2 minus signs `12 - - 4` are the same as a plus sign `12 + 4`. The same is true of "not not" in the `if (notAlpha(character) != true)`.

To prevent this mental horror, we should ALWAYS name our boolean functions, to check "if something is TRUE".
