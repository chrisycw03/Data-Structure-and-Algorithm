# Description

You are given an array coordinates, coordinates[i] = [x, y], where [x, y] represents the coordinate of a point. Check if these points make a straight line in the XY plane.

# Constraints

- 2 <= coordinates.length <= 1000
- coordinates[i].length == 2
- -10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4
coordinates contains no duplicate point.

# Thoughts

- 以第一個座標為起點到其他點的斜率相同，則為共線。
	- (yi - y0) / (xi - x0) = const. --> (y1 - y0) * (xi - x0) = (x1 - x0) * (yi - y0)

```c
bool checkStraightLine(int** coordinates, int coordinatesSize, int* coordinatesColSize){
    int x_diff = coordinates[1][0] - coordinates[0][0];
    int y_diff = coordinates[1][1] - coordinates[0][1];
    for(int i = 2; i < coordinatesSize; i++){
        int x_diff2 = coordinates[i][0] - coordinates[0][0];
        int y_diff2 = coordinates[i][1] - coordinates[0][1];
        if(x_diff2 * y_diff != x_diff * y_diff2)
            return false;
    }

    return true;
}
```