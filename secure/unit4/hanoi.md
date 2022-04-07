---
layout: notes
---
# Towers of Hanoi

```python
TOWER_A = 'A'
TOWER_B = 'B'
TOWER_C = 'C'

def print_towers(towers):
    for i in range(len(towers[TOWER_A])-1, -1, -1):
        print(str(towers[TOWER_A][i]) + ' ' + str(towers[TOWER_B][i]) + ' ' + str(towers[TOWER_C][i]))
    print('-----')

def update(towers, source, target):
    def find_last_index(peg):
        if(peg[0] == 0):
            return -1
        i = 0
        while peg[i] != 0:
            if len(peg) > i + 1:
                i = i + 1
            else:
                return i
        return i - 1
    index_source = find_last_index(towers[source])
    index_target = find_last_index(towers[target]) + 1
    towers[target][index_target] = towers[source][index_source]
    towers[source][index_source] = 0
    print_towers(towers)

def move(source, target, support, disks, towers):
    if(disks == 1):    
        print('from {source} to {target}'.format(source = source, target = target))
        update(towers, source, target)
    else:
        move(source, support, target, disks - 1, towers)
        move(source, target, support, 1, towers)
        move(support, target, source, disks - 1, towers)

if __name__ == "__main__":
    disks = 3
    towers = {
        TOWER_A: [i for i in range(disks, 0, -1)],
        TOWER_B: [0 for _ in range(0, disks)],
        TOWER_C: [0 for _ in range(0, disks)]
    }
    print_towers(towers)
    move(TOWER_A, TOWER_B, TOWER_C, disks, towers)
```

The output will be:

```
1 0 0
2 0 0
3 0 0
-----
from A to B
0 0 0
2 0 0
3 1 0
-----
from A to C
0 0 0
0 0 0
3 1 2
-----
from B to C
0 0 0
0 0 1
3 0 2
-----
from A to B
0 0 0
0 0 1
0 3 2
-----
from C to A
0 0 0
0 0 0
1 3 2
-----
from C to B
0 0 0
0 2 0
1 3 0
-----
from A to B
0 1 0
0 2 0
0 3 0
-----
```
