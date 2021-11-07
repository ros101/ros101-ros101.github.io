---
layout: notes
---
# Data sort using cards
Suppose you are sorting a set of cards. The right hand holds several cards which are sequentially sorted by numbers arranged from right to left, say for example, five cards with 10, 6, 5, 3, 2 arranged from right to left. Your left hand is picking up the top card from a pile of card deck. Now you insert the card that you have picked from the pile of deck into the right position within the right-hand cards, in a sorted order from right to left.

Write the instructions in a step by step manner. Note down even a minor step that you have taken to insert the left-hand card into a correct position within the set of right-hand cards so that the right-hand card set remains sorted from right to left.

## Solution
The data structure is a linked list where *head* points to the first card and every card points to the next one.
```
[2] -> [3] -> [5] -> [6] -> [10]
```
Insertion sort is the solution to insert the next card in the right position. The *insert* function returns the new head of the list.

1. if there are no cards, return the new card
2. else, if the new card precedes the current head, append the head to the new card and return the new card
3. else, if the new card follows the head and head is the last card, append the new cart to the head and return the head
4. else, put aside the head and call *insert* recursively. Append the result to head and return head.

In Python:
```
import random

class Card:
    ''' List element '''
    def __init__(self, value:int) -> None:
        self.value = value
        self.next = None

    def get_value(self) -> int:
        return self.value

    def get_next(self):
        return self.next
    
    def set_next(self, next) -> None:
        self.next = next

def insert(new_card:Card, head:Card) -> Card:
    ''' insert new_card and return the new head '''
    if head is None:
        # if there are no cards, return the new card
        return new_card
    elif new_card.get_value() < head.get_value():
        # add the card in front if it precedes the current slice
        new_card.set_next(head)
        return new_card
    elif head.get_next() is None:
        # add the card at the end if it's bigger than the last one
        head.set_next(new_card)
        return head
    else:
        # insert in the hand skipping the first card
        tmp = insert(new_card, head.get_next())
        # append to the first card
        head.set_next(tmp)
        return head

def print_hand(head:Card) -> None:
    ''' print the hand '''
    card = head
    while card is not None:
        print(card.get_value(),end='',)
        card=card.get_next()
        print(" " if card is not None else "\n",end='')

if __name__ == "__main__":
    # some test code
    cards = [i for i in range(1,11)]
    random.shuffle(cards)
    head:Card = None
    for i in range(0,10):
        next = Card(cards[i])
        print(format("inserting {value}".format(value = next.get_value())))
        head = insert(next, head)
        print_hand(head)
```
output
```
inserting 1
1
inserting 8
1 8
inserting 2
1 2 8
inserting 9
1 2 8 9
inserting 5
1 2 5 8 9
inserting 3
1 2 3 5 8 9
inserting 7
1 2 3 5 7 8 9
inserting 6
1 2 3 5 6 7 8 9
inserting 4
1 2 3 4 5 6 7 8 9
inserting 10
1 2 3 4 5 6 7 8 9 10
```