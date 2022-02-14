---
layout: notes
---
# Exercise 4

You are given code for the Library class (in its own file). This is a composite class. You are going to create the Book class (the component class) in book.py file. Look over the Library class carefully to determine what attributes are needed for the Book class. In addition, the table of output contains a hint as to what method the Book class needs.

## Expected Output
To check your work, open the exercise4.py file and enter the following code.

```
library = Library()
book1 = Book('Three Musketeers', 'Alexandre Dumas', 'fiction')
book2 = Book('The Count of Monte Cristo', 'Alexandre Dumas', 'fiction')
book3 = Book('Educated', 'Tara Westover', 'nonfiction')

library.add_book(book1)
library.add_book(book2)
library.add_book(book3)
library.sort_books()
```

The following commands should produce the output on the right.

|Command|	Output|
|print(library.books)|	[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction), Book(Educated, Tara Westover, nonfiction)]|
|print(library.fiction)|	[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction)]|
|print(library.nonfiction)|	[Book(Educated, Tara Westover, nonfiction)]|
|print(library.search_author('Alexandre Dumas'))|	[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction)]|
|print(library.search_author('Herman Melville'))|	[]|
|print(library.search_title('Educated'))|	True|
|print(library.search_title('Moby Dick'))|	False|

# Solution

library.py

```
class Library:
  def __init__(self):
    self.books = []
    self.fiction = []
    self.nonfiction = []

  def add_book(self, book):
    '''Takes a Book object and adds it to self.books'''
    self.books.append(book)

  def search_title(self, title):
    '''Takes a string and returns a Boolean'''
    has_book = False
    for book in self.books:
      if title.lower() == book.title.lower():
        has_book = True
    return has_book

  def search_author(self, author):
    '''Takes a string and returns a list of Book objects'''
    author_books = []
    for book in self.books:
      if book.author.lower() == author.lower():
        author_books.append(book)
    return author_books

  def sort_books(self):
    '''Helper method for sort_fiction and sort_nonfiction'''
    self.fiction = self.sort_fiction()
    self.nonfiction = self.sort_nonfiction()

  def sort_fiction(self):
    '''Return list of Book objects where the genre is fiction'''
    fiction_books = []
    for book in self.books:
      if book.genre.lower() == 'fiction':
        fiction_books.append(book)
    return fiction_books

  def sort_nonfiction(self):
    '''Return list of Book objects where the genre is nonfiction'''
    nonfiction_books = []
    for book in self.books:
      if book.genre.lower() == 'nonfiction':
        nonfiction_books.append(book)
    return nonfiction_books
```

book.py

```
class Book():
  def __init__(self, title, author, genre):
    self.title = title
    self.author = author
    self.genre = genre

  def __str__(self):
    return f'{self.title}, {self.author}, {self.genre}'

  def __repr__(self):
    return f'Book({self})'
```

excercise4.py

```
from library import Library
from book import Book

library = Library()
book1 = Book('Three Musketeers', 'Alexandre Dumas', 'fiction')
book2 = Book('The Count of Monte Cristo', 'Alexandre Dumas', 'fiction')
book3 = Book('Educated', 'Tara Westover', 'nonfiction')

library.add_book(book1)
library.add_book(book2)
library.add_book(book3)
library.sort_books()

print(library.books) #[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction), Book(Educated, Tara Westover, nonfiction)]
print(library.fiction)	#[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction)]
print(library.nonfiction) #[Book(Educated, Tara Westover, nonfiction)]
print(library.search_author('Alexandre Dumas'))	#[Book(Three Musketeers, Alexandre Dumas, fiction), Book(The Count of Monte Cristo, Alexandre Dumas, fiction)]
print(library.search_author('Herman Melville'))	#[]
print(library.search_title('Educated'))	#True
print(library.search_title('Moby Dick')) #False
```
