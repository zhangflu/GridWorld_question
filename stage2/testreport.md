对designreport所要求的6种情况进行测试，思路是使用juint构造环境（放置对象），推测正确的运行后各对象的位置和方向，再用assertture验证

* a
```
//a. What will a jumper do if the location in front of it is empty, 
//	 but the location two cells in front contains a flower or a rock?
@Test
public void testa() {
    world.add(new Location(5, 5), j1);
    world.add(new Location(3, 5), r1);
    Location el = new Location(5, 5);
    int ed = j1.getDirection() + Location.HALF_RIGHT;
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
}
```

* b
```
//b. What will a jumper do if the location two cells 
//   in front of the jumper is out of the grid?
@Test
public void testb() {
    world.add(new Location(0, 0), j1);
    Location el = new Location(0, 0);
    int ed = j1.getDirection() + Location.HALF_RIGHT;
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
    ed = j1.getDirection() + Location.HALF_RIGHT;
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
    j1.act();
    el = new Location(0, 2);
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
}
```

* c
```
	
//c. What will a jumper do if it is facing an edge of the grid?
@Test
public void testc() {
    world.add(new Location(0, 0), j1);
    Location el = new Location(0, 0);
    int ed = j1.getDirection() + Location.HALF_RIGHT;
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
}
```

* d
```
//d. What will a jumper do if another actor (not a flower or a rock) is 
//   in the cell that is two cells in front of the jumper?
public void testd() {
    world.add(new Location(3, 3), j1);
    world.add(new Location(3, 5), j2);
    Location el = new Location(5, 5);
    int ed = j1.getDirection() + Location.HALF_RIGHT;
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
    ed = j1.getDirection() + Location.HALF_RIGHT;
    el = new Location(1, 5);
    j1.act();
    assertEquals(el, j1.getLocation());
    assertEquals(ed, j1.getDirection());
}
```

* e,f
```
//e. What will a jumper do if it encounters another jumper in its path?
//the same as d

//f. Are there any other tests the jumper needs to make?
//   forword one cell is Jumper, forword two cell is empty
@Test
public void testf() {
    world.add(new Location(2, 4), j1);
    j2.setDirection(Location.SOUTH);
    world.add(new Location(1, 4), j2);
    j1.act();
    j2.act();
    int ed1 = j1.getDirection();
    int ed2 = j2.getDirection();
    Location el1 = j1.getLocation();
    Location el2 = j2.getLocation();
    Location el3 = new Location(0, 4);
    Location el4 = new Location(3, 4);
    assertTrue(el1.equals(el3) && ed1 == Location.NORTH);        
    assertTrue(el2.equals(el4) && ed2 == Location.SOUTH);
}
```