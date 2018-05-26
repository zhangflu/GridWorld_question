1
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 46
makeMove(loc);
//@file: /GridWorldCode/projects/critters/ChameleonCritter.java
//@line: 50
public void makeMove(Location loc)
```
因为ChameleonCritter类重载了makeMove方法，makeMove方法被act()方法调用。

2
```
//@file: /GridWorldCode/projects/critters/ChameleonCritter.java
//@line: 50
public void makeMove(Location loc)
```
因为剩下的操作与父类makeMove方法完全相同，可以复用代码。

3
```
//@file: /GridWorldCode/projects/critters/ChameleonCritter.java
//@line: 50
public void makeMove(Location loc)
```
修改makeMove函数：
```
public void makeMove(Location loc)
{
    
    Location old_loc = getLocation();
    setDirection(getLocation().getDirectionToward(loc));
    super.makeMove(loc);
    Flower flower = new Flower(getColor());
    flower.putSelfInGrid(gr, old_loc);
}
```

4
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 56
public ArrayList<Actor> getActors()
```
因为操作与父类的方法完全相同，可以复用代码。

5
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 102
public Location getLocation()
```
Actor

6
```
//@file: /framework/info/gridworld/grid/actor/Actor.java
//@line: 92
public Grid<Actor> getGrid()
```
调用父类函数getGrid()