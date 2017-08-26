# Library Menu

**Objectives**: Make an interactive menu for a library to add books, add patrons, check out books, and return books. You'll explore how to respond to user inputs, how an application would be organized, and how data relates to each other.

### Step 1
Make your console project with the .NET Core CLI:
```
mkdir -p ~/workspace/csharp/exercises/librarymenu&& cd $_
dotnet new console
dotnet restore
code .
```

### Step 2
Build a Book class.

A Book should have a title, an author, and a way to see if the book is checked out. 

### Step 3
Build a Patron class.

A Patron has a name (first name and last name), a unique library card number, a list of checked out books, and a way to see if a patron can check out an additional book. A patron can only checkout 5 books at one time.

### Step 4
Build a Library class.

A library has a list of books, a list of patrons, a name, the following functionality:

- the ability to add a new book to the library
- the ability to add a new patron to the library
- the ability to retrieve all the books of the library
- the ability to retrieve all *available* books of the library
- the ability to retrieve all the patrons of the library
- the ability to retrieve all the patrons who are allowed to check out another book
- the ability to check out a book to a patron (the book is marked as unavailable, and the book is added to the patron's checked out books - but only if a patron is allowed to check out and additional book)
- the ability to return a checked out book to the library (the book is marked as available, and the book is removed from the patron's checked out books)

If you want to move the functionality into a separate LibraryService class, you may. It's up to you.

### Step 5
Implement a main menu to display on start up.

Here's your menu:
```
Library System Menu
-------------------
1 - See All Books
2 - See All Patrons
3 - Add New Book To Library
4 - Add New Patron to Library
5 - Check Out Book to Patron
6 - Return Book to Library
7 - Exit or Quit
```

**Optional Pro-Tip**: You'll only want ONE instance of the `Library` class in your program - probably one of the first things you'll want in the Program.cs. Feel free to pass the one instance of the library to other classes as needed, but you should only say `new Library();` once in the whole application. You'll find you have funny behavior if you create multiple instances of `Library`.

### Step 4
Prepopulate the library with 5 patrons and 5 books on the load of the application. 

### Step 5
Implement menu option 1 (see all books).

When a user selects option 1, display all the books in the library in this format:
```
{book.Title}
	By {book.Author}
	This book {(book.IsAvailable ? is available : is not available)}.
```

### Step 6
Implement menu option 2 (see all patrons).

When a user selects option 2, display all patrons in the library in this format:
```
{patron.FirstName} {patron.LastName} - {patron.libraryCardNumber}
```

### Step 7
Implement menu option 3 (add new book).

Ask the user to provide the new book's title and author. Use those to create a new Book and add it to the library's book list.

### Step 8
Implement menu option 4 (add a new patron)

Ask the user for the patron's name and generate the patron's library card number.

(**Pro Tip** - 
It might be hard to keep up with what number you are on for generating library card numbers. You can get around that by giving it a unique value.

You can create a unique value from their data {patronlastname}-{currentTimeInMinutes}{inSeconds}{inMilliseconds} - which would generate something like williams-265319  

As long as the value is unique enough for this project, you should be fine.)

### Step 9
Implement menu option 5 (check out book to patron)

In order to implement this option, follow these steps:
1. List all the patrons in the library that can check out another book (remember, if they have 5 checked out, they cannot checkout another book)
2. Have the user choose which patron (optionally, you can have them choose by library card number)
3. List all the books in the library that are available (not checked out by another patron).
6. Have the user select the book to add to the patron.
7. Add the book to the patron's list of checked out books and mark the book as not available.

### Step 10
Implement menu option 6 (return book to the library)

Have the user select a patron from a list of the patrons with at least one book checked out. List the books the selected patron has checked out, and have the user select which book to return. Remove the selected book from the patron's list of checked out books, and mark the book as available. 

### Step 11
Implement menu option 7 (exiting)

If the user selects 7 or enters "exit" or "close", close the window (do nothing).

### Step 12
Once the user has completed a menu option, return the user to the main menu.

Unless the user closes the window or chooses 7, exit, or close on the main menu, the window should always return to the main menu.

### Step 13
Error handling and user experience

In the main menu, if a user selects a menu option that does not exist, print a helpful message "{selection} is not a valid menu option. Please try again." and ask them for their selection again.

For all the interactions in each of menu options 3-6, confirm with the user that their input is correct. For example: "You have entered Charlotte's Web as the title. Is that correct? (y, n)". If the user selects n, allow them to try again.
 
### Step 14
Clean up your code!

Move your main menu into it's own class. Move each menu option implementation into it's own class. You shouldn't have to scroll in your Program.cs file to see all of your code.

Consider refactoring your code to an implementation that makes more sense to you, as long as you do not lose functionality. Make your code as reusable and modular as possible.
