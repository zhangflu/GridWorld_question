1
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Location.java
//@line:218~221
public int hashCode()
{
    return getRow() * 3737 + getCol();
}
//@line:234~246
public int compareTo(Object other)
{
    Location otherLoc = (Location) other;
    if (getRow() < otherLoc.getRow())
        return -1;
    if (getRow() > otherLoc.getRow())
        return 1;
    if (getCol() < otherLoc.getCol())
        return -1;
    if (getCol() > otherLoc.getCol())
        return 1;
    return 0;
}
```
使用hashmap需要定义hashcode方法；
使用treemap需要实现comparable接口；
Location类均满足条件

2
HashMap只允许键、值均为null的情况，因为boundedgrid中的储存数据结构时数组，允许null存入

3
```
//@file: /GridWorldCode/framework/info/gridworld/grid/Unboundedgrid.java
//@line:66~87

public E get(Location loc)
{
    if (loc == null)
        throw new NullPointerException("loc == null");
    return occupantMap.get(loc);
}

public E put(Location loc, E obj)
{
    if (loc == null)
        throw new NullPointerException("loc == null");
    if (obj == null)
        throw new NullPointerException("obj == null");
    return occupantMap.put(loc, obj);
}

public E remove(Location loc)
{
    if (loc == null)
        throw new NullPointerException("loc == null");
    return occupantMap.remove(loc);
}
```
均为O(1);
均为O(log2(n))

4
树形映射通过使用比较方法的定义，构建红黑树实现映射的功能；哈希通过使用哈希数组，辅以线性拉链法或其他方法解决溢出问题

5
可以，使getOccupiedLocations等时间复杂度为O(n^2)下降为O(1)
可以，实现方法同unboundedgrid，但注意检查值是否超越边界

q19
```
public Part5Grid2(int tr, int tc)
    {
    	//add bound limitation
        if (tr <= 0) {
            throw new IllegalArgumentException("tr <= 0");
        }
        if (tc <= 0) {
            throw new IllegalArgumentException("tc <= 0");
        }

        MAXCOL = tc;
        MAXROW = tr;
        occupantMap = new HashMap<Location, E>();
    }

    public int getNumRows()
    {
    	//add max bound
        return MAXROW;
    }

    public int getNumCols()
    {
    	//add max bound
        return MAXCOL;
    }

    public boolean isValid(Location loc)
    {
    	//add bound limitation
        return 0 <= loc.getRow() && loc.getRow() < getNumRows()
                && 0 <= loc.getCol() && loc.getCol() < getNumCols();
    }

    //the same as unbounded grid
    public ArrayList<Location> getOccupiedLocations();

    //the same as unbounded grid
    public E get(Location loc);

    //the same as unbounded grid
    public E put(Location loc, E obj);
   
    //the same as unbounded grid
    public E remove(Location loc)
```
如代码所示
通过增加边界判断实现

**n为对象总数**

O(1) O(n) O(1) O(log2(n))

O(1) O(n) O(1) O(log2(n))

O(1) O(n) O(1) O(log2(n))

O(n) O(n) O(n) O(n)

O(1) O(n) O(1) O(log2(n))

O(1) O(n) O(1) O(log2(n))

O(1) O(n) O(1) O(log2(n))


q20
**n为数组当前边长**
O(n^2)
O(1) （不需要resize）
O(n^2)