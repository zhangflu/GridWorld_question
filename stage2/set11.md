1
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:41~44
if (rows <= 0)
    throw new IllegalArgumentException("rows <= 0");
if (cols <= 0)
    throw new IllegalArgumentException("cols <= 0");
```
在构造函数中，如果边界值小于或等于0，会抛出异常

2
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:53~58
 public int getNumCols()
{
    // Note: according to the constructor precondition, numRows() > 0, so
    // theGrid[0] is non-null.
    return occupantArray[0].length;
}
```
是occupantArray[0]的长度，因为numRows() > 0，occupantArray[0]不为null。

3
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:60~64
public boolean isValid(Location loc)
{
    return 0 <= loc.getRow() && loc.getRow() < getNumRows()
            && 0 <= loc.getCol() && loc.getCol() < getNumCols();
}
```
loc的row值和col值均小于对应的grid上界

**next**

1
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:68~74
ArrayList<Location> theLocations = new ArrayList<Location>();

// Look at all grid locations.
for (int r = 0; r < getNumRows(); r++)
{
    for (int c = 0; c < getNumCols(); c++)
    {
```
ArrayList<Location>，
O(n^2)

2
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:85~91
public E get(Location loc)
{
    if (!isValid(loc))
        throw new IllegalArgumentException("Location " + loc
                + " is not valid");
    return (E) occupantArray[loc.getRow()][loc.getCol()]; // unavoidable warning
}
```
E，对象的位置，O(1)

3
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:93~105
public E put(Location loc, E obj)
{
    if (!isValid(loc))
        throw new IllegalArgumentException("Location " + loc
                + " is not valid");
    if (obj == null)
        throw new NullPointerException("obj == null");

    // Add the object to the grid.
    E oldOccupant = get(loc);
    occupantArray[loc.getRow()][loc.getCol()] = obj;
    return oldOccupant;
}
```
位置不合法或放入的对象为空，O(1)

4
```
//@file: /GridWorldCode/framework/info/gridworld/grid/BoundedGrid.java
//@line:107~117
public E remove(Location loc)
{
    if (!isValid(loc))
        throw new IllegalArgumentException("Location " + loc
                + " is not valid");
    
    // Remove the object from the grid.
    E r = get(loc);
    occupantArray[loc.getRow()][loc.getCol()] = null;
    return r;
}
```
返回被移除的对象，返回null，O(1)。

5
在插入和删除对象时，效率很高；在查找的时候，效率较低；若地图尺寸很大（也包括为了实现无边界的情况），这种方法效率很低