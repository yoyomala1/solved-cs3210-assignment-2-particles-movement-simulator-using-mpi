Download Link: https://assignmentchef.com/product/solved-cs3210-assignment-2-particles-movement-simulator-using-mpi
<br>
Assignment 2 is designed to enhance your understanding of parallel programming with distributed memory (MPI). Apply a different parallelization model to implement the particle movement simulation.

Problem Scenario

In Assignment 1, you have implemented and parallelize a particle movement simulator using shared memory (OpenMP) and GPU programming (CUDA). In assignment 2, you need to implement in parallel the same particle movement simulator using MPI, and compare with your shared memory programs in terms of parallelization strategy and performance.

The requirements for the particle movement simulator are the same with those described in Assignment 1, sections on Problem Scenario, Input and Output, and Physics engine. Instead of implementing the particle movement simulator with OpenMP and CUDA, you are now tasked to model the particle movement simulator as a distributed memory system and implement it with MPI.

<h2>Reflection on Assignment 1 Implementation</h2>

Together with this assignment, we are releasing a few simple test cases and a particle visualizer that can be used to check the correctness of your implementations. Observe the correctness of your implementations for OpenMP and CUDA before starting your MPI implementation. For comparison purposes, you might want to fix/adjust your OpenMP and CUDA implementations if needed. Up to 3 bonus marks will be awarded if you are successful in fixing your bugs, depending on the extent of the fixes.

For comparison purposes, you are allowed to change your implementation for OpenMP and CUDA for a better comparison of results of the same strategy across various implementations. Up to 3 bonus marks will be awarded if you decide to change your Assignment 1 implementation, depending on the extent of the changes. (Note: at most 3 bonus marks in total can be accumulated for changes made to your Assignment

1).

Requirements for Assignment 1 mention that the collisions can happen anytime during the step. But some parallelization approaches discretized the simulation by assuming that collisions happen only in the beginning of a step, followed by movement the particles. Note that you are not expected to completely change the assumptions you have made in assignment 1 as long as your simulation looks visually accurate (no deduction will be applied if you keep the same assumptions for your MPI implementation). However, you should try to minimally fix your implementation if your implementation is visually incorrect.

<h2>Parallelization Approach for Assignment 2</h2>

The first approach that comes to mind might be to just port your solution from OpenMP to MPI (or CUDA to MPI). However, you must be aware of the different programming model, and try to make your implementation more efficient.

1

Many students have chosen to parallelize the detection of collision (i.e one thread per particle) for their Assignment 1. While this can be directly translated into MPI (i.e, one process per particle for collision detection), your implementation will not be efficient due to communication overhead. Hence, you should try to find a better suited parallelization approach for MPI.

The challenging part is to come up with a parallel implementation that scales when increasing input size, number of processes and hardware capabilities. As such, you might need to try several approaches to parallelize the algorithm and several parallel implementations. You are advised to retain your alternative implementations and explain the incremental improvements you have done. Clearly state in your README and report which is the approach you used for measurements (and you want to be graded on).

<strong>Additional Note: </strong>For your midterm, you have seen a method to increase the efficiency of finding nearby bodies in the N-body simulator by using a quadtree. Note that this is only valid because of spatial locality – in that case, we assume that there are non-negligible gravitational force between bodies when they are within a certain radius of each other. This is not true for the particle movement simulator – it is possible for a particle to collide with another particle far away from itself, provided that the velocity is high enough. Do not assume that spatial locality holds when you are attempting your parallelization of the particle movement simulation.

<h2>Running your Simulation</h2>

For MPI, run your experiments varying the input size (number of particles, surface, etc), the number of processes used, and the number of machines. For performance measurements, run each simulation at least 3 times and take the shortest execution time. You can use any number of machines from the lab for your measurements:

<ul>

 <li>Dell Optiplex 7050 (Intel Core i7-7700)</li>

 <li>Dell Precision 7820 (intel Xeon Silver 4114)</li>

</ul>