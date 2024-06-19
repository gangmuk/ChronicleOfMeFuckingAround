# ChronicleOfMeFuckingAround
**Disclaimer: Don't be offended. I am the only one here offended by myself.**

This repo is for self-reflection. It archives records of me fucking around. 
It **could** be useful
1. for me to keep track of how much I fucked around.
2. as a list of bookmarks for someone who wants to fuck around more conveniently and efficiently.

Jun-19th-2024, Wed
```
Under these heavy workload conditions, as seen during genAI training in AI clusters, GPUs typically have a mean time between failures (MTBF) of 20,000 to 30,000 hours. That means that, in a cluster of 24,000 GPUs, one GPU may fail every hour and 15 minutes. This figure does not even include the failures of network switches and interconnects.
 
In addition, high-energy particles from cosmic rays and environmental neutrons interacting with silicon atoms could lead to bit flips (soft errors) in the Asics. Error-correcting code (ECC) protection can correct single-bit flips in the SRAMs. Most networking and GPU vendors these days provide close to 100% ECC protection for their SRAMs (as in #Express5, which offers 100% ECC protection). ECC not only corrects single-bit flops caused by soft errors but also extends the device's lifespan by correcting single-bit errors in read data due to degraded SRAM cells. HBM vendors also offer ECC protection for memory contents. However, providing similar protection for flops inside logic is impractical - this can result in silent failures with no indication.
 
How does training cope with these hardware errors? 🤔

The training state is typically checkpointed at regular intervals, usually at the boundaries of training iterations. The checkpoint frequency depends on the scale of the training cluster and the system's MTBF.

In the 24K GPU scenario, check-pointing must happen at least once an hour. It involves copying most of the GPU's gigabytes of memory contents to the CPU and, from there, to the storage system, which slows down training and adds a heavy burden on the storage fabric.

How do you reduce the overhead of checkpointing? 🤔

Some algorithms monitor training progress from the last checkpoint and use heuristic methods to decide between restarting from the previous checkpoint and the cost of a new checkpoint. Others use AI algorithms to monitor the health of GPUs, network elements, and links, triggering checkpoints if imminent failure is predicted. Asynchronous checkpointing allows training to continue while the state transfers from GPU to CPU.
 
Regardless of checkpoint frequency, each hardware failure increases the effective training time due to lost progress and the additional time required to detect failures, replace hardware, reinitialize the GPUs with checkpoint state, and restart all the software containers. The more frequent the errors, the longer the training duration.
 
Fault-tolerant implementations with error correction mechanisms such as FEC, ECC, and link-level retries, periodic scrubbing of the memories, and on a memory failure, restarting only affected training jobs instead of resetting the entire hardware are some of the techniques that allow systems to degrade performance gradually rather than fail suddenly...

As cluster sizes continue to grow, resilient networking/GPU hardware is more critical than ever for sustainable training!
```
