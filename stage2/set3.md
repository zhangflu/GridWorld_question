1
```
//@file: /framework/info/gridworld/grid/Location.java
//@line: 43~54
public int getRow()
{
    return row;
}
```
使用方法getRow()。

2
```
//@file: /framework/info/gridworld/grid/Location.java
//@line: 205~212
public int getRow()
{
    return row;
}
```
false.

3
```
//@file: /framework/info/gridworld/grid/Location.java
//@line: 130~169
else if (adjustedDirection == SOUTH)
    dr = 1;
```
(4, 4)

4
```
//@file: /framework/info/gridworld/grid/Location.java
//@line: 178~195
public int getDirectionToward(Location target)
{
    int dx = target.getCol() - getCol();
    int dy = target.getRow() - getRow();
    // y axis points opposite to mathematical orientation
    int angle = (int) Math.toDegrees(Math.atan2(-dy, dx));

    // mathematical angle is counterclockwise from x-axis,
    // compass angle is clockwise from y-axis
    int compassAngle = RIGHT - angle;
    // prepare for truncating division by 45 degrees
    compassAngle += HALF_RIGHT / 2;
    // wrap negative angles
    if (compassAngle < 0)
        compassAngle += FULL_CIRCLE;
    // round to nearest multiple of 45
    return (compassAngle / HALF_RIGHT) * HALF_RIGHT;
}
```
180

5
```
//@file: /framework/info/gridworld/grid/Location.java
//@line: 130~169
public Location getAdjacentLocation(int direction)
{
    // reduce mod 360 and round to closest multiple of 45
    int adjustedDirection = (direction + HALF_RIGHT / 2) % FULL_CIRCLE;
    if (adjustedDirection < 0)
        adjustedDirection += FULL_CIRCLE;

    adjustedDirection = (adjustedDirection / HALF_RIGHT) * HALF_RIGHT;
    int dc = 0;
    int dr = 0;
    if (adjustedDirection == EAST)
        dc = 1;
    else if (adjustedDirection == SOUTHEAST)
    {
        dc = 1;
        dr = 1;
    }
    else if (adjustedDirection == SOUTH)
        dr = 1;
    else if (adjustedDirection == SOUTHWEST)
    {
        dc = -1;
        dr = 1;
    }
    else if (adjustedDirection == WEST)
        dc = -1;
    else if (adjustedDirection == NORTHWEST)
    {
        dc = -1;
        dr = -1;
    }
    else if (adjustedDirection == NORTH)
        dr = -1;
    else if (adjustedDirection == NORTHEAST)
    {
        dc = 1;
        dr = -1;
    }
    return new Location(getRow() + dr, getCol() + dc);
}
```
首先将角度转换为八个标准方向的其中一个（角度最接近那个），然后对应的八种方向，采取八种不同方式的x轴方向和y轴方向位移。