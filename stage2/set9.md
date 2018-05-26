1
```
//@file: GridWorldCode/projects/critters/CrabCritter.java
//@line: 44~57
public ArrayList<Actor> getActors()
{
    ArrayList<Actor> actors = new ArrayList<Actor>();
    int[] dirs =
        { Location.AHEAD, Location.HALF_LEFT, Location.HALF_RIGHT };
    for (Location loc : getLocationsInDirections(dirs))
    {
        Actor a = getGrid().get(loc);
        if (a != null)
            actors.add(a);
    }

    return actors;
}
```
因为根据它的设定，它会吃掉它正前方、右前方、左前方的所有actors。

2
```
//@file: GridWorldCode/projects/critters/CrabCritter.java
//@line: 44~57
public ArrayList<Actor> getActors()
{
    ArrayList<Actor> actors = new ArrayList<Actor>();
    int[] dirs =
        { Location.AHEAD, Location.HALF_LEFT, Location.HALF_RIGHT };
    for (Location loc : getLocationsInDirections(dirs))
    {
        Actor a = getGrid().get(loc);
        if (a != null)
            actors.add(a);
    }

    return actors;
}
```
父类act()调用 getActors和processActors
重载的getActors将当前位置正前方、右前方、左前方的所有actors加入ArrayList
父类 processActors方法，会删除所有ArrayList中的actor
达到“吃掉”的效果
会全部吃掉，由上面的分析可得。

3
```
//@file: GridWorldCode/projects/critters/CrabCritter.java
//@line: 101~114
public ArrayList<Location> getLocationsInDirections(int[] directions)
{
    ArrayList<Location> locs = new ArrayList<Location>();
    Grid gr = getGrid();
    Location loc = getLocation();

    for (int d : directions)
    {
        Location neighborLoc = loc.getAdjacentLocation(getDirection() + d);
        if (gr.isValid(neighborLoc))
            locs.add(neighborLoc);
    }
    return locs;
}   
```
给定一组方向，得到该组方向对应的一组位置。

4
```
//@file: GridWorldCode/projects/critters/CrabCritter.java
//@line: 44~57
public ArrayList<Actor> getActors()
{
    ArrayList<Actor> actors = new ArrayList<Actor>();
    int[] dirs =
        { Location.AHEAD, Location.HALF_LEFT, Location.HALF_RIGHT };
    for (Location loc : getLocationsInDirections(dirs))
    {
        Actor a = getGrid().get(loc);
        if (a != null)
            actors.add(a);
    }

    return actors;
}
```
(4, 4), (4, 3), (4, 5)

5
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@file: GridWorldCode/projects/critters/CrabCritter.java
public void act();
public ArrayList<Actor> getActors();
public void processActors(ArrayList<Actor> actors);
public ArrayList<Location> getMoveLocations();
public Location selectMoveLocation(ArrayList<Location> locs);
public void makeMove(Location loc);
```
除了获得actors和得到移动位置、执行移动的方法不同，导致的调用上述三个方法的方法实现也不一样，其它完全一样。

6
```
//@file: GridWorldCode/projects/critters/CrabCritter.java
//@line:79
if (loc.equals(getLocation()))
```
当目标移动位置就是原位时，说明canMove为false，这时应该执行旋转。

7
```
//@file: /framework/info/gridworld/grid/actor/Critter.java
//@line:75
if (!(a instanceof Rock) && !(a instanceof Critter))
```
如代码所示
