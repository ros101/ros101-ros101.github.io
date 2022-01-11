---
layout: notes
---
# Exercise 5
The Substitute class reads a text file and replaces every fifth word with the string HELLO.

## Parent class output
To see the output from the parent class, add the following code to your script and run it.

```
s = Substitute(source_file, answer_file)
s.swap_words()
print(s.words)
```

Create the class Stars which is a child class of Substitute. Then override the swap_words method so that every third word is replaced by a series of *. If the word has three letters then it should be replaced with ***. The number of * should match the number of characters in the word. Write the new string to self.answer_file.

## Important
Keep the following things in mind as you write your code. Changes should only be made to the Stars class; do not alter the code for the file variables and the Substitute class.

- The source_file attribute represents the file you will read.
- The answer_file attribute represents the file to which you will write your new text.
- The string_to_list method converts the string (the text file) into a 2D list. Each inner list represents a sentence. The elements of each inner list are the words that make up that sentence.
- The list_to_string method converts the 2D list back into a string.
- When you override the swap_words methods, be sure to start with string_to_list and use list_to_string before writing to the file.
- The text used for this activity are the first four sentences of Jane Austen’s Pride and Prejudice.

# Solution

```
source_file = '/home/codio/workspace/code/polymorphism/text_1_exercise5.txt'
answer_file = '/home/codio/workspace/code/polymorphism/answer_exercise5.txt'

class Substitute:
  def __init__(self, source_file, answer_file):
    self.source_file = source_file
    self.answer_file = answer_file
    self.words = None

  def string_to_list(self):
    '''Read text file, turn it into a
    2D list of words for each line'''
    words = []
    with open(self.source_file, 'r') as file_object:
      lines = file_object.read().split('\n')
      for line in lines:
        words.append(line.split())
    self.words = words

  def list_to_string(self):
    '''Convert 2D list back into a
    string with newline characters'''
    lines = []
    for line in self.words:
      lines.append(' '.join(line))
    string = '\n'.join(lines)
    self.words = string

  def swap_words(self):
    self.string_to_list()
    for line in self.words:
      for i in range(len(line)):
        if (i + 1) % 5 == 0:
          word = line[i]
          line[i] = 'HELLO'
    self.list_to_string()

class Star(Substitute):
  def swap_words(self):
    self.string_to_list()
    for i in range(len(self.words)):
      for j in range(len(self.words[i])):
        if (j+1)%3==0:
          self.words[i][j]="*"*len(self.words[i][j])
    self.list_to_string()
    with open(self.answer_file, 'w') as file_object:
      file_object.write(self.words)

s = Star(source_file, answer_file)
s.swap_words()
```
