1. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 43~54
if (steps < sideLength && canMove())
{
    move();
    steps++;
}
```
定义虫子在没有遇到阻碍（canMove()）的情况下，沿当前方向走的步数。

2. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 43~54
if (steps < sideLength && canMove())
{
    move();
    steps++;
}
else
{
    turn();
    turn();
    steps = 0;
}
```
用于记录虫子没有遇到障碍时走的步数，在步数到达sideLength或遇到障碍时清零。

3. 
```
//@file: GridWorldCode/framework/info/gridworld/actor/Bug.java
//@line: 62~65
public void turn()
{
    setDirection(getDirection() + Location.HALF_RIGHT);
}
```
调用一次为顺时针旋转45度，为了达到虫子在不受阻碍的情况下箱型运动的目的，需要调用两次旋转90度。

4. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 25
public class BoxBug extends Bug
```
因为BoxBug类继承Bug类，Bug类中用该方法。

5. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 34~38
```
是的，因为没有成员函数可以修改它的sideLength的值。

6. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 43~54
if (steps < sideLength && canMove())
{
    move();
    steps++;
}
else
{
    turn();
    turn();
    steps = 0;
}
```
可以，当不满足条件steps < sideLength && canMove()时，它就会转向

7. 
```
//@file: /projects/boxBug/BoxBug.java
//@line: 43~54
if (steps < sideLength && canMove())
{
    move();
    steps++;
}
else
{
    turn();
    turn();
    steps = 0;
}
```
当不满足条件steps < sideLength && canMove()时