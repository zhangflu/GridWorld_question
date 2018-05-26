* a 顺时针每次旋转45度，直到前两格的第二格无障碍物
* b 顺时针每次旋转45度，直到前两格的第二格无障碍物
```
    /**
    * Moves the Jumper forward, putting a flower into the location it previously
    * occupied.
    */
public void move()
{
    Grid<Actor> gr = getGrid();
    if (gr == null)
        return;
    Location loc = getLocation();
    //Move twice
    Location next = loc.getAdjacentLocation(getDirection());
    next = next.getAdjacentLocation(getDirection());
    if (gr.isValid(next))
        moveTo(next);
    else
        removeSelfFromGrid();
}
```

* c 顺时针每次旋转45度，直到前两格的第二格无障碍物
* d 顺时针每次旋转45度，直到前两格的第二格无障碍物
* e 顺时针每次旋转45度，直到前两格的第二格无障碍物
* f 测试：面前一格有障碍物，面前两格无障碍物的情况
* ```
/**
    * Tests whether this Jumper can move forward into a location that is empty or
    * contains a flower.
    * @return true if this Jumper can move.
    */
public boolean canMove()
{
    Grid<Actor> gr = getGrid();
    if (gr == null)
        return false;
    Location loc = getLocation();
    Location next = loc.getAdjacentLocation(getDirection());
    next = next.getAdjacentLocation(getDirection());
    if (!gr.isValid(next))
        return false;
    Actor neighbor = gr.get(next);
    return (neighbor == null);
    // not ok to move onto any other actor
}
```