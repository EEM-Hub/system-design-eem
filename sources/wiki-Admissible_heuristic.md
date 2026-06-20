---
source: https://en.wikipedia.org/wiki/Admissible_heuristic
fetched: 2026-06-19
---

Computer science pathfinding concept 

In [computer science](./Computer_science), specifically in [algorithms](./Algorithm) related to [pathfinding](./Pathfinding), a [heuristic function](./Heuristic_function) is said to be **admissible** if it never overestimates the cost of reaching the goal, i.e. the cost it estimates to reach the goal is not higher than the lowest possible cost from the current point in the path.[[1]](./Admissible_heuristic#cite_note-1) In other words, it should act as a lower bound.

 

It is related to the concept of [consistent heuristics](./Consistent_heuristic). While all consistent heuristics are admissible, not all admissible heuristics are consistent.

 

## Search algorithms

 

An admissible heuristic is used to estimate the cost of reaching the goal state in an [informed search algorithm](./Informed_search_algorithm). In order for a heuristic
to be admissible to the search problem, the estimated cost must always be lower than or equal to the actual cost of reaching the goal state. 
The search algorithm uses the admissible heuristic to find an estimated 
optimal path to the goal state from the current node. 
For example, in [A* search](./A*_search) the evaluation function (where 
    n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the current node) is:

 

    f ( n ) = g ( n ) + h ( n )   {\displaystyle f(n)=g(n)+h(n)}  ![{\displaystyle f(n)=g(n)+h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5c05c9af6fa9d56e8faf12460bf98ebf9f936581)

 

where

     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) = the evaluation function.     g ( n )   {\displaystyle g(n)}  ![{\displaystyle g(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4ad18070e494503403daf39398e711c1378348e) = the cost from the start node to the current node     h ( n )   {\displaystyle h(n)}  ![{\displaystyle h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/125976c5970a395422e1baf572a26f31ae5e0b7d) = estimated cost from current node to goal. 

    h ( n )   {\displaystyle h(n)}  ![{\displaystyle h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/125976c5970a395422e1baf572a26f31ae5e0b7d) is calculated using the heuristic 
function. With a non-admissible heuristic, the A* algorithm could 
overlook the optimal solution to a search problem due to an 
overestimation in     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973).

 

## Formulation

     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is a node     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) is a heuristic     h ( n )   {\displaystyle h(n)}  ![{\displaystyle h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/125976c5970a395422e1baf572a26f31ae5e0b7d) is cost indicated by     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) to reach a goal from     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)      h  ∗ ∗    ( n )   {\displaystyle h^{*}(n)}  ![{\displaystyle h^{*}(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1b7dc45e238088cbc45930cf3a4334256f2c17b2) is the optimal cost to reach a goal from     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)     h ( n )   {\displaystyle h(n)}  ![{\displaystyle h(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/125976c5970a395422e1baf572a26f31ae5e0b7d) is admissible if,     ∀ ∀  n   {\displaystyle \forall n}  ![{\displaystyle \forall n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/698d930c1b4873ed101572755416d9ff94b849ed)     h ( n ) ≤ ≤   h  ∗ ∗    ( n )   {\displaystyle h(n)\leq h^{*}(n)}  ![{\displaystyle h(n)\leq h^{*}(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7f7dc40bac4f8c0fb1eedb7500792cae3912e97c) 

## Construction

 

An admissible heuristic can be derived from a [relaxed](./Relaxation_(approximation))
version of the problem, or by information from pattern databases that store exact solutions to subproblems of the problem, or by using [inductive learning](./Inductive_transfer) methods.

 

## Examples

 

Two different examples of admissible heuristics apply to the [fifteen puzzle](./Fifteen_puzzle) problem:

 
- [Hamming distance](./Hamming_distance)
- [Manhattan distance](./Manhattan_distance)

 

The [Hamming distance](./Hamming_distance) is the total number of misplaced tiles. It is clear that this heuristic is admissible since the total number of moves to order the tiles correctly is at least the number of misplaced tiles (each tile not in place must be moved at least once). The cost (number of moves) to the goal (an ordered puzzle) is at least the [Hamming distance](./Hamming_distance) of the puzzle.

 

The Manhattan distance of a puzzle is defined as:

     h ( n ) =  ∑ ∑   all tiles     d i s t a n c e   (  tile, correct position  )   {\displaystyle h(n)=\sum _{\text{all tiles}}{\mathit {distance}}({\text{tile, correct position}})}  ![{\displaystyle h(n)=\sum _{\text{all tiles}}{\mathit {distance}}({\text{tile, correct position}})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c496b31499b953176a57deb4573a1aea5c1e82c7) 

Consider the puzzle below in which the player wishes to move each tile such that the numbers are ordered. The Manhattan distance is an admissible heuristic in this case because every tile will have to be moved at least the number of spots in between itself and its correct position.[[2]](./Admissible_heuristic#cite_note-Korf,2000-2)

 
| 43 | 61 | 30 | 81 |
| --- | --- | --- | --- |
| 72 | 123 | 93 | 144 |
| 153 | 132 | 14 | 54 |
| 24 | 101 | 111 |  |

 

The subscripts show the Manhattan distance for each tile. The total Manhattan distance for the shown puzzle is:

     h ( n ) = 3 + 1 + 0 + 1 + 2 + 3 + 3 + 4 + 3 + 2 + 4 + 4 + 4 + 1 + 1 = 36   {\displaystyle h(n)=3+1+0+1+2+3+3+4+3+2+4+4+4+1+1=36}  ![{\displaystyle h(n)=3+1+0+1+2+3+3+4+3+2+4+4+4+1+1=36}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e4a0e7c9de58758768740902a30b13c1af86cd84) 

## Optimality proof

 

If an admissible heuristic is used in an algorithm that, per iteration, progresses only the path of lowest evaluation (current cost + heuristic) of several candidate paths, terminates the moment its exploration reaches the goal and, crucially, closes all optimal paths before terminating (something that's possible with [A* search algorithm](./A*_search_algorithm) if special care isn't taken[[3]](./Admissible_heuristic#cite_note-Misconceptions-3)), then this algorithm can only terminate on an optimal path. To see why, consider the following [proof by contradiction](./Proof_by_contradiction):

 

Assume such an algorithm managed to terminate on a path T with a true cost **Ttrue** greater than the optimal path S with true cost **Strue**. This means that before terminating, the evaluated cost of T was less than or equal to the evaluated cost of S (or else S would have been picked). Denote these evaluated costs **Teval** and **Seval** respectively. The above can be summarized as follows,

 **Strue** < **Ttrue** **Teval** ≤ **Seval** 

If our heuristic is admissible it follows that at this penultimate step **Teval** = **Ttrue** because any increase on the true cost by the heuristic on T would be inadmissible and the heuristic cannot be negative. On the other hand, an admissible heuristic would require that **Seval** ≤ **Strue** which combined with the above inequalities gives us **Teval** < **Ttrue** and more specifically **Teval** ≠ **Ttrue**. As **Teval** and **Ttrue** cannot be both equal and unequal our assumption must have been false and so it must be impossible to terminate on a more costly than optimal path.

 

As an example,[[4]](./Admissible_heuristic#cite_note-4) let us say we have costs as follows:(the cost above/below a node is the heuristic, the cost at an edge is the actual cost)

 
```
 0     10   0   100   0
START ----  O  ----- GOAL
 |                   |
0|                   |100
 |                   | 
 O ------- O  ------ O
100   1    100   1   100
```
 

So clearly we would start off visiting the top middle node, since the expected total cost, i.e.     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973), is     10 + 0 = 10   {\displaystyle 10+0=10}  ![{\displaystyle 10+0=10}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e106ba23138be397a2b36969104753fb4f98a6f7). Then the goal would be a candidate, with     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) equal to     10 + 100 + 0 = 110   {\displaystyle 10+100+0=110}  ![{\displaystyle 10+100+0=110}](https://wikimedia.org/api/rest_v1/media/math/render/svg/645015d3dbdc18e1e593f51158a06e48c0bbe504). Then we would clearly pick the bottom nodes one after the other, followed by the updated goal, since they all have     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) lower than the     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) of the current goal, i.e. their     f ( n )   {\displaystyle f(n)}  ![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) is     100 , 101 , 102 , 102   {\displaystyle 100,101,102,102}  ![{\displaystyle 100,101,102,102}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c4eaf823c85aded3303a6b3ad1c3184d54914822). So even though the goal was a candidate, we could not pick it because there were still better paths out there. This way, an admissible heuristic can ensure optimality.

 

However, note that although an admissible heuristic can guarantee final optimality, it is not necessarily efficient.

 

## See also

 
- [Consistent heuristic](./Consistent_heuristic)
- [Heuristic function](./Heuristic_function)
- [Search algorithm](./Search_algorithm)

 

## References

  
1. [↑](./Admissible_heuristic#cite_ref-1) Russell, S.J.; Norvig, P. (2002). *[Artificial Intelligence: A Modern Approach](./Artificial_Intelligence:_A_Modern_Approach)*. Prentice Hall. [ISBN](./ISBN_(identifier)) [0-13-790395-2](./Special:BookSources/0-13-790395-2).
2. [↑](./Admissible_heuristic#cite_ref-Korf,2000_2-0) [Korf, Richard E.](./Richard_E._Korf) (2000), ["Recent progress in the design and analysis of admissible heuristic functions"](https://www.aaai.org/Papers/AAAI/2000/AAAI00-212.pdf) (PDF), in Choueiry, Berthe Y.; Walsh, Toby (eds.), *Abstraction, Reformulation, and Approximation: 4th International Symposium, SARA 2000 Horseshoe Bay, USA, July 26-29, 2000 Proceedings*, vol. 1864, Springer, pp. 45–55, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.124.817](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.124.817), [doi](./Doi_(identifier)):[10.1007/3-540-44914-0_3](https://doi.org/10.1007%2F3-540-44914-0_3), [ISBN](./ISBN_(identifier)) [978-3-540-67839-7](./Special:BookSources/978-3-540-67839-7), retrieved 2010-04-26
3. [↑](./Admissible_heuristic#cite_ref-Misconceptions_3-0) Holte, Robert (2005). ["Common Misconceptions Concerning Heuristic Search"](https://web.archive.org/web/20220801183131/https://aaai.org/ocs/index.php/SOCS/SOCS10/paper/view/2073). *Proceedings of the Third Annual Symposium on Combinatorial Search (SoCS)*. Archived from [the original](https://aaai.org/ocs/index.php/SOCS/SOCS10/paper/view/2073) on 2022-08-01. Retrieved 2021-07-10.
4. [↑](./Admissible_heuristic#cite_ref-4) ["Why do admissable [*sic*] heuristics guarantee optimality?"](https://stackoverflow.com/questions/23970588/why-do-admissable-heuristics-guarantee-optimality). algorithm. *Stack Overflow*. Retrieved 2018-12-11.