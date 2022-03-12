---
layout: default
---

[返回主页](https://luofaming.github.io/)

关于C++的一些学习笔记
* 用C++生成满足高斯分布的随机数
``` c++
double generateGaussianNoise(double mu, double sigma)
{
   const double epsilon = std::numeric_limits<double>::min();
   const double two_pi = 2.0*3.14159265358979323846;

   static double z0, z1;
   static bool generate;
   generate = !generate;

   if (!generate)
      return z1 * sigma + mu;

   double u1, u2;
   do
    {
      u1 = rand() * (1.0 / RAND_MAX);
      u2 = rand() * (1.0 / RAND_MAX);
    }
   while ( u1 <= epsilon );

   z0 = sqrt(-2.0 * log(u1)) * cos(two_pi * u2);
   z1 = sqrt(-2.0 * log(u1)) * sin(two_pi * u2);
   return z0 * sigma + mu;
}
```
