---
source: https://en.wikipedia.org/wiki/Min-max_heap
fetched: 2026-06-19
---

Computer data structure 
| Min-max heap |
| --- |
| Type | binary tree/heap |
| Invented | 1986 |
| Invented by | M. D. Atkinson, J. R. Sack, N. Santoro, T. Strothotte |
| Time complexityinbig O notationOperationAverageWorst caseInsertO(log  n)O(log n)DeleteO(log  n)[1]O(log n)Space complexity | Time complexityinbig O notation | Operation | Average | Worst case | Insert | O(log  n) | O(log n) | Delete | O(log  n)[1] | O(log n) | Space complexity |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Insert | O(log  n) | O(log n) |
| Delete | O(log  n)[1] | O(log n) |
| Space complexity |

 

In [computer science](./Computer_science), a **min-max heap** is a complete [binary tree](./Binary_tree) [data structure](./Data_structure) which combines the usefulness of both a [min-heap](./Min-heap) and a [max-heap](./Max-heap), that is, it provides constant time retrieval and logarithmic time removal of both the minimum and maximum elements in it.[[2]](./Min-max_heap#cite_note-:0-2) This makes the min-max heap a very useful data structure to implement a [double-ended priority queue](./Double-ended_priority_queue). Like binary min-heaps and max-heaps, min-max heaps support logarithmic insertion and deletion and can be built in linear time.[[3]](./Min-max_heap#cite_note-3) Min-max heaps are often represented implicitly in an *array*;[[4]](./Min-max_heap#cite_note-:1-4) hence it's referred to as an [implicit data structure](./Implicit_data_structure).

 

The *min-max heap* property is: *each node at an even level in the tree is less than all of its descendants, while each node at an odd level in the tree is greater than all of its descendants*.[[4]](./Min-max_heap#cite_note-:1-4)

 

The structure can also be generalized to support other order-statistics operations efficiently, such as `find-median`, `delete-median`,[[2]](./Min-max_heap#cite_note-:0-2)`find(k)` (determine the *kth* smallest value in the structure) and the operation `delete(k)` (delete the *kth* smallest value in the structure), for any fixed value (or set of values) of *k*. These last two operations can be implemented in constant and logarithmic time, respectively. The notion of min-max ordering can be extended to other structures based on the max- or min-ordering, such as [leftist trees](./Leftist_tree), generating a new (and more powerful) class of data structures.[[4]](./Min-max_heap#cite_note-:1-4) A min-max heap can also be useful when implementing an external quicksort.[[5]](./Min-max_heap#cite_note-5)

 

## Description

 
- A min-max heap is a *complete binary tree* containing alternating *min* (or *even*) and *max*  (or *odd*) *levels*.  Even levels are for example 0, 2, 4, etc, and odd levels are respectively 1, 3, 5, etc. We assume in the next points that the root element is at the first level, i.e., 0.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/50/Min-max_heap.jpg/330px-Min-max_heap.jpg)](./File:Min-max_heap.jpg)Example of Min-max heap 
- Each node in a min-max heap has a data member (usually called *key*) whose value is used to determine the order of the node in the min-max heap.
- The *root* element is the *smallest* element in the min-max heap.
- One of the two elements in the second level, which is a max (or odd) level, is the greatest element in the min-max heap
- Let     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) be any node in a min-max heap. 

- If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is on a min (or even) level, then     x . k e y   {\displaystyle x.key}  ![{\displaystyle x.key}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa4ff86d58158ae2af84626c9e3b37531082db5e) is the minimum key among all keys in the subtree with root     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4).
- If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is on a max (or odd) level, then     x . k e y   {\displaystyle x.key}  ![{\displaystyle x.key}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa4ff86d58158ae2af84626c9e3b37531082db5e) is the maximum key among all keys in the subtree with root     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4).

- A node on a min (max) level is called a min (max) node.

 

A *max-min heap* is defined analogously; in such a heap, the maximum value is stored at the root, and the smallest value is stored at one of the root's children.[[4]](./Min-max_heap#cite_note-:1-4)

 

## Operations

 

In the following operations we assume that the min-max heap is represented in an array `A[1..N]`; The     i t h   {\displaystyle ith}  ![{\displaystyle ith}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d66e814a28eb25bb9b903f46c50fa4c8a81e9ff5) location in the array will correspond to a node located on the level     ⌊ ⌊   log  2   ⁡ ⁡  i ⌋ ⌋    {\displaystyle \lfloor \log _{2}i\rfloor }  ![{\displaystyle \lfloor \log _{2}i\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/a2aff90b7b004b98b88d5bc2177ea410d9a6d852) in the heap.

 

### Build

 

Creating a min-max heap is accomplished by an adaptation of Floyd's linear-time heap construction algorithm, which proceeds in a bottom-up fashion.[[4]](./Min-max_heap#cite_note-:1-4) A typical Floyd's *build-heap* algorithm[[6]](./Min-max_heap#cite_note-6) goes as follows:

 
```
function FLOYD-BUILD-HEAP(h):
    for each index i from 
  
    
      
        ⌊
        l
        e
        n
        g
        t
        h
        (
        h
        )
        
          /
        
        2
        ⌋
      
    
    {\displaystyle \lfloor length(h)/2\rfloor }
  
down to 1 do:
        push-down(h, i)
    return h
```
 

In this function, *h* is the initial array, whose elements may not be ordered according to the min-max heap property. The `push-down` operation (which sometimes is also called *heapify*) of a min-max heap is explained next.

 

### Push Down

 

The `push-down` algorithm (or `trickle-down` as it is called in [[4]](./Min-max_heap#cite_note-:1-4)
) is as follows:

 
```
function PUSH-DOWN(h, i):
    if i is on a min level then:
        PUSH-DOWN-MIN(h, i)
    else:
        PUSH-DOWN-MAX(h, i)
    endif
```
 

#### Push Down Min

 
```
function PUSH-DOWN-MIN(h, i):
    if i has children then:
        m := index of the smallest child or grandchild of i
        if m is a grandchild of i then:
            if h[m] < h[i] then:
                swap h[m] and h[i]
                if h[m] > h[parent(m)] then:
                    swap h[m] and h[parent(m)]
                endif
                PUSH-DOWN(h, m)
            endif
        else if h[m] < h[i] then:
            swap h[m] and h[i]
        endif 
    endif
```
 

#### Push Down Max

 

The algorithm for `push-down-max` is identical to that for push-down-min, but with all of the comparison operators reversed.

 
```
function PUSH-DOWN-MAX(h, i):
    if i has children then:
        m := index of the largest child or grandchild of i
        if m is a grandchild of i then:
            if h[m] > h[i] then:
                swap h[m] and h[i]
                if h[m] < h[parent(m)] then:
                    swap h[m] and h[parent(m)]
                endif
                PUSH-DOWN(h, m)
            endif
        else if h[m] > h[i] then:
            swap h[m] and h[i]
        endif 
    endif
```
 

#### Iterative Form

 

As the recursive calls in `push-down-min` and `push-down-max` are in tail position, these functions can be trivially converted to purely iterative forms executing in constant space:

 
```
function PUSH-DOWN-ITER(h, m):
    while m has children then:
        i := m
        if i is on a min level then:
            m := index of the smallest child or grandchild of i
            if h[m] < h[i] then:
                swap h[m] and h[i]
                if m is a grandchild of i then:
                    if h[m] > h[parent(m)] then:
                        swap h[m] and h[parent(m)]
                    endif
                else
                    break
                endif
            else
                break 
            endif
        else:
            m := index of the largest child or grandchild of i
            if h[m] > h[i] then:
                swap h[m] and h[i]
                if m is a grandchild of i then:
                    if h[m] < h[parent(m)] then:
                        swap h[m] and h[parent(m)]
                    endif
                else
                    break
                endif
            else
                break 
            endif
        endif
    endwhile
```
 

### Insertion

 

To add an element to a min-max heap perform following operations:

 
1. Append the required key to (the end of) the array representing the min-max heap. This will likely break the min-max heap properties, therefore we need to adjust the heap.
2. Compare the new key to its parent:

1. If it is found to be less (greater) than the parent, then it is surely less (greater) than all other nodes on max (min) levels that are on the path to the root of heap. Now, just check for nodes on min (max) levels.
2. The path from the new node to the root (considering only min (max) levels) should be in a descending (ascending) order as it was before the insertion. So, we need to make a binary insertion of the new node into this sequence. Technically it is simpler to swap the new node with its parent while the parent is greater (less).

 

This process is implemented by calling the `push-up` algorithm described below on the index of the newly-appended key.

 

### Push Up

 

The `push-up` algorithm (or `bubble-up` as it is called in [[7]](./Min-max_heap#cite_note-7)
) is as follows:

 
```
function PUSH-UP(h, i):
    if i is not the root then:
        if i is on a min level then:
            if h[i] > h[parent(i)] then:
                swap h[i] and h[parent(i)]
                PUSH-UP-MAX(h, parent(i))
            else:
                PUSH-UP-MIN(h, i)
            endif
        else:
            if h[i] < h[parent(i)] then:
                swap h[i] and h[parent(i)]
                PUSH-UP-MIN(h, parent(i))
            else:
                PUSH-UP-MAX(h, i)
            endif
        endif
    endif
```
 

#### Push Up Min

 
```
function PUSH-UP-MIN(h, i):
    if i has a grandparent and h[i] < h[grandparent(i)] then:
        swap h[i] and h[grandparent(i)]
        PUSH-UP-MIN(h, grandparent(i))
    endif
```
 

#### Push Up Max

 

As with the `push-down` operations, `push-up-max` is identical to `push-up-min`, but with comparison operators reversed:

 
```
function PUSH-UP-MAX(h, i):
    if i has a grandparent and h[i] > h[grandparent(i)] then:
        swap h[i] and h[grandparent(i)]
        PUSH-UP-MAX(h, grandparent(i))
    endif
```
 

#### Iterative Form

 

As the recursive calls to `push-up-min` and `push-up-max` are in tail position, these functions also can be trivially converted to purely iterative forms executing in constant space:

 
```
function PUSH-UP-MIN-ITER(h, i):
    while i has a grandparent and h[i] < h[grandparent(i)] then:
        swap h[i] and h[grandparent(i)]
        i := grandparent(i)
    endwhile
```
 

#### Example

 

Here is one example for inserting an element to a Min-Max Heap.

 

Say we have the following min-max heap and want to insert a new node with value 6.

 [![Example of Min-max heap](//upload.wikimedia.org/wikipedia/commons/thumb/5/50/Min-max_heap.jpg/500px-Min-max_heap.jpg)](./File:Min-max_heap.jpg) 

Initially, node 6 is inserted as a right child of the node 11. 6 is less than 11, therefore it is less than all the nodes on the max levels (41), and we need to check only the min levels (8 and 11). We should swap the nodes 6 and 11 and then swap 6 and 8. So, 6 gets moved to the root position of the heap, the former root 8 gets moved down to replace 11, and 11 becomes a right child of 8.

 

Consider adding the new node 81 instead of 6. Initially, the node is inserted as a right child of the node 11. 81 is greater than 11, therefore it is greater than any node on any of the min levels (8 and 11). Now, we only need to check the nodes on the max levels (41) and make one swap.

 

### Find Minimum

 

The minimum node (or a minimum node in the case of duplicate keys) of a Min-Max Heap is always located at the root. Find Minimum is thus a trivial constant time operation which simply returns the roots.

 

### Find Maximum

 

The maximum node (or a maximum node in the case of duplicate keys) of a Min-Max Heap that contains more than one node is always located on the first max level--i.e., as one of the immediate children of the root. Find Maximum thus requires at most one comparison, to determine which of the two children of the root is larger, and as such is also a constant time operation. If the Min-Max heap contains one node then that node is the maximum node.

 

### Remove Minimum

 

Removing the minimum is just a special case of removing an arbitrary node whose index in the array is known. In this case, the last element of the array is removed (reducing the length of the array) and used to replace the root, at the head of the array. `push-down` is then called on the root index to restore the heap property in     O (  log  2   ⁡ ⁡  ( n ) )   {\displaystyle O(\log _{2}(n))}  ![{\displaystyle O(\log _{2}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bca0626f9c0b4e0eef3953d0e11471c15c807079)time.

 

### Remove Maximum

 

Removing the maximum is again a special case of removing an arbitrary node with known index. As in the Find Maximum operation, a single comparison is required to identify the maximal child of the root, after which it is replaced with the final element of the array and `push-down` is then called on the index of the replaced maximum to restore the heap property.

 

## Extensions

 

The min-max-median heap is a variant of the min-max heap, suggested in the original publication on the structure, that supports the operations of an [order statistic tree](./Order_statistic_tree).

 

## References

  
1. [↑](./Min-max_heap#cite_ref-How_to_perform_a_general_deletion_operation_on_a_min-max_heap?_1-0) Mischel. ["Jim"](https://stackoverflow.com/a/39393768). *Stack Overflow*. Retrieved 8 September 2016.
2. [1](./Min-max_heap#cite_ref-:0_2-0) [2](./Min-max_heap#cite_ref-:0_2-1) [ATKINSON, M. D](./Michael_D._Atkinson); [SACK, J.-R](./Jörg-Rüdiger_Sack); SANTORO, N.; STROTHOTTE, T. (1986). Munro, Ian (ed.). ["Min-Max Heaps and Generalized Priority Queues"](http://www.akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/02/Atkinson86.pdf) (PDF). *Communications of the ACM*. **29** (10): 996–1000. [doi](./Doi_(identifier)):[10.1145/6617.6621](https://doi.org/10.1145%2F6617.6621). [S2CID](./S2CID_(identifier)) [3090797](https://api.semanticscholar.org/CorpusID:3090797).
3. [↑](./Min-max_heap#cite_ref-3) [ATKINSON, M. D](./Michael_D._Atkinson); [SACK, J.-R](./Jörg-Rüdiger_Sack); SANTORO, N.; STROTHOTTE, T. (1986). Munro, Ian (ed.). ["Min-Max Heaps and Generalized Priority Queues"](http://www.akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/02/Atkinson86.pdf) (PDF). *Communications of the ACM*. **29** (10): 996–1000. [doi](./Doi_(identifier)):[10.1145/6617.6621](https://doi.org/10.1145%2F6617.6621). [S2CID](./S2CID_(identifier)) [3090797](https://api.semanticscholar.org/CorpusID:3090797).
4. [1](./Min-max_heap#cite_ref-:1_4-0) [2](./Min-max_heap#cite_ref-:1_4-1) [3](./Min-max_heap#cite_ref-:1_4-2) [4](./Min-max_heap#cite_ref-:1_4-3) [5](./Min-max_heap#cite_ref-:1_4-4) [6](./Min-max_heap#cite_ref-:1_4-5) [ATKINSON, M. D](./Michael_D._Atkinson); [SACK, J.-R](./Jörg-Rüdiger_Sack); SANTORO, N.; STROTHOTTE, T. (1986). Munro, Ian (ed.). ["Min-Max Heaps and Generalized Priority Queues"](http://www.akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/02/Atkinson86.pdf) (PDF). *Communications of the ACM*. **29** (10): 996–1000. [doi](./Doi_(identifier)):[10.1145/6617.6621](https://doi.org/10.1145%2F6617.6621). [S2CID](./S2CID_(identifier)) [3090797](https://api.semanticscholar.org/CorpusID:3090797).
5. [↑](./Min-max_heap#cite_ref-5) Gonnet, Gaston H.; Baeza-Yates, Ricardo (1991). *Handbook of Algorithms and Data Structures: In Pascal and C*. Addison-Wesley Publishing Company. [ISBN](./ISBN_(identifier)) [0201416077](./Special:BookSources/0201416077).
6. [↑](./Min-max_heap#cite_ref-6) K. Paparrizos, Ioannis (2011). "A tight bound on the worst-case number of comparisons for Floyd's heap construction algorithm". [arXiv](./ArXiv_(identifier)):[1012.0956](https://arxiv.org/abs/1012.0956). [Bibcode](./Bibcode_(identifier)):[2010arXiv1012.0956P](https://ui.adsabs.harvard.edu/abs/2010arXiv1012.0956P). `{{cite journal}}`: Cite journal requires `|journal=` ([help](./Help:CS1_errors#missing_periodical))
7. [↑](./Min-max_heap#cite_ref-7) [ATKINSON, M. D](./Michael_D._Atkinson); [SACK, J.-R](./Jörg-Rüdiger_Sack); SANTORO, N.; STROTHOTTE, T. (1986). Munro, Ian (ed.). ["Min-Max Heaps and Generalized Priority Queues"](http://www.akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/02/Atkinson86.pdf) (PDF). *Communications of the ACM*. **29** (10): 996–1000. [doi](./Doi_(identifier)):[10.1145/6617.6621](https://doi.org/10.1145%2F6617.6621). [S2CID](./S2CID_(identifier)) [3090797](https://api.semanticscholar.org/CorpusID:3090797).

 
-