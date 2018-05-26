1
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 31~132
public void act();
public ArrayList<Actor> getActors();
public void processActors(ArrayList<Actor> actors);
public ArrayList<Location> getMoveLocations();
public Location selectMoveLocation(ArrayList<Location> locs);
public void makeMove(Location loc);
```
public void act();
public ArrayList<Actor> getActors();
public void processActors(ArrayList<Actor> actors);
public ArrayList<Location> getMoveLocations();
public Location selectMoveLocation(ArrayList<Location> locs);
public void makeMove(Location loc);

2
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 40~46
if (getGrid() == null)
    return;
ArrayList<Actor> actors = getActors();
processActors(actors);
ArrayList<Location> moveLocs = getMoveLocations();
Location loc = selectMoveLocation(moveLocs);
makeMove(loc);
```
1. 如果不在grid上，不作反应
2. 获取其它Actor信息
3. 获取可移动位置信息
4. 根据可移动位置的信息，选择要移动的目标位置
5. 移动到目标位置

3
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 58
return getGrid().getNeighbors(getLocation());
```
需要，因为不同的critter可能只需要特定类型actor的信息

4
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 71~78
public void processActors(ArrayList<Actor> actors)
{
    for (Actor a : actors)
    {
        if (!(a instanceof Rock) && !(a instanceof Critter))
            a.removeSelfFromGrid();
    }
}
```
在这个方法中，可以遍历分析所有取到的actors，然后做出相应的决策

5
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line: 88~131
public ArrayList<Location> getMoveLocations()
{
    return getGrid().getEmptyAdjacentLocations(getLocation());
}
public Location selectMoveLocation(ArrayList<Location> locs)
{
    int n = locs.size();
    if (n == 0)
        return getLocation();
    int r = (int) (Math.random() * n);
    return locs.get(r);
}
public void makeMove(Location loc)
{
    if (loc == null)
        removeSelfFromGrid();
    else
        moveTo(loc);
}
```
第一个方法得到可以移动的位置
第二个方法从第一步的位置中挑一个目标移动过去的位置
第三个方法执行移动

6
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
```
因为没有特有的私有变量，所以构造函数直接继承Actor即可