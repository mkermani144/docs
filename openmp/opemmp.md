OpenMP Summary
====


Setting environmental variables
----
```bash
# Exporting number of threads
export OMP_NUM_THREADS=`grep 'processor' /proc/cpuinfo | wc -l `
```


Compiling options
----
```gcc
gcc -fopenmp source.c -o source.exe
```


code
---
```c
// Parallel region
#pragma omp parallel
{
  // Some code here
}


// Setting number of threads from default to 4
//First method
#pragma omp parallel num_threads(4)
{

}
//Second method
omp_set_num_threads(4)
#pragma omp parallel
{

}


// Basic funtions
#include <omp.h> //OMP library
omp_get_num_procs(); // Get number of cores
omp_get_thread_num(); // Get thread number
omp_get_num_threads(); // Get number of threads available in this region
omp_get_max_threads(); // Get total number of threads
```
