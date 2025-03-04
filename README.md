# ST-Matching 

This repository implements a map-matching algorithm for gps trajectories.

Its advantage is that it does not rely on spatial databases such as postgis.

So it's more flexible.

However, the format of the road network data and the raw gps trajectory must be the same as those in the shp/input folder.

You should hardly use it immediately, but you can adapt it to use.
## usage

python get_od_path.py

## result

![result1](https://github.com/zhuang-hao-ming/map-match/blob/master/images/1.jpg)


![result2](https://github.com/zhuang-hao-ming/map-match/blob/master/images/2.jpg)

## reference

1. [st-match](https://www.microsoft.com/en-us/research/publication/map-matching-for-low-sampling-rate-gps-trajectories/)
