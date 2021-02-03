---
layout: default
title: Jump Table
parent: Blog
---

Here's a cool hack I came up with in ```C99``` to create a conditional jump table.

```c
// m - total condition states
// reduction from O(2^m) -> O(m) ops
// jumptables are faster as there is no branching
// added benefit of ordinally-non-sequential answers

unsigned int conditions[] = {
    1, // C1
    0, // C2 
    1  // C3
};
int answers[] = {1, 6, 5, 7, 9, 3, 6, 8};
int jump_table(){
    unsigned int conditional = 0;
    unsigned int n = sizeof(conditions)/sizeof(conditions[0]);
    for(unsigned int i=0;i<n;++i){
        conditional += 1 << i*conditions[i] : 0;
    }
    return answers[conditional];
}

```