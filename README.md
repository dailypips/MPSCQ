# MPSCQ

This is an intrusive lock-free multiple-producer, single-consumer queue inspired by Dmitry Vyukov's implementation 
( [here](http://www.1024cores.net/home/lock-free-algorithms/queues/intrusive-mpsc-node-based-queue), and 
[here](https://www.google.com/url?q=https://groups.google.com/d/msg/lock-free/nvjCNJgb0bA/9eDuTeDcMXQJ&sa=D&ust=1459199281327000&usg=AFQjCNESQjG_pfvey8S35QKNIMll9JUzdw)).

There is a blocking and non-blocking version. In both cases the consumer only spins if the producer is blocked before 
performing `prev->next = &first;`. The while loops can be replaced with `return` statements to avoid unnecessary spinning
(e.g., to check other queues or perform other work until the producer is unblocked). 


Examples are provided in 'test.cpp' and 'testBlocking.cpp'. 
