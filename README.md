# Exercise 6.12 Joke Manager

The exercise base contains the following program that has been written "in the main".

```python
jokes = []
print("What a joke!")

while True:
    print("Commands:")
    print(" 1 - add a joke")
    print(" 2 - draw a joke")
    print(" 3 - list jokes")
    print(" X - stop")

    command = input()

    if (command=="X"):
        break

    if (command=="1"):
        print("Write the joke to be added:")
        joke = input()
        jokes.add_joke(joke)
    else if (command=="2"):
        print("Drawing a joke.")

        if (jokes.is_empty()):
            print("Jokes are in short supply.")
        else:
            draw = Random()
            index = draw.next_int(len(jokes))
            print(jokes[index])

    else if (command=="3"):
        print("Printing the jokes.")
        for joke in jokes:
            print(joke)
```

The application is in practice a storage for jokes. You can add jokes, get a randomized joke, and the stored jokes can be printed. In this exercise the program is divided into parts in a guided manner.

## Joke manager

Create a class called `JokeManager` and move the functionality to manage jokes in it. The class must have a parameter-free constructor, and the following methods:

- `def add_joke(self, joke)` - adds a joke to the manager.
- `def draw_joke()` - chooses one joke at random and returns it. It there are no jokes stored in the joke manager, the method should return the string "Jokes are in short supply.".
- `def print_jokes()` - prints all the jokes stored in the joke manager.

An example of how to use the class:

```python
manager = JokeManager()
manager.add_joke("What is red and smells of blue paint? - Red paint.")
manager.add_joke("What is blue and smells of red paint? - Blue paint.")

print("Drawing jokes:")
for i in range(5):
    print(manager.draw_jokes())

print("")
print("Drawing jokes:")
manager.print_jokes()
```

Below is a possible output of the program. Notice that the jokes will probably not be drawn as in this example.

```plaintext
Drawing jokes:
What is blue and smells of red paint? - Blue paint.
What is red and smells of blue paint? - Red paint.
What is blue and smells of red paint? - Blue paint.
What is blue and smells of red paint? - Blue paint.
What is blue and smells of red paint? - Blue paint.

Printing jokes:
What is red and smells of blue paint? - Red paint.
What is blue and smells of red paint? - Blue paint.
```

## User interface

Create a class called `UserInterface` and move the UI functionality of the program theres. The class must have a constructor with two parameters. The first parameter is an instance of the JokeManager class, and the second parameter is an instance of the Scanner class. In addition, the class should have the method `def start()` that can be used to start the user interface.

The user interface should provide the user with the following commands:

- `X` - ending: exits the method `start`.
- `1` - adding: asks the user for the joke to be added to the joke manager, and then adds it.
- `2` - drawing: chooses a random joke from the joke manager and prints it. If there are no jokes in the manager, thi string "Jokes are in short supply." will be printed.
- `3` - printing: prints all the jokes stored in the joke manager.

An example of how to use the UI:

```python
manager = JokeManager()
interface = UserInterface(manager)
interface.start()
```

```plaintext
Commands:
1 - add a joke
2 - draw a joke
3 - list jokes
X - stop
**1**
Write the joke to be added:
**Did you hear about the claustrophobic astronaut? -- He just needed a little space.**
Commands:
1 - add a joke
2 - draw a joke
3 - list jokes
X - stop
**3**
Printing the jokes.
Did you hear about the claustrophobic astronaut? -- He just needed a little space.
Commands:
1 - add a joke
2 - draw a joke
3 - list jokes
X - stop
**X**
```

**NB:** There is no automatic testing for this exercise past syntax checking, so you should test your code before committing it.
