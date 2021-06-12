---
layout: default
title: Diagonally
parent: Blog
---

# Diagonally Traversing an Array 
{: .no_toc }

Consider the array

```
[[ a00  a01  a02  a03  a04  a05 ],
 [ a10  a11  a12  a13  a14  a15 ],
 [ a20  a21  a22  a23  a24  a25 ],
 [ a30  a31  a32  a33  a34  a35 ],
 [ a40  a41  a42  a43  a44  a45 ],
 [ a50  a51  a52  a53  a54  a55 ]
```

let's say we want to traverse is diagonally as such 

```
diagonal -5:  a50
diagonal -4:  a40 -> a51
diagonal -3:  a30 -> a41 -> a52
diagonal -2:  a20 -> a31 -> a42 -> a53
diagonal -1:  a10 -> a21 -> a32 -> a43 -> a54
diagonal -0:  a00 -> a11 -> a22 -> a33 -> a44 -> a55
diagonal  1:  a01 -> a12 -> a23 -> a34 -> a45
diagonal  2:  a02 -> a13 -> a24 -> a35
diagonal  3:  a03 -> a14 -> a25
diagonal  4:  a04 -> a15
diagonal  5:  a05
```


I've had to think about this question myself sometime back and one of the things that I realize is this
traversals of any kind in a 2D grid structure like this essentially boils down to the line or curve equations for the points 


[Tl:DR convert diagonal to straight line by shearing + simplify diagonal traversal]


## Math


for clarity I will leave out the a and just use numbers.
It may help to visualize if you turn the screen so y is facing up
(xcoord,ycoord)

```
--------------------------------------> (+y axis)
|(0,0) (0,1) (0,2) (0,3) (0,4) (0,5)
|(1,0) (1,1) (1,2) (1,3) (1,4) (1,5)(1,6)[assume]
|(2,0) (2,1) (2,2) (2,3) (2,4) (2,5)
|(3,0) (3,1) (3,2) (3,3) (3,4) (3,5)
|(4,0) (4,1) (4,2) (4,3) (4,4) (4,5)
|(5,0) (5,1) (5,2) (5,3) (5,4) (5,5)
|      (6,1)[assume] 
v
(+x axis)
```
you want a diagonal traversal (5,0)->(4,0)->(5,1)->(3,0)->(4,1)->(5,2) ... so on
this is bascially drawing 45 degree straight lines 

m is the slope
c is y-intercept - easy way to understand is that setting x=0 gives y=c ie c is independent of x
x,y are the respective coordinates

```y = mx + c [eq1]```

take any two points on the same diagonal for example
```
[x1,y1](3,0) and [x2,y2](5,2)

m = (y2-y1)/(x2-x1) = (2-0)/(5-3) = 2/(2) = 1

lets substitute of of the points say [x2,y2](5,2)

2 = 1*5 + c
c = 2-3 = -1

c = -1 [eq2]
y = x - 1 [eq3]

```

let's do this for a bunch of other diagonals specially the ones towards the start and end - we don't need to calculate m again as all lines have the same slope of 
```m=1``` we're just interested in seeing how c changes as we traverse through the matrix

```
for diagonal [x1,y1](5,0) [x2,y2](6,1)
y = mx + c
1 = 1*(6) + c
c = 1-6 = -5 [eq4]

for diagonal [x1,y1](4,0) [x2,y2](5,1)
y = mx + c
1 = 1*(5) + c
c = 1-5 = -4 [eq5]

... so on untill

for diagonal [x1,y1](0,4) [x2,y2](1,5)
y = mx + c
5 = 1*(1) + c
c = 5-1 = 4 [eq6]

for diagonal [x1,y1](0,5) [x2,y2](1,6)
y = mx + c
6 = 1*(1) + c
c = 6-1 = 5 [eq7]


we see a pattern here 

c [-5,-4...,4,5] 

[NOTE]
c = -5  depends on the number of rows
c = 5   depends on the number of cols   



```

## Code


Now that we understand what's occuring let's buld the code i'm going to use C
```cplusplus
// let n_rows : number of rows (6) here
// let n_cols : number of cols (6) here

#include "stdio.h"

int main(int argc, char** argv){

    int a[6][6] = 
        {
            {0,     1,      2,      3,      4,      5},
            {6,     7,      8,      9,      10,     11},
            {12,    13,     14,     15,     16,     17},
            {18,    19,     20,     21,     22,     23},
            {24,    25,     26,     27,     28,     29},
            {30,    31,     32,     33,     34,     35},
        };

    int n_rows = 6;
    int n_cols = 6;

    int n_diagonal_count;

    int x=0,y=0,c=0;

    for(c = -(n_rows-1); c <= (n_cols-1); ++c){
    // now we get our varying c which allows us to move the line

    // the xvariable for these diagonals goes down from (n_rows-1) to 0
        for(y = 0; y <= n_cols-1 ; ++y){

            x = y - c;
            
            // do bounds checking 
            if(x>= 0 && x<= (n_rows-1)){
                printf("%d ",a[x][y]);
            }

        }
    }
    return 0;
}

```

## Some brainstorming

so this really simplifed the diagonal traversal 
our next step is to think what if the matrix is not 6x6

what is if is 10000x1000 and your machine can only fit 10x10 into memory 


let's see how we can optmize this further : basic idea is to start streaming the data in chunk that you need and then discard them 
consider the following grid 6x5 i'm picking arbitrarily
now each of the boxes correspond to a 3x3 region in memory 

so that is total of 6*3*5*3 = 270 elements in total
lets's say my budget allows me to only store 9 elements at a time and space for a small number of constant variables to keep track of state let's number the grid

[full data grid that needs to be made into chunks]

```

---.---.---.---.---.
|15|20 |24 |27 |29 |
---.---.---.---.---.
|10|16 |21 |25 |28 |
---.---.---.---.---.
|6 |11 |17 |22 |26 |
---.---.---.---.---.
|3 | 7 |12 |18 |23 |
---.---.---.---.---.
|1 | 4 | 8 |13 |19 |
---.---.---.---.---.
|0 |2  | 5 | 9 |14 |
---.---.---.---.---.
```

so if you want to diagonally traverse the 270 elements - we would need to diagonall traverse all the 30 chunks as well
```

[a single chunk]
.---.---.---.
| g | h | i |
.---.---.---.
| d | e | f |
.---.---.---.
| a | b | c |
.---.---.---.
```
so the traversal fashion will be hierarchical


but here's the deal - if memory isn't a contraint or you do have a setup to steam data very fast 

here's a very neat way to do diagonal traversal and maximize cache hits

this would take O((n_rows + n_cols) * n_rows) space

```
        .---.---.---.
  *   * | g | h | i |
    .---.---.---.---.
  * | d | e | f | $
.---.---.---.---.
| a | b | c | $   $
.---.---.---.

* are empty spots with some illegal value
$ are possible values from future chunks


let this be your new matrix - just traverse each column top to bottom - it is better to vertically flip the matrix as well to maximize leagal hits

.---.---.---.
| a | b | c | $   $
.---.---.---.---.
  * | d | e | f | $
    .---.---.---.---.
  *   * | g | h | i |
        .---.---.---.


this above 'shear' technique will increase cache hits 
at the expense of requiring some data preprocessing and streaming



[full data grid that needs to be made into chunks]

---.---.---.---.---.
|15|20 |24 |27 |29 |
---.---.---.---.---.
|10|16 |21 |25 |28 |
---.---.---.---.---.
|6 |11 |17 |22 |26 |
---.---.---.---.---.
|3 | 7 |12 |18 |23 |
---.---.---.---.---.
|1 | 4 | 8 |13 |19 |
---.---.---.---.---.
|0 |2  | 5 | 9 |14 |
---.---.---.---.---.


coming back to the grid 
diagonal_ids[] = [diag for d in range(-(n_rows-1),(n_cols-1))]

each one of the chunks can be separately processed based on the diagonal ID's
```

```
Some sketch of a pseudo code

1. use the shearing mechanism to increase cache hits
    you will have stream data and concatenate sheared blocks loading memory in bigger chunks into ram is fast than smaller chunks
    caches draw from the memory so it'll work fine as long as we can stream sheared chunks

2. calculate diagonal numbers
    y = chunk_y + offset
    x = chunk_x + offset
    diag_id = (y-x) + (n_rows-1)

3. create a threadpool based on the number of available threads

4. launch separate threads and have them process the columns 

```

## Summary
1. calculate diagonal indices in a simple manner
2. shear data
3. shearing converts problem to sequential access
4. sequential access == cache is happy
