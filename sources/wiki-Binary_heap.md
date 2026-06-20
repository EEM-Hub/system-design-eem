---
source: https://en.wikipedia.org/wiki/Binary_heap
fetched: 2026-06-19
---

Variant of heap data structure 
| Binary (min) heap |
| --- |
| Type | binary tree/heap |
| Invented | 1964 |
| Invented by | J. W. J. Williams |
| Time complexityinbig O notationOperationAverageWorst caseInsertO(1)O(logn)Find-minO(1)O(1)Delete-minO(logn)O(logn)Decrease-keyO(logn)O(logn)MergeO(n)O(n)Space complexitySpaceO(n)O(n) | Time complexityinbig O notation | Operation | Average | Worst case | Insert | O(1) | O(logn) | Find-min | O(1) | O(1) | Delete-min | O(logn) | O(logn) | Decrease-key | O(logn) | O(logn) | Merge | O(n) | O(n) | Space complexity | Space | O(n) | O(n) |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Insert | O(1) | O(logn) |
| Find-min | O(1) | O(1) |
| Delete-min | O(logn) | O(logn) |
| Decrease-key | O(logn) | O(logn) |
| Merge | O(n) | O(n) |
| Space complexity |
| Space | O(n) | O(n) |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/38/Max-Heap.svg/250px-Max-Heap.svg.png)](./File:Max-Heap.svg)Example of a complete binary max-heap [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/69/Min-heap.png/250px-Min-heap.png)](./File:Min-heap.png)Example of a complete binary min heap 

A **binary heap** is a [heap](./Heap_(data_structure)) [data structure](./Data_structure) that takes the form of a [binary tree](./Binary_tree). Binary heaps are a common way of implementing [priority queues](./Priority_queue).[[1]](./Binary_heap#cite_note-clrs-1): 162–163  The binary heap was introduced by [J. W. J. Williams](./J._W._J._Williams) in 1964 as a data structure for implementing [heapsort](./Heapsort).[[2]](./Binary_heap#cite_note-2)

 

A binary heap is defined as a binary tree with two additional constraints:[[3]](./Binary_heap#cite_note-3)

 
- Shape property: a binary heap is a *[complete binary tree](./Complete_binary_tree)*; that is, all levels of the tree, except possibly the last one (deepest) are fully filled, and, if the last level of the tree is not complete, the nodes of that level are filled from left to right.
- Heap property: the key stored in each node is either greater than or equal to (≥) (or less than or equal to (≤)) the keys in the node's children, according to some [total order](./Total_order).

 

Heaps where the parent key is greater than or equal to (≥) the child keys are called *max-heaps*; those where it is less than or equal to (≤) are called *min-heaps*. Efficient (that is, [logarithmic time](./Logarithmic_time)) algorithms are known for the two operations needed to implement a priority queue on a binary heap:

 
- Inserting an element;
- Removing the smallest or largest element from (respectively) a min-heap or max-heap.

 

Binary heaps are also commonly employed in the [heapsort](./Heapsort) [sorting algorithm](./Sorting_algorithm), which is an in-place algorithm as binary heaps can be implemented as an [implicit data structure](./Implicit_data_structure), storing keys in an array and using their relative positions within that array to represent child–parent relationships.

 

## Heap operations

 

Both the insert and remove operations modify the heap to preserve the shape property first, by adding or removing from the end of the heap. Then the heap property is restored by traversing up or down the heap. Both operations take O(log *n*) time.

 

### Insert

 

To insert an element to a heap, we perform the following steps:

 
1. Add the element to the bottom level of the heap at the leftmost open space.
2. Compare the added element with its parent; if they are in the correct order, stop.
3. If not, swap the element with its parent and return to the previous step.

 

Steps 2 and 3, which restore the heap property by comparing and possibly swapping a node with its parent, are called *the up-heap* operation (also known as *bubble-up*, *percolate-up*,  not a typo: *sift-up*, *trickle-up*, *swim-up*, *heapify-up*, *cascade-up*, or *fix-up*).

 

The number of operations required depends only on the number of levels the new element must rise to satisfy the heap property. Thus, the insertion operation has a worst-case time complexity of O(log *n*). For a random heap, and for repeated insertions, the insertion operation has an average-case complexity of O(1).[[4]](./Binary_heap#cite_note-4)[[5]](./Binary_heap#cite_note-5)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cf/InsertingIntoBinaryHeap.gif/330px-InsertingIntoBinaryHeap.gif)](./File:InsertingIntoBinaryHeap.gif)A short animation depicting adding a value to a binary max-heap. 

The following animation depicts an example of binary heap insertion. It begins by inserting 15 into the heap at the left-most empty entry on the next available row. However, the heap property is violated since 15 > 8, so we need to swap the 15 and the 8. Even after this swap, the heap property is still violated since 15 > 11, so we need to swap again. The heap property is now satisfied, so the resulting binary tree is a valid max-heap. There is no need to check the left child after this final step: at the start, the max-heap was valid, meaning the root was already greater than its left child, so replacing the root with an even greater value will maintain the property that each node is greater than its children (11 > 5; if 15 > 11, and 11 > 5, then 15 > 5, because of the [transitive relation](./Transitive_relation)).

 

### Extract

 

The procedure for deleting the root from the heap (effectively extracting the maximum element in a max-heap or the minimum element in a min-heap) while retaining the heap property is as follows:

 
1. Replace the root of the heap with the last element on the last level.
2. Compare the new root with its children; if they are in the correct order, stop.
3. If not, swap the element with one of its children and return to the previous step. (Swap with its smaller child in a min-heap and its larger child in a max-heap.)

 

Steps 2 and 3, which restore the heap property by comparing and possibly swapping a node with one of its children, are called the *down-heap* (also known as *bubble-down*, *percolate-down*,  not a typo: *sift-down*, *sink-down*, *trickle down*, *heapify-down*, *cascade-down*, *fix-down*, *extract-min* or *extract-max*, or simply *heapify*) operation.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/28/ExtractingFromBinaryHeap.gif/330px-ExtractingFromBinaryHeap.gif)](./File:ExtractingFromBinaryHeap.gif)A short animation depicting extracting a value from a binary max-heap. 

So, if we have the same max-heap as before, we remove the 11 and replace it with the 4. Now the heap property is violated since 8 is greater than 4. In this case, swapping the two elements, 4 and 8, is enough to restore the heap property and we need not swap elements further.

 

The downward-moving node is swapped with the *larger* of its children in a max-heap (in a min-heap it would be swapped with its smaller child), until it satisfies the heap property in its new position. This functionality is achieved by the **Max-Heapify** function as defined below in [pseudocode](./Pseudocode) for an [array](./Array_data_structure)-backed heap *A* of length *length*(*A*). *A* is indexed starting at 1.

 
```
// Perform a down-heap or heapify-down operation for a max-heap
// A: an array representing the heap, indexed starting at 1
// i: the index to start at when heapifying down
Max-Heapify(A, i):
    left ← 2×i
    right ← 2×i + 1
    largest ← i
    
    if left ≤ length(A) and A[left] > A[largest] then:
        largest ← left
    if right ≤ length(A) and A[right] > A[largest] then:
        largest ← right
    
    if largest ≠ i then:
        swap A[i] and A[largest]
        Max-Heapify(A, largest)
```
 

For the above algorithm to correctly re-heapify the array, no nodes besides the node at index *i* and its two direct children can violate the heap property. The down-heap operation (without the preceding swap) can also be used to modify the value of the root, even when an element is not being deleted.

 

In the worst case, the new root has to be swapped with its child on each level until it reaches the bottom level of the heap, meaning that the delete operation has a time complexity relative to the height of the tree, or O(log *n*).

 

### Insert then extract

 

Inserting an element then extracting from the heap can be done more efficiently than simply calling the insert and extract functions defined above, which would involve both an `upheap` and `downheap` operation. Instead, we can do just a `downheap` operation, as follows:

 
1. Compare whether the item we're pushing or the peeked top of the heap is greater (assuming a max heap)
2. If the root of the heap is greater:

1. Replace the root with the new item
2. Down-heapify starting from the root

3. Else, return the item we're pushing

 

[Python](./Python_(programming_language)) provides such a function for insertion then extraction called "heappushpop", which is paraphrased below.[[6]](./Binary_heap#cite_note-6)[[7]](./Binary_heap#cite_note-7) The heap array is assumed to have its first element at index 1.

 
```
// Push a new item to a (max) heap and then extract the root of the resulting heap. 
// heap: an array representing the heap, indexed at 1
// item: an element to insert
// Returns the greater of the two between item and the root of heap.
Push-Pop(heap: List<T>, item: T) -> T:
    if heap is not empty and heap[1] > item then:  // < if min heap
        swap heap[1] and item
        _downheap(heap starting from index 1)
    return item
```
 

A similar function can be defined for popping and then inserting, which in Python is called "heapreplace":

 
```
// Extract the root of the heap, and push a new item 
// heap: an array representing the heap, indexed at 1
// item: an element to insert
// Returns the current root of heap
Replace(heap: List<T>, item: T) -> T:
    swap heap[1] and item
    _downheap(heap starting from index 1)
    return item
```
 

### Search

 

Finding an arbitrary element takes O(n) time.

 

This can be easily proved by considering that the heap is not sorted so we need to look through the whole tree to find the target element.

 

### Delete

 

Deleting an arbitrary element can be done as follows:

 
1. Find the index     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) of the element we want to delete
2. Swap this element with the last element. Remove the last element after the swap.
3. Down-heapify or up-heapify to restore the heap property. In a max-heap (min-heap), up-heapify is only required when the new key of element     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is greater (smaller) than the previous one because only the heap-property of the parent element might be violated. Assuming that the heap-property was valid between element     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) and its children before the element swap, it can't be violated by a now larger (smaller) key value. When the new key is less (greater) than the previous one then only a down-heapify is required because the heap-property might only be violated in the child elements.

 

### Decrease or increase key

  section linked from [[Reheapification]]  

The decrease key operation replaces the value of a node with a given value with a lower value, and the increase key operation does the same but with a higher value. This involves finding the node with the given value, changing the value, and then down-heapifying or up-heapifying to restore the heap property.

 

Decrease key can be done as follows:

 
1. Find the index of the element we want to modify
2. Decrease the value of the node
3. Down-heapify (assuming a max heap) to restore the heap property

 

Increase key can be done as follows:

 
1. Find the index of the element we want to modify
2. Increase the value of the node
3. Up-heapify (assuming a max heap) to restore the heap property

 

## Building a heap

 

Building a heap from an array of n input elements can be done by starting with an empty heap, then successively inserting each element. This approach, called Williams' method after the inventor of binary heaps, is easily seen to run in *O*(*n* log *n*) time: it performs n insertions at *O*(log *n*) cost each.[[a]](./Binary_heap#cite_note-9)

 

However, Williams' method is suboptimal. A faster method (due to [Floyd](./Robert_W._Floyd)[[8]](./Binary_heap#cite_note-heapbuildjalg-8)) starts by arbitrarily putting the elements on a binary tree, respecting the shape property (the tree could be represented by an array, see below). Then starting from the lowest level and moving upwards, sift the root of each subtree downward as in the deletion algorithm until the heap property is restored. More specifically if all the subtrees starting at some height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) have already been "heapified" (the bottommost level corresponding to     h = 0   {\displaystyle h=0}  ![{\displaystyle h=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffe239e1050529410001cc1c0b3245945bc69709)), the trees at height     h + 1   {\displaystyle h+1}  ![{\displaystyle h+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d6bdac90f1b229b8d6c70a3f207926e61c5c68f3) can be heapified by sending their root down along the path of maximum valued children when building a max-heap, or minimum valued children when building a min-heap. This process takes     O ( h )   {\displaystyle O(h)}  ![{\displaystyle O(h)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/08b2b7b64f0a9e9848ecd3a114cc7dcc8ca6179d) operations (swaps) per node. In this method most of the heapification takes place in the lower levels. Since the height of the heap is     ⌊ ⌊  log ⁡ ⁡  n ⌋ ⌋    {\displaystyle \lfloor \log n\rfloor }  ![{\displaystyle \lfloor \log n\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/2691a5620da37c1f740a04a8fd226072143455c9), the number of nodes at height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) is     ≤ ≤     2  ⌊ ⌊  log ⁡ ⁡  n ⌋ ⌋     2  h     ≤ ≤    n  2  h       {\displaystyle \leq {\frac {2^{\lfloor \log n\rfloor }}{2^{h}}}\leq {\frac {n}{2^{h}}}}  ![{\displaystyle \leq {\frac {2^{\lfloor \log n\rfloor }}{2^{h}}}\leq {\frac {n}{2^{h}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5051ad1ea862f8357779fc9ad08e03be88ec7fbf). Therefore, the cost of heapifying all subtrees is:

          ∑ ∑   h = 0   ⌊ ⌊  log ⁡ ⁡  n ⌋ ⌋      n  2  h     O ( h )    = O  (  n  ∑ ∑   h = 0   ⌊ ⌊  log ⁡ ⁡  n ⌋ ⌋      h  2  h      )        = O  (  n  ∑ ∑   h = 0   ∞ ∞      h  2  h      )        = O ( n )       {\displaystyle {\begin{aligned}\sum _{h=0}^{\lfloor \log n\rfloor }{\frac {n}{2^{h}}}O(h)&=O\left(n\sum _{h=0}^{\lfloor \log n\rfloor }{\frac {h}{2^{h}}}\right)\\&=O\left(n\sum _{h=0}^{\infty }{\frac {h}{2^{h}}}\right)\\&=O(n)\end{aligned}}}  ![{\displaystyle {\begin{aligned}\sum _{h=0}^{\lfloor \log n\rfloor }{\frac {n}{2^{h}}}O(h)&=O\left(n\sum _{h=0}^{\lfloor \log n\rfloor }{\frac {h}{2^{h}}}\right)\\&=O\left(n\sum _{h=0}^{\infty }{\frac {h}{2^{h}}}\right)\\&=O(n)\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b1f5dac83f79e16b8794611e4b4a91594c422d8) 

This uses the fact that the given infinite [series](./Series_(mathematics))      ∑ ∑   i = 0   ∞ ∞    i  /   2  i     {\textstyle \sum _{i=0}^{\infty }i/2^{i}}  ![{\textstyle \sum _{i=0}^{\infty }i/2^{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c346abeef6557578d06d71e709ff29c9e96a6f49) [converges](./Convergent_series).

 

The exact value of the above (the worst-case number of comparisons during the heap construction) is known to be equal to:

     2 n − −  2  s  2   ( n ) − −   e  2   ( n )   {\displaystyle 2n-2s_{2}(n)-e_{2}(n)}  ![{\displaystyle 2n-2s_{2}(n)-e_{2}(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0134cac877b68b92f3c460708a5a2f4466d1ef86),[[9]](./Binary_heap#cite_note-10)[[b]](./Binary_heap#cite_note-11) 

where *s*2(*n*) is the [sum of all digits of the binary representation](./Hamming_weight) of n and *e*2(*n*) is the exponent of 2 in the prime factorization of n.

 

The average case is more complex to analyze, but it can be shown to asymptotically approach 1.8814 *n* − 2 log2*n* + *O*(1) comparisons.[[10]](./Binary_heap#cite_note-12)[[11]](./Binary_heap#cite_note-13)

 

The **Build-Max-Heap** function that follows, converts an array *A* which stores a complete
binary tree with *n* nodes to a max-heap by repeatedly using **Max-Heapify** (down-heapify for a max-heap) in a bottom-up manner.
The array elements indexed by
*[floor](./Floor_function)*(*n*/2) + 1, *floor*(*n*/2) + 2, ..., *n*
are all leaves for the tree (assuming that indices start at 1)—thus each is a one-element heap, and does not need to be down-heapified. **Build-Max-Heap** runs
**Max-Heapify** on each of the remaining tree nodes.

 
```
Build-Max-Heap (A):
    for each index i from floor(length(A)/2) downto 1 do:
        Max-Heapify(A, i)
```
 

## Heap implementation

 This section is linked from [[Heapsort]]  [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/86/Binary_tree_in_array.svg/500px-Binary_tree_in_array.svg.png)](./File:Binary_tree_in_array.svg)A small complete binary tree stored in an array [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Binary_Heap_with_Array_Implementation.JPG/500px-Binary_Heap_with_Array_Implementation.JPG)](./File:Binary_Heap_with_Array_Implementation.JPG)Comparison between a binary heap and an array implementation. 

Heaps are commonly implemented with an [array](./Array_data_structure). Any binary tree can be stored in an array, but because a binary heap is always a complete binary tree, it can be stored compactly. No space is required for [pointers](./Pointer_(computer_programming)); instead, the parent and children of each node can be found by arithmetic on array indices. These properties make this heap implementation a simple example of an [implicit data structure](./Implicit_data_structure) or [Ahnentafel](./Ahnentafel) list. Details depend on the root position, which in turn may depend on constraints of a [programming language](./Programming_language) used for implementation, or programmer preference. Specifically, sometimes the root is placed at index 1, in order to simplify arithmetic.

 

Let *n* be the number of elements in the heap and *i* be an arbitrary valid index of the array storing the heap. If the tree root is at index 0, with valid indices 0 through *n − *1, then each element *a* at index *i* has

 
- children at indices 2*i *+ 1 and 2*i *+ 2
- its parent at index *[floor](./Floor_function)*((*i* − 1) / 2).

 

Alternatively, if the tree root is at index 1, with valid indices 1 through *n*, then each element *a* at index *i* has

 
- children at indices 2*i* and 2*i *+1
- its parent at index *[floor](./Floor_function)*(*i* / 2).

 

This implementation is used in the [heapsort](./Heapsort) algorithm which reuses the space allocated to the input array to store the heap (i.e. the algorithm is done [in-place](./In-place_algorithm)). This implementation is also useful as a [Priority queue](./Priority_queue).  When a [dynamic array](./Dynamic_array) is used, insertion of an unbounded number of items is possible.

 

The `upheap` or `downheap` operations can then be stated in terms of an array as follows: suppose that the heap property holds for the indices *b*, *b*+1, ..., *e*. The sift-down function extends the heap property to *b*−1, *b*, *b*+1, ..., *e*.
Only index *i* = *b*−1 can violate the heap property.
Let *j* be the index of the largest child of *a*[*i*] (for a max-heap, or the smallest child for a min-heap) within the range *b*, ..., *e*.
(If no such index exists because 2*i* > *e* then the heap property holds for the newly extended range and nothing needs to be done.)
By swapping the values *a*[*i*] and *a*[*j*] the heap property for position *i* is established.
At this point, the only problem is that the heap property might not hold for index *j*.
The sift-down function is applied [tail-recursively](./Tail_recursion) to index *j* until the heap property is established for all elements.

 

The sift-down function is fast. In each step it only needs two comparisons and one swap. The index value where it is working doubles in each iteration, so that at most log2 *e* steps are required.

 

For big heaps and using [virtual memory](./Virtual_memory), storing elements in an array according to the above scheme is inefficient: (almost) every level is in a different [page](./Page_(computer_memory)).  [B-heaps](./B-heap) are binary heaps that keep subtrees in a single page, reducing the number of pages accessed by up to a factor of ten.[[12]](./Binary_heap#cite_note-14)

 

The operation of merging two binary heaps takes Θ(*n*) for equal-sized heaps. The best you can do is (in case of array implementation) simply concatenating the two heap arrays and build a heap of the result.[[13]](./Binary_heap#cite_note-15) A heap on *n* elements can be merged with a heap on *k* elements using O(log *n* log *k*) key comparisons, or, in case of a pointer-based implementation, in O(log *n* log *k*) time.[[14]](./Binary_heap#cite_note-16) An algorithm for splitting a heap on *n* elements into two heaps on *k* and *n-k* elements, respectively, based on a new view
of heaps as an ordered collections of subheaps was presented in.[[15]](./Binary_heap#cite_note-17) The algorithm requires O(log *n* * log *n*)  comparisons. The view also presents a new and conceptually simple algorithm for merging heaps. When merging is a common task, a different heap implementation is recommended, such as [binomial heaps](./Binomial_heap), which can be merged in O(log *n*).

 

Additionally, a binary heap can be implemented with a traditional binary tree data structure, but there is an issue with finding the adjacent element on the last level on the binary heap when adding an element. This element can be determined algorithmically or by adding extra data to the nodes, called "threading" the tree—instead of merely storing references to the children, we store the [inorder](./Inorder) successor of the node as well.

 

It is possible to modify the heap structure to make the extraction of both the smallest and largest element possible in [    O   {\displaystyle O}  ![{\displaystyle O}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d70e1d0d87e2ef1092ea1ffe2923d9933ff18fc)](./Big_O_notation)    ( log ⁡ ⁡  n )   {\displaystyle (\log n)}  ![{\displaystyle (\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f92166a0c67bebc0d93429917673f7d73ea420b1) time.[[16]](./Binary_heap#cite_note-sym-18)  To do this, the rows alternate between min heap and max-heap.  The algorithms are roughly the same, but, in each step, one must consider the alternating rows with alternating comparisons.  The performance is roughly the same as a normal single direction heap. This idea can be generalized to a min-max-median heap.

 

## Derivation of index equations

 

In an array-based heap, the children and parent of a node can be located via simple arithmetic on the node's index. This section derives the relevant equations for heaps with their root at index 0, with additional notes on heaps with their root at index 1.

 

To avoid confusion, we define the **level** of a node as its distance from the root, such that the root itself occupies level 0.

 

### Child nodes

 

For a general node located at index i (beginning from 0), we will first derive the index of its right child,      right  = 2 i + 2   {\displaystyle {\text{right}}=2i+2}  ![{\displaystyle {\text{right}}=2i+2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/32ca8eccdc7c16039f885cdf9ec831e5eed514c5).

 

Let node i be located in level L, and note that any level l contains exactly      2  l     {\displaystyle 2^{l}}  ![{\displaystyle 2^{l}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d99018c1b3139cf29ec7d875e018f3188350ada1) nodes. Furthermore, there are exactly      2  l + 1   − −  1   {\displaystyle 2^{l+1}-1}  ![{\displaystyle 2^{l+1}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dfad4341ad1c847177c6d3ea1ff22dca4245c55c) nodes contained in the layers up to and including layer l (think of binary arithmetic; 0111...111 = 1000...000 - 1). Because the root is stored at 0, the kth node will be stored at index     ( k − −  1 )   {\displaystyle (k-1)}  ![{\displaystyle (k-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e69f74fa2adbbab50f6969acb2af719045435461). Putting these observations together yields the following expression for the **index of the last node in layer l**.

      last  ( l ) = (  2  l + 1   − −  1 ) − −  1 =  2  l + 1   − −  2   {\displaystyle {\text{last}}(l)=(2^{l+1}-1)-1=2^{l+1}-2}  ![{\displaystyle {\text{last}}(l)=(2^{l+1}-1)-1=2^{l+1}-2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/039261a4e9a7f0988db871983f9af657972dc1d1) 

Let there be j nodes after node i in layer L, such that

         i =     last  ( L ) − −  j     =     (  2  L + 1   − −  2 ) − −  j       {\displaystyle {\begin{alignedat}{2}i=&\quad {\text{last}}(L)-j\\=&\quad (2^{L+1}-2)-j\\\end{alignedat}}}  ![{\displaystyle {\begin{alignedat}{2}i=&\quad {\text{last}}(L)-j\\=&\quad (2^{L+1}-2)-j\\\end{alignedat}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/150fed76d084262c71f1b74a12ce89f2e7f2286e) 

Each of these j nodes must have exactly 2 children, so there must be     2 j   {\displaystyle 2j}  ![{\displaystyle 2j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a031183edfcba17a64f7bad6f0f3da15bf1b0b99) nodes separating i's right child from the end of its layer (    L + 1   {\displaystyle L+1}  ![{\displaystyle L+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/75933f53b57abd647b7e539c51c4f90fd122bb63)).

          right  =     last(L + 1)  − −  2 j     =     (  2  L + 2   − −  2 ) − −  2 j     =    2 (  2  L + 1   − −  2 − −  j ) + 2     =    2 i + 2       {\displaystyle {\begin{alignedat}{2}{\text{right}}=&\quad {\text{last(L + 1)}}-2j\\=&\quad (2^{L+2}-2)-2j\\=&\quad 2(2^{L+1}-2-j)+2\\=&\quad 2i+2\end{alignedat}}}  ![{\displaystyle {\begin{alignedat}{2}{\text{right}}=&\quad {\text{last(L + 1)}}-2j\\=&\quad (2^{L+2}-2)-2j\\=&\quad 2(2^{L+1}-2-j)+2\\=&\quad 2i+2\end{alignedat}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f68925f3a3bffafa2879240c2a0f26c6f850406e) 

Noting that the left child of any node is always 1 place before its right child, we get      left  = 2 i + 1   {\displaystyle {\text{left}}=2i+1}  ![{\displaystyle {\text{left}}=2i+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/38f41c3c5f13acfd82b321f265b7f80ce236e75b).

 

If the root is located at index 1 instead of 0, the last node in each level is instead at index      2  l + 1   − −  1   {\displaystyle 2^{l+1}-1}  ![{\displaystyle 2^{l+1}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dfad4341ad1c847177c6d3ea1ff22dca4245c55c). Using this throughout yields      left  = 2 i   {\displaystyle {\text{left}}=2i}  ![{\displaystyle {\text{left}}=2i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbc36e0d7f83009322861ddecd75efee1bce3def) and      right  = 2 i + 1   {\displaystyle {\text{right}}=2i+1}  ![{\displaystyle {\text{right}}=2i+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a912711b9fc45d9ced00bb90446c9531ecd2f7fc) for heaps with their root at 1.

 

### Parent node

 

Every non-root node is either the left or right child of its parent, so one of the following must hold:

 
-     i = 2 × ×  (  parent  ) + 1   {\displaystyle i=2\times ({\text{parent}})+1}  ![{\displaystyle i=2\times ({\text{parent}})+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/00f553a10e4625564819c5f2dc550428e7da23df)
-     i = 2 × ×  (  parent  ) + 2   {\displaystyle i=2\times ({\text{parent}})+2}  ![{\displaystyle i=2\times ({\text{parent}})+2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5e01b57bbdebebb1bd20a7ea35ab3d5d3d966974)

 

Hence,

      parent  =    i − −  1  2      or       i − −  2  2     {\displaystyle {\text{parent}}={\frac {i-1}{2}}\;{\textrm {or}}\;{\frac {i-2}{2}}}  ![{\displaystyle {\text{parent}}={\frac {i-1}{2}}\;{\textrm {or}}\;{\frac {i-2}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01c4fb2151973555b629c2eb95b71e994a5f8adf) 

Now consider the expression      ⌊     i − −  1  2    ⌋    {\displaystyle \left\lfloor {\dfrac {i-1}{2}}\right\rfloor }  ![{\displaystyle \left\lfloor {\dfrac {i-1}{2}}\right\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd7bea3d8291201eb4a4297dc225e096f71b4ec).

 

If node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is a left child, this gives the result immediately, however, it also gives the correct result if node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is a right child. In this case,     ( i − −  2 )   {\displaystyle (i-2)}  ![{\displaystyle (i-2)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e72fd36b5107b350f88b400dab8de091cbb79e04) must be even, and hence     ( i − −  1 )   {\displaystyle (i-1)}  ![{\displaystyle (i-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cb6858c31c116f58a5c51345a12ea06e83a3d4e9) must be odd.

          ⌊     i − −  1  2    ⌋  =     ⌊      i − −  2  2    +    1 2     ⌋      =       i − −  2  2       =     parent        {\displaystyle {\begin{alignedat}{2}\left\lfloor {\dfrac {i-1}{2}}\right\rfloor =&\quad \left\lfloor {\dfrac {i-2}{2}}+{\dfrac {1}{2}}\right\rfloor \\=&\quad {\frac {i-2}{2}}\\=&\quad {\text{parent}}\end{alignedat}}}  ![{\displaystyle {\begin{alignedat}{2}\left\lfloor {\dfrac {i-1}{2}}\right\rfloor =&\quad \left\lfloor {\dfrac {i-2}{2}}+{\dfrac {1}{2}}\right\rfloor \\=&\quad {\frac {i-2}{2}}\\=&\quad {\text{parent}}\end{alignedat}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/28959d1675c247656687d3deb7cf359ed2280aed) 

Therefore, irrespective of whether a node is a left or right child, its parent can be found by the expression:

      parent  =  ⌊     i − −  1  2    ⌋    {\displaystyle {\text{parent}}=\left\lfloor {\dfrac {i-1}{2}}\right\rfloor }  ![{\displaystyle {\text{parent}}=\left\lfloor {\dfrac {i-1}{2}}\right\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a39ac09ebd3525dd701af2b20bd8bff6b71413e) 

## Related structures

 

Since the ordering of siblings in a heap is not specified by the heap property, a single node's two children can be freely interchanged unless doing so violates the shape property (compare with [treap](./Treap)). Note, however, that in the common array-based heap, simply swapping the children might also necessitate moving the children's sub-tree nodes to retain the heap property.

 

The binary heap is a special case of the [d-ary heap](./D-ary_heap) in which d = 2.

 

## Summary of running times

 

Here are [time complexities](./Computational_complexity_theory)[[17]](./Binary_heap#cite_note-CLRS-19) of various heap data structures. The abbreviation am. indicates that the given complexity is amortized, otherwise it is a worst-case complexity. For the meaning of "*O*(*f*)" and "*Θ*(*f*)" see [Big O notation](./Big_O_notation). Names of operations assume a min-heap.

 
| Operation | find-min | delete-min | decrease-key | insert | meld | make-heap[c] |
| --- | --- | --- | --- | --- | --- | --- |
| Binary[17] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) | Θ(n) |
| Skew[18] | Θ(1) | O(logn)am. | O(logn)am. | O(logn)am. | O(logn)am. | Θ(n)am. |
| Leftist[19] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) |
| Binomial[17][21] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1)am. | Θ(logn)[d] | Θ(n) |
| Skew binomial[22] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1) | Θ(logn)[d] | Θ(n) |
| 2–3 heap[24] | Θ(1) | O(logn)am. | Θ(1) | Θ(1)am. | O(logn)[d] | Θ(n) |
| Bottom-up skew[18] | Θ(1) | O(logn)am. | O(logn)am. | Θ(1)am. | Θ(1)am. | Θ(n)am. |
| Pairing[25] | Θ(1) | O(logn)am. | o(logn)am.[e] | Θ(1) | Θ(1) | Θ(n) |
| Rank-pairing[28] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Fibonacci[17][29] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Strict Fibonacci[30][f] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n) |
| Brodal[31][f] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n)[32] |

 
1. [↑](./Binary_heap#cite_ref-9) In fact, this procedure can be shown to take Θ(*n* log *n*) time [in the worst case](./Best,_worst_and_average_case), meaning that *n* log *n* is also an asymptotic lower bound on the complexity.[[1]](./Binary_heap#cite_note-clrs-1): 167  In the *average case* (averaging over all [permutations](./Permutation) of n inputs), though, the method takes linear time.[[8]](./Binary_heap#cite_note-heapbuildjalg-8)
2. [↑](./Binary_heap#cite_ref-11) This does not mean that *sorting* can be done in linear time since building a heap is only the first step of the [heapsort](./Heapsort) algorithm.
3. [↑](./Binary_heap#cite_ref-23) *make-heap* is the operation of building a heap from a sequence of *n* unsorted elements. It can be done in *Θ*(*n*) time whenever *meld* runs in *O*(log *n*) time (where both complexities can be amortized).[[18]](./Binary_heap#cite_note-sleator-tarjan-skew-20)[[19]](./Binary_heap#cite_note-tarjan-leftist-21) Another algorithm achieves *Θ*(*n*) for binary heaps.[[20]](./Binary_heap#cite_note-hayward-mcdiarmid-heap-build-22)
4. [1](./Binary_heap#cite_ref-bootstrap-meld_25-0) [2](./Binary_heap#cite_ref-bootstrap-meld_25-1) [3](./Binary_heap#cite_ref-bootstrap-meld_25-2) For [persistent](./Persistent_data_structure) heaps (not supporting *decrease-key*), a generic transformation reduces the cost of *meld* to that of *insert*, while the new cost of *delete-min* is the sum of the old costs of *delete-min* and *meld*.[[23]](./Binary_heap#cite_note-27) Here, it makes *meld* run in *Θ*(1) time (amortized, if the cost of *insert* is) while *delete-min* still runs in *O*(log *n*). Applied to skew binomial heaps, it yields Brodal-Okasaki queues, persistent heaps with optimal worst-case complexities.[[22]](./Binary_heap#cite_note-brodal-okasaki-26)
5. [↑](./Binary_heap#cite_ref-pairingdecreasekey_32-0) Lower bound of     Ω Ω  ( log ⁡ ⁡  log ⁡ ⁡  n ) ,   {\displaystyle \Omega (\log \log n),}  ![{\displaystyle \Omega (\log \log n),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7caf8c32fbd99eed1338c02b7f7f1255f16ade36)[[26]](./Binary_heap#cite_note-Fredman1999-30) upper bound of     O (  2  2   log ⁡ ⁡  log ⁡ ⁡  n     ) .   {\displaystyle O(2^{2{\sqrt {\log \log n}}}).}  ![{\displaystyle O(2^{2{\sqrt {\log \log n}}}).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/45c772d2ec070e49a6438ea92b1c8dc764613c5e)[[27]](./Binary_heap#cite_note-31)
6. [1](./Binary_heap#cite_ref-optimum_36-0) [2](./Binary_heap#cite_ref-optimum_36-1) Brodal queues and strict Fibonacci heaps achieve optimal worst-case complexities for heaps. They were first described as imperative data structures. The Brodal-Okasaki queue is a [persistent](./Persistent_data_structure) data structure achieving the same optimum, except that *decrease-key* is not supported.

 

## References

  
1. [1](./Binary_heap#cite_ref-clrs_1-0) [2](./Binary_heap#cite_ref-clrs_1-1) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009) [1990]. [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03384-4](./Special:BookSources/0-262-03384-4).
2. [↑](./Binary_heap#cite_ref-2) [Williams, J. W. J.](./J._W._J._Williams) (1964), "Algorithm 232 - Heapsort", *[Communications of the ACM](./Communications_of_the_ACM)*, **7** (6): 347–348, [doi](./Doi_(identifier)):[10.1145/512274.3734138](https://doi.org/10.1145%2F512274.3734138)
3. [↑](./Binary_heap#cite_ref-3) Y Narahari, ["Binary Heaps"](http://lcm.csa.iisc.ernet.in/dsa/node137.html), [*Data Structures and Algorithms*](https://gtl.csa.iisc.ac.in/dsa/)
4. [↑](./Binary_heap#cite_ref-4) Porter, Thomas; Simon, Istvan (Sep 1975). "Random insertion into a priority queue structure". *IEEE Transactions on Software Engineering*. **SE-1** (3): 292–298. [Bibcode](./Bibcode_(identifier)):[1975ITSEn...1..292P](https://ui.adsabs.harvard.edu/abs/1975ITSEn...1..292P). [doi](./Doi_(identifier)):[10.1109/TSE.1975.6312854](https://doi.org/10.1109%2FTSE.1975.6312854). [ISSN](./ISSN_(identifier)) [1939-3520](https://search.worldcat.org/issn/1939-3520). [S2CID](./S2CID_(identifier)) [18907513](https://api.semanticscholar.org/CorpusID:18907513).
5. [↑](./Binary_heap#cite_ref-5) Mehlhorn, Kurt; Tsakalidis, A. (Feb 1989). ["Data structures"](https://publikationen.sulb.uni-saarland.de/handle/20.500.11880/26179). *Universität des Saarlandes*: 27. [doi](./Doi_(identifier)):[10.22028/D291-26123](https://doi.org/10.22028%2FD291-26123). Porter and Simon [171] analyzed the average cost of inserting a random element into a random heap in terms of exchanges. They proved that this average is bounded by the constant 1.61. Their proof does not generalize to sequences of insertions since random insertions into random heaps do not create random heaps. The repeated insertion problem was solved by Bollobas and Simon [27]; they show that the expected number of exchanges is bounded by 1.7645. The worst-case cost of inserts and deletemins was studied by Gonnet and Munro [84]; they give log log n + O(1) and log n + log n* + O(1) bounds for the number of comparisons respectively.
6. [↑](./Binary_heap#cite_ref-6) ["python/cpython/heapq.py"](https://github.com/python/cpython/blob/master/Lib/heapq.py). *GitHub*. Retrieved 2020-08-07.
7. [↑](./Binary_heap#cite_ref-7) ["heapq — Heap queue algorithm — Python 3.8.5 documentation"](https://docs.python.org/3/library/heapq.html#heapq.heappushpop). *docs.python.org*. Retrieved 2020-08-07. heapq.heappushpop(heap, item): Push item on the heap, then pop and return the smallest item from the heap. The combined action runs more efficiently than heappush() followed by a separate call to heappop().
8. [1](./Binary_heap#cite_ref-heapbuildjalg_8-0) [2](./Binary_heap#cite_ref-heapbuildjalg_8-1) Hayward, Ryan; McDiarmid, Colin (1991). ["Average Case Analysis of Heap Building by Repeated Insertion"](https://web.archive.org/web/20160205023201/http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF). *J. Algorithms*. **12**: 126–153. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.353.7888](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.353.7888). [doi](./Doi_(identifier)):[10.1016/0196-6774(91)90027-v](https://doi.org/10.1016%2F0196-6774%2891%2990027-v). Archived from [the original](http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF) on 2016-02-05. Retrieved 2016-01-28.
9. [↑](./Binary_heap#cite_ref-10) Suchenek, Marek A. (2012), ["Elementary Yet Precise Worst-Case Analysis of Floyd's Heap-Construction Program"](http://www.deepdyve.com/lp/ios-press/elementary-yet-precise-worst-case-analysis-of-floyd-s-heap-50NW30HMxU), *Fundamenta Informaticae*, **120** (1): 75–92, [doi](./Doi_(identifier)):[10.3233/FI-2012-751](https://doi.org/10.3233%2FFI-2012-751).
10. [↑](./Binary_heap#cite_ref-12) Doberkat, Ernst E. (May 1984). ["An Average Case Analysis of Floyd's Algorithm to Construct Heaps"](https://core.ac.uk/download/pdf/82135122.pdf) (PDF). *Information and Control*. **6** (2): 114–131. [doi](./Doi_(identifier)):[10.1016/S0019-9958(84)80053-4](https://doi.org/10.1016%2FS0019-9958%2884%2980053-4).
11. [↑](./Binary_heap#cite_ref-13) Pasanen, Tomi (November 1996). *Elementary Average Case Analysis of Floyd's Algorithm to Construct Heaps* (Technical report). Turku Centre for Computer Science. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.15.9526](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.15.9526). [ISBN](./ISBN_(identifier)) [951-650-888-X](./Special:BookSources/951-650-888-X). TUCS Technical Report No. 64.  Note that this paper uses Floyd's original terminology "siftup" for what is now called sifting *down*.
12. [↑](./Binary_heap#cite_ref-14) Kamp, Poul-Henning (June 11, 2010). ["You're Doing It Wrong"](http://queue.acm.org/detail.cfm?id=1814327). *ACM Queue*. Vol. 8, no. 6. 
13. [↑](./Binary_heap#cite_ref-15) Chris L. Kuszmaul.
["binary heap"](http://nist.gov/dads/HTML/binaryheap.html) [Archived](https://web.archive.org/web/20080808141408/http://www.nist.gov/dads/HTML/binaryheap.html) 2008-08-08 at the [Wayback Machine](./Wayback_Machine).
Dictionary of Algorithms and Data Structures, Paul E. Black, ed., U.S. National Institute of Standards and Technology. 16 November 2009.
14. [↑](./Binary_heap#cite_ref-16) [J.-R. Sack](./Jörg-Rüdiger_Sack) and T. Strothotte
["An Algorithm for Merging Heaps"](https://doi.org/10.1007%2FBF00264229),
Acta Informatica 22, 171-186 (1985).
15. [↑](./Binary_heap#cite_ref-17) [Sack, Jörg-Rüdiger](./Jörg-Rüdiger_Sack); Strothotte, Thomas (1990). ["A characterization of heaps and its applications"](https://doi.org/10.1016%2F0890-5401%2890%2990026-E). *Information and Computation*. **86**: 69–86. [doi](./Doi_(identifier)):[10.1016/0890-5401(90)90026-E](https://doi.org/10.1016%2F0890-5401%2890%2990026-E).
16. [↑](./Binary_heap#cite_ref-sym_18-0) [Atkinson, M.D.](./Michael_D._Atkinson); [J.-R. Sack](./Jörg-Rüdiger_Sack); N. Santoro & T. Strothotte (1 October 1986). ["Min-max heaps and generalized priority queues"](https://web.archive.org/web/20070127093845/http://cg.scs.carleton.ca/%7Emorin/teaching/5408/refs/minmax.pdf) (PDF). Programming techniques and Data structures. Comm. ACM, 29(10): 996–1000. Archived from [the original](http://cg.scs.carleton.ca/~morin/teaching/5408/refs/minmax.pdf) (PDF) on 27 January 2007. Retrieved 29 April 2008.
17. [1](./Binary_heap#cite_ref-CLRS_19-0) [2](./Binary_heap#cite_ref-CLRS_19-1) [3](./Binary_heap#cite_ref-CLRS_19-2) [4](./Binary_heap#cite_ref-CLRS_19-3) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest) (1990). [*Introduction to Algorithms*](./Introduction_to_Algorithms) (1st ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03141-8](./Special:BookSources/0-262-03141-8).
18. [1](./Binary_heap#cite_ref-sleator-tarjan-skew_20-0) [2](./Binary_heap#cite_ref-sleator-tarjan-skew_20-1) [3](./Binary_heap#cite_ref-sleator-tarjan-skew_20-2) [Sleator, Daniel Dominic](./Daniel_Sleator); [Tarjan, Robert Endre](./Robert_Tarjan) (February 1986). ["Self-Adjusting Heaps"](https://www.cs.cmu.edu/~sleator/papers/Adjusting-Heaps.htm). *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **15** (1): 52–69. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.93.6678](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.93.6678). [doi](./Doi_(identifier)):[10.1137/0215004](https://doi.org/10.1137%2F0215004). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397). 
19. [1](./Binary_heap#cite_ref-tarjan-leftist_21-0) [2](./Binary_heap#cite_ref-tarjan-leftist_21-1) [Tarjan, Robert](./Robert_Tarjan) (1983). "3.3. Leftist heaps". *Data Structures and Network Algorithms*. pp. 38–42. [doi](./Doi_(identifier)):[10.1137/1.9781611970265](https://doi.org/10.1137%2F1.9781611970265). [ISBN](./ISBN_(identifier)) [978-0-89871-187-5](./Special:BookSources/978-0-89871-187-5).
20. [↑](./Binary_heap#cite_ref-hayward-mcdiarmid-heap-build_22-0) Hayward, Ryan; McDiarmid, Colin (1991). ["Average Case Analysis of Heap Building by Repeated Insertion"](https://web.archive.org/web/20160205023201/http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF). *J. Algorithms*. **12**: 126–153. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.353.7888](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.353.7888). [doi](./Doi_(identifier)):[10.1016/0196-6774(91)90027-v](https://doi.org/10.1016%2F0196-6774%2891%2990027-v). Archived from [the original](http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF) on 2016-02-05. Retrieved 2016-01-28.
21. [↑](./Binary_heap#cite_ref-24) ["Binomial Heap | Brilliant Math & Science Wiki"](https://brilliant.org/wiki/binomial-heap/). *brilliant.org*. Retrieved 2019-09-30.
22. [1](./Binary_heap#cite_ref-brodal-okasaki_26-0) [2](./Binary_heap#cite_ref-brodal-okasaki_26-1) Brodal, Gerth Stølting; Okasaki, Chris (November 1996), "Optimal purely functional priority queues", *Journal of Functional Programming*, **6** (6): 839–857, [doi](./Doi_(identifier)):[10.1017/s095679680000201x](https://doi.org/10.1017%2Fs095679680000201x)
23. [↑](./Binary_heap#cite_ref-27) [Okasaki, Chris](./Chris_Okasaki) (1998). "10.2. Structural Abstraction". *Purely Functional Data Structures* (1st ed.). pp. 158–162. [ISBN](./ISBN_(identifier)) [9780521631242](./Special:BookSources/9780521631242).
24. [↑](./Binary_heap#cite_ref-28) [Takaoka, Tadao](./Tadao_Takaoka?action=edit&redlink=1) (1999), [*Theory of 2–3 Heaps*](https://ir.canterbury.ac.nz/bitstream/handle/10092/14769/2-3heaps.pdf) (PDF), p. 12
25. [↑](./Binary_heap#cite_ref-Iacono_29-0) [Iacono, John](./John_Iacono) (2000), "Improved upper bounds for pairing heaps", [*Proc. 7th Scandinavian Workshop on Algorithm Theory*](http://john2.poly.edu/papers/swat00/paper.pdf) (PDF), Lecture Notes in Computer Science, vol. 1851, Springer-Verlag, pp. 63–77, [arXiv](./ArXiv_(identifier)):[1110.4428](https://arxiv.org/abs/1110.4428), [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.748.7812](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.748.7812), [doi](./Doi_(identifier)):[10.1007/3-540-44985-X_5](https://doi.org/10.1007%2F3-540-44985-X_5), [ISBN](./ISBN_(identifier)) [3-540-67690-2](./Special:BookSources/3-540-67690-2)
26. [↑](./Binary_heap#cite_ref-Fredman1999_30-0) [Fredman, Michael Lawrence](./Michael_Fredman) (July 1999). ["On the Efficiency of Pairing Heaps and Related Data Structures"](http://www.uqac.ca/azinflou/Fichiers840/EfficiencyPairingHeap.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **46** (4): 473–501. [doi](./Doi_(identifier)):[10.1145/320211.320214](https://doi.org/10.1145%2F320211.320214).
27. [↑](./Binary_heap#cite_ref-31) Pettie, Seth (2005). [*Towards a Final Analysis of Pairing Heaps*](http://web.eecs.umich.edu/~pettie/papers/focs05.pdf) (PDF). FOCS '05 Proceedings of the 46th Annual IEEE Symposium on Foundations of Computer Science. pp. 174–183. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.549.471](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.549.471). [doi](./Doi_(identifier)):[10.1109/SFCS.2005.75](https://doi.org/10.1109%2FSFCS.2005.75). [ISBN](./ISBN_(identifier)) [0-7695-2468-0](./Special:BookSources/0-7695-2468-0).
28. [↑](./Binary_heap#cite_ref-33) Haeupler, Bernhard; Sen, Siddhartha; [Tarjan, Robert E.](./Robert_Tarjan) (November 2011). ["Rank-pairing heaps"](http://sidsen.org/papers/rp-heaps-journal.pdf) (PDF). *SIAM J. Computing*. **40** (6): 1463–1485. [doi](./Doi_(identifier)):[10.1137/100785351](https://doi.org/10.1137%2F100785351).
29. [↑](./Binary_heap#cite_ref-Fredman_And_Tarjan_34-0) [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (July 1987). ["Fibonacci heaps and their uses in improved network optimization algorithms"](http://bioinfo.ict.ac.cn/~dbu/AlgorithmCourses/Lectures/Fibonacci-Heap-Tarjan.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **34** (3): 596–615. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.309.8927](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.309.8927). [doi](./Doi_(identifier)):[10.1145/28869.28874](https://doi.org/10.1145%2F28869.28874). An earlier version of this paper appeared in 1984 {{doi|10.1109/SFCS.1984.715934}}
30. [↑](./Binary_heap#cite_ref-35) [Brodal, Gerth Stølting](./Gerth_Stølting_Brodal); Lagogiannis, George; [Tarjan, Robert E.](./Robert_Tarjan) (2012). [*Strict Fibonacci heaps*](http://www.cs.au.dk/~gerth/papers/stoc12.pdf) (PDF). Proceedings of the 44th symposium on Theory of Computing - STOC '12. pp. 1177–1184. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.233.1740](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.233.1740). [doi](./Doi_(identifier)):[10.1145/2213977.2214082](https://doi.org/10.1145%2F2213977.2214082). [ISBN](./ISBN_(identifier)) [978-1-4503-1245-5](./Special:BookSources/978-1-4503-1245-5).
31. [↑](./Binary_heap#cite_ref-37) [Brodal, Gerth S.](./Gerth_Stølting_Brodal) (1996), ["Worst-Case Efficient Priority Queues"](http://www.cs.au.dk/~gerth/papers/soda96.pdf) (PDF), *Proc. 7th Annual ACM-SIAM Symposium on Discrete Algorithms*, pp. 52–58
32. [↑](./Binary_heap#cite_ref-38) [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2004). "7.3.6. Bottom-Up Heap Construction". *Data Structures and Algorithms in Java* (3rd ed.). pp. 338–341. [ISBN](./ISBN_(identifier)) [0-471-46983-1](./Special:BookSources/0-471-46983-1).

 

## External links

 
- [Open Data Structures - Section 10.1 - BinaryHeap: An Implicit Binary Tree](http://opendatastructures.org/versions/edition-0.1e/ods-java/10_1_BinaryHeap_Implicit_Bi.html), [Pat Morin](./Pat_Morin)
- [Implementation of binary max heap in C](https://robin-thomas.github.io/max-heap/) by Robin Thomas
- [Implementation of binary min heap in C](https://robin-thomas.github.io/min-heap/) by Robin Thomas

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |