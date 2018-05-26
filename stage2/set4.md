1
```
//@file: /framework/info/gridworld/grid/Grid.java
//@line: 118, 107
ArrayList<Location> getOccupiedAdjacentLocations(Location loc);
ArrayList<Location> getEmptyAdjacentLocations(Location loc);
```
分别使用方法：
ArrayList<Location> getOccupiedAdjacentLocations(Location loc);
ArrayList<Location> getEmptyAdjacentLocations(Location loc);

2
```
//@file: /framework/info/gridworld/grid/Grid.java
//@line: 50
boolean isValid(Location loc);
```
调用方法 isValid(new Location(10, 10));

3
```
//@file: /framework/info/gridworld/grid/Grid.java
//@file: /framework/info/gridworld/grid/BoundedGrid.java
//@file: /framework/info/gridworld/grid/UnboundedGrid.java
```
因为结构如下：
Grid为AbstructGrid的接口，声明需要实现的函数，但不能实现，AbstructGrid是BoundedGrid和UnboundedGrid的父类，包含了那两个类共有的函数实现，BoundedGrid和UnboundedGrid分别实现功能实现不同的同名函数

4
Array（[]）：最高效；但是其容量固定且无法动态改变
ArrayList：  容量可动态增长；但牺牲效率；
无法确定数组大小时使用ArrayList