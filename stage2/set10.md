1
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Grid.java
//@line:50
boolean isValid(Location loc);
```
在Grid类声明，分别在BoundedGrid和UnboundedGrid中实现

2
```
//@file: /GridWorldCode/framework/info/gridworld/grid/AbstructGrid.java
//@line:44
if (isValid(neighborLoc))
```
public ArrayList<Location> getValidAdjacentLocations(Location loc);
这个方法已经可以得到有效的临近方格，其它方法调用这个方法即可

3
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Grid.java
//@line:129
ArrayList<E> getNeighbors(Location loc);
//@file: /GridWorldCode/framework/info/gridworld/grid/AbstructGrid.java
//@line:28
public ArrayList<E> getNeighbors(Location loc)
```

4
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Grid.java
//@line:79, 107
E get(Location loc);
ArrayList<Location> getEmptyAdjacentLocations(Location loc);
```
作用不一样：
get传入位置，传出该位置的对象
getEmptyAdjacentLocations传入位置。传出该位置周围的对象位置，可以通过再次调用get获得具体的对象

5
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Grid.java
//@line:36,49
public ArrayList<Location> getValidAdjacentLocations(Location loc)
{
    ArrayList<Location> locs = new ArrayList<Location>();

    int d = Location.NORTH;
    for (int i = 0; i < Location.FULL_CIRCLE / Location.HALF_RIGHT; i++)
    {
        Location neighborLoc = loc.getAdjacentLocation(d);
        if (isValid(neighborLoc))
            locs.add(neighborLoc);
        d = d + Location.HALF_RIGHT;
    }
    return locs;
}
```
得到的位置仅包含正北、正南、正东、正西的相邻位置