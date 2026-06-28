# special-python-codes
[28/06/2026 4:30 pm] Yaw Struijk: # ==============================================================================
# THE ULTIMATE PYTHON SPECIAL (DUNDER) METHODS CHEAT SHEET WITH USAGE NOTES
# ==============================================================================

# ------------------------------------------------------------------------------
# 1. Constructor: init()
# ------------------------------------------------------------------------------
class Book:
    # METHOD EXPLANATION:
    # The init method is a constructor. It is automatically called right after 
    # a new object is created in memory. Its primary purpose is to initialize the 
    # object's attributes (its state) using the arguments passed during instantiation.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you call Book("1984", "George Orwell"), Python creates the object and 
    # automatically passes "1984" and "George Orwell" into __init__ as title 
    # and author. This attaches those values permanently to that specific book.
    initit__(self, title, author):
        self.title = title       # Sets the 'title' attribute for the instance
        self.author = author     # Sets the 'author' attribute for the instance

# Usage Example
my_book = Book("1984", "George Orwell")
print(my_book.title)  # Output: 1984


# ------------------------------------------------------------------------------
# 2. String Representatistrtr__() reprpr__()
# ------------------------------------------------------------------------------
class BookWithStr:
    # METHOD EXPLANATION:
  strtr__() reprpr__() control how an object looks when turned into a string.
    strtr__() is built for end-users. It returns a clean, readable text representation.
    reprpr__() is built for developers. It returns an unambiguous text string showing 
    #   the exact code needed to recreate the object.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # - Calling str(my_book_str) or print(my_book_str) automatically triggers 
    #   __str__() to show a clean presentation format to a user.
    # - Calling repr(my_book_str) trepr__repr__(), which is useful during debugging 
    #   to see exactly what type of object and data you are working with.
init__init__(self, title, author):
        self.title = title
        self.author = author

str __str__(self):
        return f"'{self.title}' by {self.author}"

repr__repr__(self):
        return f"BookWithStr('{self.title}', '{self.author}')"

# Usage Example
my_book_str = BookWithStr("1984", "George Orwell")
print(str(my_book_str))   # Output: '1984' by George Orwell
print(repr(my_book_str))  # Output: BookWithStr('1984', 'George Orwell')


# ------------------------------------------------------------------------------
# 3. len __len__()
# ------------------------------------------------------------------------------
class Shelf:
    # METHOD EXPLANATION:
  len __len__ method allows you to use Python's built-in len() function on your 
    # custom objects. It must return a non-negative integer.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # Instead of writing a clunky method name like my_shelf.get_total_items(), 
    # implelen __len__ lets you pass the object directly into standard Python 
    # syntax: len(my_shelf). Python looks inside the claslen __len__, and 
    # runs it.
init__init__(self, items):
        self.items = items  # Expects a list of items

len __len__(self):
        return len(self.items)

# Usage Example
my_shelf = Shelf(["Book1", "Book2", "Book3"])
print(len(my_shelf))  # Output: 3


# ------------------------------------------------------------------------------
# 4. Eqeq: __eq__()
# ------------------------------------------------------------------------------
[28/06/2026 4:30 pm] Yaw Struijk: class Box:
    # METHOD EXPLANATION:
    # By default, == checks if two variables point to the exact same memory address. 
    # Implementing __eq__ lets you compare the actual contents or properties instead.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # box1 and box2 are two completely distinct objects in memory. However, when 
    # you run box1 == box2, Python intercepts the == operator and evaluates 
    # box1.__eq__(box2). Because their size values match, it returns True.
init__init__(self, size):
        self.size = size

eqf __eq__(self, other):
        if isinstance(other, Box):
            return self.size == other.size
        return False

# Usage Example
box1 = Box(10)
box2 = Box(10)
print(box1 == box2)  # Output: True


# ------------------------------------------------------------------------------
# 5. Operator Overladd __asub __smul __mul__()
# ------------------------------------------------------------------------------
class Vector:
    # METHOD EXPLANATION:
    # Operator overloading allows your custom classes to respond to mathematical 
    # operators like +, -, and *.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # - Writing v1 + v2 tells Python to run v1.__add__(v2), returning a brand new Vector.
    # - Writing v1 - v2 tells Pythosubn v1.__sub__(v2).
    # - Writing v1 * 3 tells Pythomuln v1.__mul__(3), scaling the coordinate valuinitdef __init__(self, x, y):
        self.x = x
        self.y =add def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.sub def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.mul def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalareprdef __repr__(self):
        return f"Vector({self.x}, {self.y})"

# Usage Example
v1 = Vector(2, 4)
v2 = Vector(1, 3)
print(v1 + v2)  # Output: Vector(3, 7)
print(v1 - v2)  # Output: Vector(1, 1)
print(v1 * 3)   # Output: Vector(6, 12)


# ------------------------------------------------------------------------------
# 6. Igetitem __getitem__()
# ------------------------------------------------------------------------------
class CustomList:
    # METHOD EXPLANATION:
    # Igetitem __getitem__ gives your custom object bracket-indexing capabilities 
    # (e.g., obj[index] or obj[key]), mimicking lists or dictionaries.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you call my_list[1], Python automatically translates this request into 
    # my_list.__getitem__(1). The method reads index 1 from the internal 
    # self.elements list and returns "Binit    def __init__(self, elements):
        self.elements = elgetitem def __getitem__(self, index):
        return self.elements[index]

# Usage Example
my_list = CustomList(["Apple", "Banana", "Cherry"])
print(my_list[1])  # Output: Banana


# ------------------------------------------------------------------------------
# 7. Isetitement: __setitem__()
# ------------------------------------------------------------------------------
class ModifiableList:
    # METHOD EXPLANATIgetitemhile __getitem__setitemlue, __setitem__ lets you change or insert a 
    # value using square brackets (e.g., obj[index] = value).
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you execute my_mod_list[1] = "Blueberry", Python sees the assignment 
    # to a bracket index and runs my_mod_list.__setitem__(1, "Blueberry"), 
    # overwriting "Banana" with "inity".
    def __init__(self, elements):
        self.elements setitem
    def __setitem__(self, index, value):
        self.elements[index] = value

# Usage Example
my_mod_list = ModifiableList(["Apple", "Banana", "Cherry"])
my_mod_list[1] = "Blueberry"
print(my_mod_list.elements)  # Output: ['Apple', 'Blueberry', 'Cherry']
[28/06/2026 4:30 pm] Yaw Struijk: # ------------------------------------------------------------------------------
# 8. Membership Testing: contains()
# ------------------------------------------------------------------------------
class Team:
    # METHOD EXPLANATION:
    # The contains method tells Python how to handle the 'in' operator. 
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you call "Alice" in my_team, Python processes it as 
    # my_team.__contains__("Alice"). The method searches the list and returns 
    # True. When checking for "David", it returns False.
    initit__(self, players):
        self.players = players

    containsns__(self, player_name):
        return player_name in self.players

# Usage Example
my_team = Team(["Alice", "Bob", "Charlie"])
print("Alice" in my_team)  # Output: True
print("David" in my_team)  # Output: False


# ------------------------------------------------------------------------------
# 9. Callable Objeccallll__()
# ------------------------------------------------------------------------------
class Multiplier:
    # METHOD EXPLANATION:
    # callll__ method turns an instance of a class into something that behaves 
    # exactly like a regular function.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # First, triple = Multiplier(3) creates an instance. Then, instead of calling 
    # a method on it (like triple.multiply(5)), you can invoke the object directly 
    # using parentheses: triple(5). This calls __call__(5) and returns 15.
init__init__(self, factor):
        self.factor = factor

call__call__(self, value):
        return value * self.factor

# Usage Example
triple = Multiplier(3)
print(triple(5))  # Output: 15


# ------------------------------------------------------------------------------
# 10. Iteration Siter__iter_next__next__()
# ------------------------------------------------------------------------------
class Countdown:
    # METHOD EXPLANATION:
    # Together, these two methods implement the Iterator Protocol, making your object 
    # compatible with 'for' loops.
iter__iter__() initializes and returns the iterator.
next__next__() returns the next element step-by-step and raises StopIteration 
    #   to break the loop when empty.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When the for num in Countdown(3): loop starts, Pythoiter__iter__(). 
    # On every cycle of the loop, inext__next__() to get the next number. 
    # Once it hits 0, StopIteration triggers and the loop stops cleanly.
init__init__(self, start):
        self.current = start

iter__iter__(self):
        return self

next__next__(self):
        if self.current <= 0:
            raise StopIteration
        self.current -= 1
        return self.current + 1

# Usage Example
for num in Countdown(3):
    print(num)
# Output:
# 3
# 2
# 1


# ------------------------------------------------------------------------------
# 11. Boolean Evalbool__bool__()
# ------------------------------------------------------------------------------
class Account:
    # METHOD EXPLANATION:
  bool__bool__ method dictates how an object evaluates to Truthy or Falsy when 
    # checked inside conditional 'if' statements.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you check if not acc2:, Python checks the boolean truth value of acc2 
    # by executing acc2.__bool__(). Since the balance is 0, it returns False, 
    # making not acc2 evaluate to True, which fires the print statemeinitdef __init__(self, balance):
        self.balance = balanbooldef __bool__(self):
        return self.balance > 0

# Usage Example
acc1 = Account(100)
acc2 = Account(0)
print(bool(acc1))  # Output: True
if not acc2:
    print("Account has no funds!")  # Output gets printed
[28/06/2026 4:30 pm] Yaw Struijk: # ------------------------------------------------------------------------------
# 12. Destructor: del()
# ------------------------------------------------------------------------------
class DatabaseConnection:
    # METHOD EXPLANATION:
    # The del method serves as a destructor. It is called automatically right 
    # before an object is permanently deleted from memory.
    #
    # HOW IT IS USED IN THE EXAMPLE:
    # When you manually type del conn, you explicitly destroy the object reference. 
    # Python immediately runs __del__() right before purging it from memory, 
    # allowing it to print "Connection closed safely."
    initit__(self):
        print("Connection opened.")

    delel__(self):
        print("Connection closed safely.")

# Usage Example
conn = DatabaseConnection()  # Output: Connection opened.
del conn                     # Output: Connection closed safely.
