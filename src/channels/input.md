Rust uses asynchronous `channels` to allow communication between tasks.
Channels allow an unidirectional flow of information between two end-points:
the `Sender` and the `Receiver`.

{channels.rs}

This is a sample output, order may vary because of task scheduling.

``` bash
$ rustc channels.rs && ./channels
task number 1 finished
task number 3 finished
task number 4 finished
task number 2 finished
task number 0 finished
task number 1 reported
task number 2 reported
task number 0 reported
task number 3 reported
task number 4 reported
```

Albeit non obvious from the output above, channels are actually FIFO.

{fifo.rs}

The order is maintained, after removing the scheduler non-determinism.

``` bash
$ rustc fifo.rs && ./fifo
0
1
2
3
4
```
