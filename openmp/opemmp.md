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
```
