##Why this fork?
I've written a dyn tree for a project I'm working on in C# wich was inspired by Box2D's. Looking at the source I got interested in trying a different broadphase approach. Box2D uses a buffer to store all moved proxies. Then makes a tree query for each to find candidates for contacts but those queries might return dublicates so the pairs have to be cached in another buffer and filtered using sort.

My approach does store the information of moved proxies in the tree itself. It allows you to iterate over all overlapping pairs of proxies where at least one had moved. (this iteratioin also clears the 'touched' flag)

The pros are:
- No dynamically growing Pair-Buffer or Move-Buffer (thus fewer memory allocations at runtime)
- No sorting required to find dublicates
- Less lines of code
- Should be faster in large, dynamic scenes (e.g. "Tumbler" or "Add Pair Stresstest")

The cons:
- There's a baseline cost proportional to the number of proxies whenever the number of moved proxies is > 0
- ? (im sure there are more)

I don't mean to imply my approach is better then the current one but for some it could be. I did it just for fun so don't critisize me too hard if I missed something obvious. (Not a Box2D user myself)

##About
Box2D is a 2D physics engine for games.

For help with Box2D, please visit http://www.box2d.org. There is a forum there where you may post your questions.

Please see Building.txt to learn how to build Box2D and run the testbed.

To run the demos, set "Testbed" as your startup project and press F5. Some test bed commands are:
- 'r' to reset the current test
- SPACE to launch a bomb
- arrow keys to pan
- 'x' and 'z' to zoom in/out
- use the mouse to click and drag objects

Erin Catto
http://www.box2d.org

