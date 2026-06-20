---
source: https://en.wikipedia.org/wiki/Quadtree
fetched: 2026-06-19
---

Tree data structure that partitions a 2D area 
|  | This articlehas an unclearcitation style.The references used may be made clearer with a different or consistent style ofcitationandfootnoting.(April 2015)(Learn how and when to remove this message) |
| --- | --- |

 
| Quadtree |
| --- |
| Type | Tree |
| Invented | 1974 |
| Invented by | Raphael FinkelandJ.L. Bentley |
| Time complexityinbig O notationOperationAverageWorst caseSpace complexity | Time complexityinbig O notation | Operation | Average | Worst case | Space complexity |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Space complexity |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/8b/Point_quadtree.svg/330px-Point_quadtree.svg.png)](./File:Point_quadtree.svg)A point-region quadtree with point data. Bucket capacity 1. [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d7/Quadtree_compression_of_an_image.gif/330px-Quadtree_compression_of_an_image.gif)](./File:Quadtree_compression_of_an_image.gif)Quadtree compression of an image step by step. Left shows the compressed image with the tree bounding boxes while the right shows just the compressed image 

A **quadtree** is a [tree data structure](./Tree_data_structure) in which each internal node has exactly four children. Quadtrees are the two-dimensional analog of [octrees](./Octree) and are most often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions. The data associated with a leaf cell varies by application, but the leaf cell represents a "unit of interesting spatial information".

 

The subdivided regions may be square or rectangular, or may have arbitrary shapes. Although similar subdivisions were used much earlier (for instance in the [Whitney covering lemma](./Whitney_covering_lemma) of 1934),[[1]](./Quadtree#cite_note-1) this data structure was named a quadtree by [Raphael Finkel](./Raphael_Finkel) and [J.L. Bentley](./J.L._Bentley) in 1974.[[2]](./Quadtree#cite_note-2) A similar partitioning is also known as a *Q-tree*. 

 

All forms of quadtrees share some common features:

 
- They decompose space into adaptable cells.
- Each cell (or bucket) has a maximum capacity. When maximum capacity is reached, the bucket splits.
- The tree directory follows the spatial decomposition of the quadtree.

 

A **tree-pyramid** (**T-pyramid**) is a "complete" tree; every node of the T-pyramid has four child nodes except leaf nodes; all leaves are on the same level, the level that corresponds to individual pixels in the image. The data in a tree-pyramid can be stored compactly in an array as an [implicit data structure](./Implicit_data_structure) similar to the way a [binary heap](./Binary_heap#Heap_implementation) can store a complete binary tree compactly in an array.[[3]](./Quadtree#cite_note-3)

 

## Types

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c2/2D_Binary_Index.svg/250px-2D_Binary_Index.svg.png)](./File:2D_Binary_Index.svg)An example of a recursive [binary space partitioning](./Binary_space_partitioning) quadtree for a 2D index. 

Quadtrees may be classified according to the type of data they represent, including areas, points, lines and curves. Quadtrees may also be classified by whether the shape of the tree is independent of the order in which data is processed. The following are common types of quadtrees.

 

### Region quadtree

 

The region quadtree represents [a partition of space](./Space_partitioning) in two dimensions by decomposing the region into four equal quadrants, subquadrants, and so on with each leaf node containing data corresponding to a specific subregion. It can be also interpreted as a method for "[subpaving](./Subpaving) the region", based on set of hierarchical grids; or as a method of [image compression](./Image_compression), when an image  is discretizated as a mosaic of "equal color regions".

 

Each node in the tree either has exactly four children, or has no children (a leaf node). The height of quadtrees that follow this decomposition strategy (i.e. subdividing subquadrants as long as there is interesting data in the subquadrant for which more refinement is desired) is sensitive to and dependent on the spatial distribution of interesting areas in the space being decomposed. The region quadtree is a type of [trie](./Trie).

 

A region quadtree with a depth of n may be used to represent an image consisting of 2n × 2n pixels, where each pixel value is 0 or 1. The root node represents the entire image region. If the pixels in any region are not entirely 0s or 1s, it is subdivided. In this application, each leaf node represents a block of pixels that are all 0s or all 1s. Note the potential savings in terms of space when these trees are used for storing images; images often have many regions of considerable size that have the same colour value throughout. Rather than store a big 2-D array of every pixel in the image, a quadtree can capture the same information potentially many divisive levels higher than the pixel-resolution sized cells that we would otherwise require. The tree resolution and overall size is bounded by the pixel and image sizes.

 

A region quadtree may also be used as a variable resolution representation of a data field. For example, the temperatures in an area may be stored as a quadtree, with each leaf node storing the average temperature over the subregion it represents.

 

### Point quadtree

  target of redirect from Weighted planar stochastic lattice  

The point quadtree[[4]](./Quadtree#cite_note-4) is an adaptation of a [binary tree](./Binary_tree) used to represent two-dimensional point data. It shares the features of all quadtrees but is a true tree as the center of a subdivision is always on a point. It is often very efficient in comparing two-dimensional, ordered data points, usually operating in [O(log n)](./Big_O_notation) time. Point quadtrees are worth mentioning for completeness, but they have been surpassed by [*k*-d trees](./K-d_tree) as tools for generalized binary search.[[5]](./Quadtree#cite_note-Aluru2004-5)  Point quadtrees with random insertion have been studied under the name **weighted planar stochastic lattices**.[[6]](./Quadtree#cite_note-6)

 

Point quadtrees are constructed as follows. Given the next point to insert, we find the cell in which it lies and add it to the tree. The new point is added such that the cell that contains it is divided into quadrants by the vertical and horizontal lines that run through the point. Consequently, cells are rectangular but not necessarily square. In these trees, each node contains one of the input points.

 

Since the division of the plane is decided by the order of point-insertion, the tree's height is sensitive to and dependent on insertion order. Inserting in a "bad" order can lead to a tree of height linear in the number of input points (at which point it becomes a linked-list). If the point-set is static, pre-processing can be done to create a tree of balanced height.

 

#### Node structure for a point quadtree

 

A node of a point quadtree is similar to a node of a [binary tree](./Binary_tree), with the major difference being that it has four pointers (one for each quadrant) instead of two ("left" and "right") as in an ordinary binary tree. Also a key is usually decomposed into two parts, referring to x and y coordinates. Therefore, a node contains the following information:

 
- four pointers: quad['NW'], quad['NE'], quad['SW'], and quad['SE']
- point; which in turn contains:

- key; usually expressed as x, y coordinates
- value; for example a name

 

### Point-region (PR) quadtree

 

Point-region (PR) quadtrees[[7]](./Quadtree#cite_note-7)[[8]](./Quadtree#cite_note-8) are very similar to region quadtrees. The difference is the type of information stored about the cells. In a region quadtree, a uniform value is stored that applies to the entire area of the cell of a leaf. The cells of a PR quadtree, however, store a list of points that exist within the cell of a leaf. As mentioned previously, for trees following this decomposition strategy the height depends on the spatial distribution of the points. Like the point quadtree, the PR quadtree may also have a linear height when given a "bad" set.

 

### Edge quadtree

 

Edge quadtrees[[9]](./Quadtree#cite_note-9)[[10]](./Quadtree#cite_note-10) (much like PM quadtrees) are used to store lines rather than points. Curves are approximated by subdividing cells to a very fine resolution, specifically until there is a single line segment per cell. Near corners/vertices, edge quadtrees will continue dividing until they reach their maximum level of decomposition. This can result in extremely unbalanced trees which may defeat the purpose of indexing.

 

### Polygonal map (PM) quadtree

 

The polygonal map quadtree (or PM Quadtree) is a variation of quadtree which is used to store collections of polygons that may be degenerate (meaning that they have isolated vertices or edges).[[11]](./Quadtree#cite_note-11) [[12]](./Quadtree#cite_note-12) A big difference between PM quadtrees and edge quadtrees is that the cell under consideration is not subdivided if the segments meet at a vertex in the cell.

 

There are three main classes of PM Quadtrees, which vary depending on what information they store within each black node. PM3 quadtrees can store any amount of non-intersecting edges and at most one point. PM2 quadtrees are the same as PM3 quadtrees except that all edges must share the same end point. Finally PM1 quadtrees are similar to PM2, but black nodes can contain a point and its edges or just a set of edges that share a point, but you cannot have a point and a set of edges that do not contain the point.

 

### Compressed quadtrees

 

This section summarizes a subsection from a book by [Sariel Har-Peled](./Sariel_Har-Peled).[[13]](./Quadtree#cite_note-13)

 

If we were to store every node corresponding to a subdivided cell, we may end up storing a lot of empty nodes. We can cut down on the size of such sparse trees by only storing subtrees whose leaves have interesting data (i.e. "important subtrees"). We can actually cut down on the size even further. When we only keep important subtrees, the pruning process may leave long paths in the tree where the intermediate nodes have degree two (a link to one parent and one child). It turns out that we only need to store the node     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) at the beginning of this path (and associate some meta-data with it to represent the removed nodes) and attach the subtree rooted at its end to     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8). It is still possible for these compressed trees to have a linear height when given "bad" input points.

 

Although we trim a lot of the tree when we perform this compression, it is still possible to achieve logarithmic-time search, insertion, and deletion by taking advantage of [*Z*-order curves](./Z-order_curve). The *Z*-order curve maps each cell of the full quadtree (and hence even the compressed quadtree) in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time to a one-dimensional line (and maps it back in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time too), creating a total order on the elements. Therefore, we can store the quadtree in a data structure for ordered sets (in which we store the nodes of the tree). 

 

We must state a reasonable assumption before we continue: we assume that given two real numbers     α α  , β β  ∈ ∈  [ 0 , 1 )   {\displaystyle \alpha ,\beta \in [0,1)}  ![{\displaystyle \alpha ,\beta \in [0,1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6021592a035c2548997fb8d86328c3d063459fca) expressed as binary, we can compute in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time the index of the first bit in which they differ. We also assume that we can  compute in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time the lowest common ancestor of two points/cells in the quadtree and establish their relative *Z*-ordering, and we can compute the floor function in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time. 

 

With  these assumptions, point location of a given point     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) (i.e. determining the cell that would contain     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d)), insertion, and deletion operations can all be performed in     O ( log ⁡ ⁡   n  )   {\displaystyle O(\log {n})}  ![{\displaystyle O(\log {n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/653ab6d6fd99537d220f179d2591955ff4f37b99) time (i.e. the  time it takes to do a search in the underlying ordered set data structure).

 

To perform a point location for     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) (i.e. find its cell in the compressed tree):

 
1. Find the existing cell in the compressed tree that comes before     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) in the *Z*-order. Call this cell     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597).
2. If     q ∈ ∈  v   {\displaystyle q\in v}  ![{\displaystyle q\in v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/899b2c7b5a59ed5fa421d6d977e35814d1d37b5f), return     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597).
3. Else, find what would have been the lowest common ancestor of the point     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) and the cell     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) in an uncompressed quadtree. Call this ancestor cell     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8).
4. Find the existing cell in the compressed tree that comes before     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) in the *Z*-order and return it.

 

Without going into specific details, to perform insertions and deletions we first do a point location for the thing we want to insert/delete, and then insert/delete it. Care must be taken to reshape the tree as appropriate, creating and removing nodes as needed.

 

## Some common uses of quadtrees

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Quad_tree_bitmap.svg/500px-Quad_tree_bitmap.svg.png)](./File:Quad_tree_bitmap.svg)A bitmap and its compressed quadtree representation 
- Image representation
- [Image processing](./Quadtree#Image_processing_using_quadtrees)
- [Mesh generation](./Quadtree#Mesh_generation_using_quadtrees)[[14]](./Quadtree#cite_note-14)
- [Spatial indexing](./Spatial_index), point location queries, and range queries
- Efficient [collision detection](./Collision_detection) in two dimensions
- [View frustum culling](./Hidden_face_removal#Viewing_frustum_culling) of terrain data
- Storing sparse data, such as a formatting information for a [spreadsheet](./Spreadsheet)[[15]](./Quadtree#cite_note-15) or for some matrix calculations[*[citation needed](./Wikipedia:Citation_needed)*]
- Solution of multidimensional [fields](./Field_(physics)) ([computational fluid dynamics](./Computational_fluid_dynamics), [electromagnetism](./Electromagnetism))
- [Conway's Game of Life](./Conway's_Game_of_Life) simulation program.[[16]](./Quadtree#cite_note-16)
- [State estimation](./State_estimation)[[17]](./Quadtree#cite_note-17)
- Quadtrees are also used in the area of fractal image analysis
- [Maximum disjoint sets](./Maximum_disjoint_set#Fat_objects_with_arbitrary_sizes:_PTAS)

 

## Image processing using quadtrees

 

Quadtrees, particularly the [region quadtree](./Quadtree#Region_quadtree), have lent themselves well to image processing applications. We will limit our discussion to binary image data, though region quadtrees and the image processing operations performed on them are just as suitable for colour images.[[5]](./Quadtree#cite_note-Aluru2004-5)[[18]](./Quadtree#cite_note-:0-18)

 

### Image union / intersection

 

One of the advantages of using quadtrees for image manipulation is that the set operations of union and intersection can be done simply and quickly.[[5]](./Quadtree#cite_note-Aluru2004-5)[[19]](./Quadtree#cite_note-19)[[20]](./Quadtree#cite_note-20)[[21]](./Quadtree#cite_note-21) [[22]](./Quadtree#cite_note-22)
Given two binary images, the image union (also called *overlay*) produces an image wherein a pixel is black if either of the input images has a black pixel in the same location. That is, a pixel in the output image is white only when the corresponding pixel in *both* input images is white, otherwise the output pixel is black. Rather than do the operation pixel by pixel, we can compute the union more efficiently by leveraging the quadtree's ability to represent multiple pixels with a single node. For the purposes of discussion below, if a subtree contains both black and white pixels we will say that the root of that subtree is coloured grey.

 

The algorithm works by traversing the two input quadtrees (     T  1     {\displaystyle T_{1}}  ![{\displaystyle T_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f304724948a3ef606c4a92459e22b87a954d993) and      T  2     {\displaystyle T_{2}}  ![{\displaystyle T_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d1ba5f12fbb0ff766aec6e22148b429373608555)) while building the output quadtree     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0). Informally, the algorithm is as follows. Consider the nodes      v  1   ∈ ∈   T  1     {\displaystyle v_{1}\in T_{1}}  ![{\displaystyle v_{1}\in T_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e01cea50601988fb04d83193a115846ec18a7349) and       v  2   ∈ ∈   T  2     {\displaystyle v_{2}\in T_{2}}  ![{\displaystyle v_{2}\in T_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/177f07cab7f56d4ca5853833fda8cecc92037795) corresponding to the same region in the images.

 
- If      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a) or      v  2     {\displaystyle v_{2}}  ![{\displaystyle v_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb04c423c2cb809c30cac725befa14ffbf4c85f3) is black, the corresponding node is created in     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) and is colored black. If only one of them is black and the other is gray, the gray node will contain a subtree underneath. This subtree need not be traversed.
- If      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a) (respectively,      v  2     {\displaystyle v_{2}}  ![{\displaystyle v_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb04c423c2cb809c30cac725befa14ffbf4c85f3)) is white,      v  2     {\displaystyle v_{2}}  ![{\displaystyle v_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb04c423c2cb809c30cac725befa14ffbf4c85f3) (respectively,      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a)) and the subtree underneath it (if any) is copied to     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) .
- If both      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a) and      v  2     {\displaystyle v_{2}}  ![{\displaystyle v_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb04c423c2cb809c30cac725befa14ffbf4c85f3) are gray, then the corresponding children of      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a) and      v  2     {\displaystyle v_{2}}  ![{\displaystyle v_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb04c423c2cb809c30cac725befa14ffbf4c85f3) are considered.

 

While this algorithm works, it does not by itself guarantee a minimally sized quadtree. For example, consider the result if we were to union a checkerboard (where every tile is a pixel) of size       2  k   × ×   2  k     {\displaystyle 2^{k}\times 2^{k}}  ![{\displaystyle 2^{k}\times 2^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/74414f6e3b8d63d6dd77867ecfa6ff45b88296f4) with its complement. The result is a giant black square which should be represented by a quadtree with just the root node (coloured black), but instead the algorithm produces a full 4-ary tree of depth     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). To fix this, we perform a bottom-up traversal of the resulting quadtree where we check if the four children nodes have the same colour, in which case we replace their  parent with a leaf of the same colour.[[5]](./Quadtree#cite_note-Aluru2004-5)

 

The intersection of two images is almost the same algorithm. One way to think about the intersection of the two images is that we are doing a union with respect to the *white* pixels. As such, to  perform the intersection we swap the mentions of black and white in the union algorithm.

 

### Connected component labelling

 

Consider two neighbouring black pixels in a binary image. They are *adjacent* if they share a bounding horizontal or vertical edge. In general, two black pixels are *connected* if one can be  reached from the other by moving only to adjacent pixels (i.e. there is a path of black pixels between them where each consecutive pair is adjacent). Each maximal set of connected black pixels  is a *connected component*. Using the quadtree representation of images, [Samet](./Hanan_Samet)[[23]](./Quadtree#cite_note-23)  showed how we can find and label these connected components in time proportional to the size of the  quadtree.[[5]](./Quadtree#cite_note-Aluru2004-5)[[24]](./Quadtree#cite_note-:1-24) This algorithm can also be used for polygon colouring.

 

The algorithm works in three steps: 

 
1. establish the adjacency relationships between black pixels
2. process the equivalence relations from the first step to obtain one unique label for each  connected component
3. label the black pixels with the label associated with their connected component

 

To simplify the discussion, let us assume the children of a node in the quadtree follow the [*Z*-order](./Z-order_curve) (SW, NW, SE, NE). Since we can count on this structure, for any cell we know how to navigate the quadtree to find the adjacent cells in the different levels of the hierarchy.

 

Step one is accomplished with a [post-order traversal](./Tree_traversal#Post-order) of the quadtree. For each black leaf     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) we look at the node or nodes representing cells that are Northern neighbours and Eastern neighbours (i.e. the Northern and Eastern cells that share edges with the cell of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597)). Since the tree is organized in *Z*-order, we have  the invariant that the Southern and Western neighbours have already been taken care of and accounted for. Let the Northern or Eastern neighbour currently under consideration be     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8). If     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) represents black pixels:

 
- If only one of     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) or     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) has a label, assign that label to the other cell
- If neither of them have labels, create one and assign it to both of them
- If     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) and     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) have different labels, record this label equivalence and move on

 

Step two can be accomplished using the [union-find data structure](./Disjoint-set_data_structure).[[25]](./Quadtree#cite_note-25) We start with each unique label as a separate set. For every equivalence relation noted in the first step, we union the  corresponding sets. Afterwards, each distinct remaining set will be associated with a distinct connected component in the image.

 

Step three performs another post-order traversal. This time, for each black node     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) we use the union-find's *find* operation (with the old label of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597)) to find and assign     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) its new label (associated  with the connected component of which     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) is part).

 

## Mesh generation using quadtrees

 

This section summarizes a chapter from a book by Har-Peled and de Berg et al.[[26]](./Quadtree#cite_note-:2-26)[[27]](./Quadtree#cite_note-27)

 

[Mesh generation](./Mesh_generation) is essentially the [triangulation of a point set](./Point-set_triangulation) for which further processing may be performed. As such, it is desirable for the resulting triangulation to have certain properties (like non-uniformity, triangles that are not "too skinny", large triangles in sparse areas and small triangles in dense ones, etc.) to make further processing quicker and less error-prone. Quadtrees built on the point set can be used to create meshes with these desired properties.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Fig-mesh-gen-balanced-leaves.svg/250px-Fig-mesh-gen-balanced-leaves.svg.png)](./File:Fig-mesh-gen-balanced-leaves.svg)A balanced leaf has at most one corner in a side. 

Consider a leaf of the quadtree and its corresponding cell     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597). We say     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) is *balanced* (for mesh generation) if the cell's sides are intersected by the corner points of neighbouring cells at most once on each side. This  means that the quadtree levels of leaves adjacent to     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) differ by at most one from the level of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597). When this is true for all leaves, we say the whole quadtree is balanced (for mesh generation).

 

Consider the cell     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) and the     5 × ×  5   {\displaystyle 5\times 5}  ![{\displaystyle 5\times 5}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8dc635bb09101d63ece07af4a1a3883f75368dd8) neighbourhood of same-sized cells centred at     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597). We call this neighbourhood the *extended cluster*. We say the quadtree is *well-balanced* if it is balanced, and for every leaf     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) that contains a point of the point set, its extended cluster is also in the quadtree and the extended cluster contains no other point of the point set.

 

Creating the mesh is done as follows:

 
1. Build a quadtree on the input points.
2. Ensure the quadtree is balanced. For every leaf, if there is a neighbour that is too large, subdivide the neighbour. This is repeated until the tree is balanced. We also make sure that for a leaf with a point in it, the nodes for each leaf's extended cluster are in the tree.
3. For every leaf node     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) that contains a point, if the extended cluster contains another point, we further subdivide the tree and rebalance as necessary. If we needed to subdivide, for each child     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) we ensure the nodes of     u   {\displaystyle u}  ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8)'s extended cluster are in the tree (and re-balance as required).
4. Repeat the previous step until the tree is well-balanced.
5. Transform the quadtree into a triangulation.

 

We consider the corner points of the tree cells as vertices in our triangulation. Before the transformation step we have a bunch of boxes with points in some of them. The transformation step is done in the following manner: for each point, warp the closest corner of its cell to meet it and triangulate the resulting four quadrangles to make "nice" triangles (the interested reader is referred to chapter 12 of Har-Peled[[26]](./Quadtree#cite_note-:2-26) for more details on what makes "nice" triangles).

 

The remaining squares are triangulated according to some simple rules. For each regular square (no points within and no corner points in its sides), introduce the diagonal. Due to the way in which we separated points with the well-balancing property, no square with a corner intersecting a side is one that was warped. As such, we can triangulate squares with intersecting corners as follows. If there is one intersected side, the square becomes three triangles by adding the long diagonals connecting the intersection with opposite corners. If there are four intersected sides, we split the square in half by adding an edge between two of the four intersections, and then connect these two endpoints to the remaining two intersection points. For the other squares, we introduce a point in the middle and connect it to all four corners of the square as well as each intersection point.

 

At the end of it all, we have a nice triangulated mesh of our point set built from a quadtree.

 

## Pseudocode

 

The following pseudo code shows one means of implementing a quadtree which handles only points. There are other approaches available.

 

### Prerequisites

 

It is assumed these structures are used.

 
```
 // Simple coordinate object to represent points and vectors
 struct XY
 {
     float x;
     float y;
 
     function __construct(float _x, float _y) {...}
 }
 
 // Axis-aligned bounding box with half dimension and center
 struct AABB
 {
     XY center;
     float halfDimension;
 
     function __construct(XY _center, float _halfDimension) {...}
     function containsPoint(XY point) {...}
     function intersectsAABB(AABB other) {...}
 }

```
 

### QuadTree class

 

This class represents both one quad tree and the node where it is rooted.

 
```
 class QuadTree
 {
     // Arbitrary constant to indicate how many elements can be stored in this quad tree node
     constant int QT_NODE_CAPACITY = 4;
 
     // Axis-aligned bounding box stored as a center with half-dimensions
     // to represent the boundaries of this quad tree
     AABB boundary;
 
     // Points in this quad tree node
     Array of XY [size = QT_NODE_CAPACITY] points;
 
     // Children
     QuadTree* northWest;
     QuadTree* northEast;
     QuadTree* southWest;
     QuadTree* southEast;
 
     // Methods
     function __construct(AABB _boundary) {...}
     function insert(XY p) {...}
     function subdivide() {...} // create four children that fully divide this quad into four quads of equal area
     function queryRange(AABB range) {...}
 }

```
 

### Insertion

 

The following method inserts a point into the appropriate quad of a quadtree, splitting if necessary.

 
```
 class QuadTree
 {
     ...
   
     // Insert a point into the QuadTree
     function insert(XY p)
     {
         // Ignore objects that do not belong in this quad tree
         if (!boundary.containsPoint(p))
             return false; // object cannot be added
     
         // If there is space in this quad tree and if it doesn't have subdivisions, add the object here
         if (points.size < QT_NODE_CAPACITY && northWest == null)
         {
             points.append(p);
             return true;
         }
     
         // Otherwise, subdivide and then add the point to whichever node will accept it
         if (northWest == null)
             subdivide();
         // We have to add the points/data contained in this quad array to the new quads if we only want
         // the last node to hold the data
     
         if (northWest->insert(p)) return true;
         if (northEast->insert(p)) return true;
         if (southWest->insert(p)) return true;
         if (southEast->insert(p)) return true;
     
         // Otherwise, the point cannot be inserted for some unknown reason (this should never happen)
         return false;
     }
 }

```
 

### Query range

 

The following method finds all points contained within a range.

 
```
 class QuadTree
 {
     ...
   
     // Find all points that appear within a range
     function queryRange(AABB range)
     {
         // Prepare an array of results
         Array of XY pointsInRange;
     
         // Automatically abort if the range does not intersect this quad
         if (!boundary.intersectsAABB(range))
             return pointsInRange; // empty list
     
         // Check objects at this quad level
         for (int p = 0; p < points.size; p++)
         {
             if (range.containsPoint(points[p]))
                 pointsInRange.append(points[p]);
         }
     
         // Terminate here, if there are no children
         if (northWest == null)
             return pointsInRange;
     
         // Otherwise, add the points from the children
         pointsInRange.appendArray(northWest->queryRange(range));
         pointsInRange.appendArray(northEast->queryRange(range));
         pointsInRange.appendArray(southWest->queryRange(range));
         pointsInRange.appendArray(southEast->queryRange(range));
     
         return pointsInRange;
     }
 }

```
 

## See also

 
- [Adaptive mesh refinement](./Adaptive_mesh_refinement)
- [Binary space partitioning](./Binary_space_partitioning)
- [Binary tiling](./Binary_tiling)
- [*k*-d tree](./K-d_tree)
- [Octree](./Octree)
- [R-tree](./R-tree)
- [UB-tree](./UB-tree)
- [Spatial database](./Spatial_database)
- [Subpaving](./Subpaving)
- [Z-order curve](./Z-order_curve)

 

## References

 

Surveys by Aluru[[5]](./Quadtree#cite_note-Aluru2004-5) and Samet[[24]](./Quadtree#cite_note-:1-24)[[18]](./Quadtree#cite_note-:0-18) give a nice overview of quadtrees.

 

### Notes

  
1. [↑](./Quadtree#cite_ref-1) [Whitney, Hassler](./Hassler_Whitney) (1934). ["Analytic extensions of functions defined in closed sets"](https://doi.org/10.2307%2F1989708). *Transactions of the American Mathematical Society*. **36** (1). American Mathematical Society: 63–89. [doi](./Doi_(identifier)):[10.2307/1989708](https://doi.org/10.2307%2F1989708). [JSTOR](./JSTOR_(identifier)) [1989708](https://www.jstor.org/stable/1989708).
2. [↑](./Quadtree#cite_ref-2) Finkel, R. A.; Bentley, J. L. (1974). ["Quad trees a data structure for retrieval on composite keys"](https://www.researchgate.net/publication/220197855). *Acta Informatica*. **4** (1): 1–9. [doi](./Doi_(identifier)):[10.1007/BF00288933](https://doi.org/10.1007%2FBF00288933). [S2CID](./S2CID_(identifier)) [33019699](https://api.semanticscholar.org/CorpusID:33019699). Retrieved 6 November 2019.
3. [↑](./Quadtree#cite_ref-3) 
Milan Sonka, Vaclav Hlavac, Roger Boyle.
["Image Processing, Analysis, and Machine Vision"](https://books.google.com/books?id=DcETCgAAQBAJ).
2014.
p. 108-109.

4. [↑](./Quadtree#cite_ref-4) Finkel, R. A.; Bentley, J. L. (1974). "Quad Trees A Data Structure for Retrieval on Composite Keys". *Acta Informatica*. **4**. Springer-Verlag: 1–9. [doi](./Doi_(identifier)):[10.1007/bf00288933](https://doi.org/10.1007%2Fbf00288933). [S2CID](./S2CID_(identifier)) [33019699](https://api.semanticscholar.org/CorpusID:33019699).
5. [1](./Quadtree#cite_ref-Aluru2004_5-0) [2](./Quadtree#cite_ref-Aluru2004_5-1) [3](./Quadtree#cite_ref-Aluru2004_5-2) [4](./Quadtree#cite_ref-Aluru2004_5-3) [5](./Quadtree#cite_ref-Aluru2004_5-4) [6](./Quadtree#cite_ref-Aluru2004_5-5) Aluru, S. (2004). "Quadtrees and octrees". In D. Mehta and S. Sahni (ed.). *Handbook of Data Structures and Applications*. Chapman and Hall/CRC. pp. 19-1 -- 19-26. [ISBN](./ISBN_(identifier)) [978-1-58488-435-4](./Special:BookSources/978-1-58488-435-4).
6. [↑](./Quadtree#cite_ref-6) Alves, Sidiney G.; de Oliveira, Marcelo M. (2022). "Contact Process on Weighted Planar Stochastic Lattice". *[Journal of Statistical Mechanics](./Journal_of_Statistical_Mechanics:_Theory_and_Experiment)* (6): 063201. [arXiv](./ArXiv_(identifier)):[2203.06150](https://arxiv.org/abs/2203.06150). [Bibcode](./Bibcode_(identifier)):[2022JSMTE2022f3201A](https://ui.adsabs.harvard.edu/abs/2022JSMTE2022f3201A). [doi](./Doi_(identifier)):[10.1088/1742-5468/ac70dc](https://doi.org/10.1088%2F1742-5468%2Fac70dc).
7. [↑](./Quadtree#cite_ref-7) Orenstein, J. A. (1982). "Multidimensional tries used for associative searching". *Information Processing Letters*. **14** (4). Elsevier: 150–157. [doi](./Doi_(identifier)):[10.1016/0020-0190(82)90027-8](https://doi.org/10.1016%2F0020-0190%2882%2990027-8).
8. [↑](./Quadtree#cite_ref-8) Samet, H. (1984). ["The quadtree and related hierarchical data structures"](http://www.cs.umd.edu/~hjs/pubs/SameCSUR84-ocr.pdf) (PDF). *ACM Computing Surveys*. **16** (2). ACM: 187–260. [doi](./Doi_(identifier)):[10.1145/356924.356930](https://doi.org/10.1145%2F356924.356930). [S2CID](./S2CID_(identifier)) [10319214](https://api.semanticscholar.org/CorpusID:10319214).
9. [↑](./Quadtree#cite_ref-9) Warnock, J. E. (1969). "A hidden surface algorithm for computer generated halftone pictures". *Computer Science Department, University of Utah*. TR 4-15.
10. [↑](./Quadtree#cite_ref-10) Schneier, M. (1981). "Two hierarchical linear feature representations: edge pyramids and edge quadtrees". *Computer Graphics and Image Processing*. **17** (3). Elsevier: 211–224. [doi](./Doi_(identifier)):[10.1016/0146-664X(81)90002-2](https://doi.org/10.1016%2F0146-664X%2881%2990002-2).
11. [↑](./Quadtree#cite_ref-11) [Hanan Samet](./Hanan_Samet) and Robert Webber. "Storing a Collection of Polygons Using
Quadtrees". *ACM Transactions on Graphics* July 1985: 182-222. *InfoLAB*. Web. 23 March 2012
12. [↑](./Quadtree#cite_ref-12) Nelson, R. C.; Samet, H. (1986). ["A consistent hierarchical representation for vector data"](https://doi.org/10.1145%2F15886.15908). *ACM SIGGRAPH Computer Graphics*. **20** (4): 197–206. [doi](./Doi_(identifier)):[10.1145/15886.15908](https://doi.org/10.1145%2F15886.15908).
13. [↑](./Quadtree#cite_ref-13) [Har-Peled, S.](./Sariel_Har-Peled) (2011). "Quadtrees - Hierarchical Grids". *Geometric approximation algorithms*. Mathematical Surveys and Monographs Vol. 173, American mathematical society.
14. [↑](./Quadtree#cite_ref-14) Wanta, Damian; Smolik, Waldemar T.; Kryszyn, Jacek; Wróblewski, Przemysław; Midura, Mateusz (2021). ["A Finite Volume Method using a Quadtree Non-Uniform Structured Mesh for Modeling in Electrical Capacitance Tomography"](https://doi.org/10.1007%2Fs40010-021-00748-7). *Proceedings of the National Academy of Sciences, India Section A*. **92** (3): 443–452. [doi](./Doi_(identifier)):[10.1007/s40010-021-00748-7](https://doi.org/10.1007%2Fs40010-021-00748-7). [S2CID](./S2CID_(identifier)) [244224810](https://api.semanticscholar.org/CorpusID:244224810).
15. [↑](./Quadtree#cite_ref-15) Sestoft, Peter (2014). *Spreadsheet Implementation Technology: Basics and Extensions*. The MIT Press. pp. 60–63. [ISBN](./ISBN_(identifier)) [978-0-262-52664-7](./Special:BookSources/978-0-262-52664-7).
16. [↑](./Quadtree#cite_ref-16) Tomas G. Rokicki (2006-04-01). ["An Algorithm for Compressing Space and Time"](http://www.ddj.com/hpc-high-performance-computing/184406478). Retrieved 2009-05-20.
17. [↑](./Quadtree#cite_ref-17) Henning Eberhardt, Vesa Klumpp, Uwe D. Hanebeck, *Density Trees for Efficient Nonlinear State Estimation*, Proceedings of the 13th International Conference on Information Fusion, Edinburgh, United Kingdom, July, 2010.
18. [1](./Quadtree#cite_ref-:0_18-0) [2](./Quadtree#cite_ref-:0_18-1) Samet, H. (1989). "Hierarchical spatial data structures". *Symposium on Large Spatial Databases*: 191–212.
19. [↑](./Quadtree#cite_ref-19) Hunter, G. M. (1978). *Efficient Computation and Data Structures for Graphics*. Ph.D. dissertation, Department of Electrical Engineering and Computer Science, Princeton University.
20. [↑](./Quadtree#cite_ref-20) Hunter, G. M.; Steiglitz, K. (1979). "Operations on images using quad trees". *IEEE Transactions on Pattern Analysis and Machine Intelligence*. **2** (2): 145–153. [Bibcode](./Bibcode_(identifier)):[1979ITPAM...1..145H](https://ui.adsabs.harvard.edu/abs/1979ITPAM...1..145H). [doi](./Doi_(identifier)):[10.1109/tpami.1979.4766900](https://doi.org/10.1109%2Ftpami.1979.4766900). [PMID](./PMID_(identifier)) [21868843](https://pubmed.ncbi.nlm.nih.gov/21868843). [S2CID](./S2CID_(identifier)) [2544535](https://api.semanticscholar.org/CorpusID:2544535).
21. [↑](./Quadtree#cite_ref-21) Schneier, M. (1981). "Calculations of geometric properties using quadtrees". *Computer Graphics and Image Processing*. **16** (3): 296–302. [doi](./Doi_(identifier)):[10.1016/0146-664X(81)90042-3](https://doi.org/10.1016%2F0146-664X%2881%2990042-3).
22. [↑](./Quadtree#cite_ref-22) Mehta, Dinesh (2007). *Handbook of Data Structures and Applications*. Chapman and Hall/CRC Press. p. 397.
23. [↑](./Quadtree#cite_ref-23) [Samet, H.](./Hanan_Samet) (1981). "Connected component labeling using quadtrees". *Journal of the ACM*. **28** (3): 487–501. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.77.2573](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.77.2573). [doi](./Doi_(identifier)):[10.1145/322261.322267](https://doi.org/10.1145%2F322261.322267). [S2CID](./S2CID_(identifier)) [17485118](https://api.semanticscholar.org/CorpusID:17485118).
24. [1](./Quadtree#cite_ref-:1_24-0) [2](./Quadtree#cite_ref-:1_24-1) Samet, H. (1988). "An overview of quadtrees, octrees, and related hierarchical data structures". In Earnshaw, R. A. (ed.). *Theoretical Foundations of Computer Graphics and CAD*. Springer-Verlag. pp. 51–68.
25. [↑](./Quadtree#cite_ref-25) Tarjan, R. E. (1975). ["Efficiency of a good but not linear set union algorithm"](http://www.csd.uwo.ca/~eschost/Teaching/07-08/CS445a/p215-tarjan.pdf) (PDF). *Journal of the ACM*. **22** (2): 215–225. [doi](./Doi_(identifier)):[10.1145/321879.321884](https://doi.org/10.1145%2F321879.321884). [hdl](./Hdl_(identifier)):[1813/5942](https://hdl.handle.net/1813%2F5942). [S2CID](./S2CID_(identifier)) [11105749](https://api.semanticscholar.org/CorpusID:11105749).
26. [1](./Quadtree#cite_ref-:2_26-0) [2](./Quadtree#cite_ref-:2_26-1) Har-Peled, S. (2011). "Good Triangulations and Meshing". *Geometric approximation algorithms*. Mathematical Surveys and Monographs Vol. 173, American mathematical society.
27. [↑](./Quadtree#cite_ref-27) de Berg, M.; Cheong, O.; van Kreveld, M.; Overmars, M. H. (2008). "Quadtrees Non-Uniform Mesh Generation". *Computational Geometry Algorithms and Applications* (3rd ed.). Springer-Verlag.

 

### General references

 
1. [Raphael Finkel](./Raphael_Finkel) and [J.L. Bentley](./J.L._Bentley) (1974). "Quad Trees: A Data Structure for Retrieval on Composite Keys". *Acta Informatica*. **4** (1): 1–9. [doi](./Doi_(identifier)):[10.1007/BF00288933](https://doi.org/10.1007%2FBF00288933). [S2CID](./S2CID_(identifier)) [33019699](https://api.semanticscholar.org/CorpusID:33019699).
2. [Mark de Berg](./Mark_de_Berg), [Marc van Kreveld](./Marc_van_Kreveld), [Mark Overmars](./Mark_Overmars), and [Otfried Schwarzkopf](./Otfried_Schwarzkopf) (2000). [*Computational Geometry*](https://archive.org/details/computationalgeo00berg) (2nd revised ed.). [Springer-Verlag](./Springer-Verlag). [ISBN](./ISBN_(identifier)) [3-540-65620-0](./Special:BookSources/3-540-65620-0).`{{cite book}}`:  CS1 maint: multiple names: authors list ([link](./Category:CS1_maint:_multiple_names:_authors_list)) Chapter 14: Quadtrees: pp. 291–306.
3. [Samet, Hanan](./Hanan_Samet); Webber, Robert (July 1985). ["Storing a Collection of Polygons Using Quadtrees"](https://web.archive.org/web/20120617044827/http://infolab.usc.edu/csci585/Spring2008/den_ar/p182-samet.pdf) (PDF). Archived from [the original](http://infolab.usc.edu/csci585/Spring2008/den_ar/p182-samet.pdf) (PDF) on 17 June 2012. Retrieved 23 March 2012.

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |