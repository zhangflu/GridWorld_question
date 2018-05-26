1
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 32~34
private Location location;
private int direction;
private Color color;
```
位置、方向、颜色

2
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 39~45
public Actor()
{
    color = Color.BLUE;
    direction = Location.NORTH;
    grid = null;
    location = null;
}
```
方向为正北、颜色为蓝色

3
因为不同的actor的同名函数会有完全一样的实现，定义成父类可以先实现出来，无需在子类再次定义

4
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 117~119
if (grid != null)
    throw new IllegalStateException(
            "This actor is already contained in a grid.");
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 117~119
if (grid == null)
    throw new IllegalStateException(
            "This actor is not contained in a grid.");

```
不能，会抛出异常IllegalStateException("This actor is already contained in a grid.")
不能，会抛出异常IllegalStateException("This actor is not contained in a grid.")
可以，因为它的私有变量grid的变化不会引发异常

5
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 80~85
public void setDirection(int newDirection)
{
    direction = newDirection % Location.FULL_CIRCLE;
    if (direction < 0)
        direction += Location.FULL_CIRCLE;
}
```
调用该对象的成员函数setDirection(90);