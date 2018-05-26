1
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 98~99
if (!gr.isValid(next))
    return false;
```
grid的成员函数isValid

2
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 101
return (neighbor == null) || (neighbor instanceof Flower);
```
canMove的返回值，仅在相邻对象为空或花时返回true。

3
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 98
if (!gr.isValid(next))
```
isValid，用来判定将要移动的位置是否越界

4
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 97
Location next = loc.getAdjacentLocation(getDirection());
```
用来获得相邻位置的Location。

5
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 91
public boolean canMove()
```
Bug类

6
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 78~81
if (gr.isValid(next))
    moveTo(next);
else
    removeSelfFromGrid();
```
将自身从grid中移除

7
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 71,76
public void move()
Location loc = getLocation();
```
可以通过多次调用getLocation得到

8
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 82
Flower flower = new Flower(getColor());
```
在move()函数中，花的颜色由getColor()定义

9
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 80~83
else
    removeSelfFromGrid();
Flower flower = new Flower(getColor());
flower.putSelfInGrid(gr, loc);
```
会

10
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 74~75
if (gr == null)
    return;
```
除了Bug对象不在Grid中的情况，其它情况均会留下一朵花

11
```
//@file: /framework/info/gridworld/grid/actor/Bug.java
//@line: 63~65
public void turn()
{
    setDirection(getDirection() + Location.HALF_RIGHT);
}
```
4次。