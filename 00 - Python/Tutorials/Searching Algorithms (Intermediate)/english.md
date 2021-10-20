To implement linear search in python first we need a list of items to search.

```py
# list of items we will search
myList = ["A", "B", "C", "D"]
```

Next we make a variable that represent the value we are wanting to find.

```py
# list of items we will search
myList = ["A", "B", "C", "D"]

# the current item we want
itemWanted = "B"
```

Then we can use a "for" loop to go over every item in the list and check if the current item matches the item we want.

```py
# list of items we will search
myList = ["A", "B", "C", "D"]

# the current item we want
itemWanted = "B"

# go through every item in myList
for item in myList:
  if item == itemWanted:
    print("Found item: " + item)

    break # exit from the loop if found itemWanted
```

But what if the item we are looking for is not in the list?

We have to have some way of checking if the search didn't find the item. For that we create a True or False variable (A bool). We set it to False initially, this way we can set it to True if we did find something, and after finishing the search we can check if the variable is still False. It is still False, we print "Item not found".

```py
# list of items we will search
myList = ["A", "B", "C", "D"]

# the current item we want
itemWeWant = "F"

# use this later so we can print message if nothing was found
found = False

# go through every item in myList
for item in myList:
  if item == itemWeWant:
    print("Found item: " + item)
    found = True

    break # exit from the loop

# if nothing was found
if found is False:
  print("Item not found")
```

Its also important to know that UPPERCASE`A` will not be equal to lowercase `a`

Binary search in Python

```py
# list of items
myList = ["A", "B", "C", "D"]

# the item we want
itemWeWant = "A"

# use this to tell if the item has been found
found = False

# find center item in list
center = round(len(myList) / 2)
currentListLen = len(myList)

# keep looking if found is false (aka if we have not found the item we want)
while found is False:
  # current center item
  currentItem = myList[center]

  # if correct
  if currentItem == itemWeWant:
    print("Found item: " + currentItem)
    found = True
  
  # once the length of the remaning list is gone we "break" or exit the loop
  if currentListLen == 0:
    break

  # if greater alphabetically
  elif itemWeWant > currentItem:
    center += round(currentListLen / 2) - 1
    currentListLen = round(currentListLen / 2)
	# start the loop over AKA "continue"
    continue

  # if lesser alphabetically
  elif itemWeWant < currentItem:
    center -= round(currentListLen / 2) - 1
    currentListLen = round(currentListLen / 2)
	# start the loop over AKA "continue"
    continue

# if nothing was found
if found is False:
  print("Item not found")
```
