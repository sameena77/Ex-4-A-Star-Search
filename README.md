<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: SAMEENA J     </h3>
<h3>Register Number: 2305002019          </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
        ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
          successor.f = successor.g + successor.h

        iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

        iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)
  
    e) push q on the closed list
    end (while loop)

## PROGRAM
```python


import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("![033d2259-863c-4ced-8bb3-06666ec58ae3](https://github.com/user-attachments/assets/1502a65c-29c2-414c-a9ec-5c9da437512b)
Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")

```

## GRAPH

![033d2259-863c-4ced-8bb3-06666ec58ae3](https://github.com/user-attachments/assets/5aa3950f-d1c4-4f3c-bf0d-40c32165d8a6)

## INPUT

A B 3

A D 5

B C 4

C E 6

D F 1

E F 2

## Output

![33438fb4-d055-465c-a86a-7bae162b0dfb](https://github.com/user-attachments/assets/392ae7c4-8418-4c55-aa6b-a7e7314d403d)


## RESULT

Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.
