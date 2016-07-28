OpenMP Summary
====


```bash
# Exporting number of threads
export OMP_NUM_THREADS=`grep 'processor' /proc/cpuinfo | wc -l `
```


```c
// Parallel region
#pragma omp parallel
{
  // Some code here
}

// Basic funtions
omp_get_num_procs(); // Get number of cores
omp_get_thread_num(); // Get thread number
omp_get_num_threads(); // Get number of threads available in this region
omp_get_max_threads(); // Get total number of threads
```
