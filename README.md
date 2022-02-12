# Lab: Multithreading Using `pthreads`

The purpose of this lab is for us to perform a standard computational task using threads. 
In particular, we will get our hands dirty with POSIX's `pthreads` by writing our own
routine for doing <i>matrix-vector multiplication</i>. This mathematical task is an essential subroutine of many
machine learning and data science algorithms.

## Matrix-Vector Multiplication
Let *A* be a *m*-by-*n* matrix (table of numbers). Let *x* be a *n*-by-*1* vector (array of *n* numbers). The *matrix-vector* multiplication *Ax* results in a *m*-by-*1* vector *y* defined as follows.
![Screenshot from 2022-02-12 02-20-32](https://user-images.githubusercontent.com/5934852/153705487-0600ad93-a10a-4390-aba5-6d197b21af69.png)
Although *A* is a 2-dimensional object, in our code, we have *flattened* *A* to be 1-dimension array of numbers of length *m x n*. This is a common and efficient way of representing multidimensional data.
## Serial Implementation
In *serial* (i.e., a single thread) build a *m*-by-*n* matrix *A* filled with random numbers, and a *n*-by-*1* vector *x* filled with random numbers. Then write a serial matrix-vector multiplication routine that returns *Ax = y*.

## Multithreaded Implementation
Use `pthreads` to perform the matrix-vector multiplication *Ax = y*. The number of threads to be used will be specified by the user, i.e., it will be in `argv[1]`. At first, you may assume that the number of threads equals *m*, the number of rows in your matrix *A*, but then you should write your program so that it balances the work to be done among the threads when the number of threads is less than the number of rows (such load balancing is needed for the programming assignment). 

When you finish, race your serial solution against your multithreaded solution for a large matrix. The larger you make your matrix, the more your multithreaded version should vastly outperform your serial implementation. For very large matrices, you will need to be careful about your implementation, i.e., watch out for integer overflow.

To begin, download the provided source code and use that as a skeleton. The skeleton code may not compile, so use this as a template to fill in the details of your implementation. If you get a `segfault`, you are probably not passing command-line arguments properly. It might be useful to review sample code in that already shows some basic written examples of how to use `pthreads`. Don't forget when using `pthreads`, we need to pass the `-lpthread` flag to `gcc` and `-lm` if you are using the math library. 
