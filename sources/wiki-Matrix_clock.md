---
source: https://en.wikipedia.org/wiki/Matrix_clock
fetched: 2026-06-19
---

A **matrix clock** is a mechanism for capturing chronological and causal relationships in a [distributed system](./Distributed_system).

 

Matrix clocks are a generalization of the notion of [vector clocks](./Vector_clock).[[1]](./Matrix_clock#cite_note-ParallelDrummond-1) A matrix clock maintains a [vector](./Vector_(data_structure)) of the vector clocks for each communicating host.

 

Every time a message is exchanged, the sending host sends not only what it knows about the global state of [time](./Time), but also the state of time that it received from other hosts.

 

This allows establishing a lower bound on what other hosts know, and is useful in applications such as [checkpointing](./Checkpointing) and [garbage collection](./Garbage_collection_(computer_science)).

 

## References

  
1. [↑](./Matrix_clock#cite_ref-ParallelDrummond_1-0) Drummond, Lúcia M. A.; Barbosa, Valmir C. (2003). "On reducing the complexity of matrix clocks". *Parallel Computing*. **29** (7): 895–905. [arXiv](./ArXiv_(identifier)):[cs/0309042](https://arxiv.org/abs/cs/0309042). [doi](./Doi_(identifier)):[10.1016/S0167-8191(03)00066-8](https://doi.org/10.1016%2FS0167-8191%2803%2900066-8). [S2CID](./S2CID_(identifier)) [269009](https://api.semanticscholar.org/CorpusID:269009).

 

## See also

 
- [Lamport timestamps](./Lamport_timestamps)
- [Vector clock](./Vector_clock)
- [Version vector](./Version_vector)

 
|  | Thiscomputer sciencearticle is astub. You can help Wikipedia byadding missing information. |
| --- | --- |

- [v](./Template:Comp-sci-stub)
- [t](./Template_talk:Comp-sci-stub)
- [e](./Special:EditPage/Template:Comp-sci-stub)