英语班长乖乖挽起裙子怎么小说

#include "error.cuh"
#include <math.h>
#include <stdio.h>

#ifdef USE_DP
    typedef double real;
#else
    typedef float real;
#endif

const int NUM_REPEATS = 10;
const int N = 1 << 22;
const int M = sizeof(real) * N;
const int MAX_NUM_STREAMS = 64;
cudaStream_t streams[MAX_NUM_STREAMS];

void timing
(
    const real *h_x, const real *h_y, real *h_z,
    real *d_x, real *d_y, real *d_z,
    const int num
);

int main(void)
{
    real *h_x, *h_y, *h_z;
    CHECK(cudaMallocHost(&h_x, M));
    CHECK(cudaMallocHost(&h_y, M));
    CHECK(cudaMallocHost(&h_z, M));
    for (int n = 0; n < N; ++n)
    {
        h_x[n] = 1.23;
        h_y[n] = 2.34;
    }
