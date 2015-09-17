#Prim
``` swift
var cost = [[ 0, 4, 0, 0, 0, 0, 0, 8, 0],
            [ 4, 0, 8, 0, 0, 0, 0,11, 0],
            [ 0, 8, 0, 7, 0, 4, 0, 0, 2],
            [ 0, 0, 7, 0, 9,14, 0, 0, 0],
            [ 0, 0, 0, 9, 0,10, 0, 0, 0],
            [ 0, 0, 4,14,10, 0, 2, 0, 0],
            [ 0, 0, 0, 0, 0, 2, 0, 1, 6],
            [ 8,11, 0, 0, 0, 0, 1, 0, 7],
            [ 0, 0, 2, 0, 0, 0, 6, 7, 0]]
    
    
for i in 0..<cost.count {
    for j in 0..<cost[i].count {
        if cost[i][j] == 0 {
            cost[i][j] = Int.max
        }
    }
}

var visited: [Bool] = []
var connected: [Int] = []
for _ in 0..<cost.count {
    visited.append(false)
}
for _ in 0...cost.count {
    connected.append(Int.max)
}
    
visited[0] = true
for i in 0..<cost.count {
    if cost[0][i] < Int.max {
        connected[i] = cost[0][i]
    }
}
    
for _ in 0..<cost.count - 1 {
    
    var next = cost.count
    for j in 0..<cost.count {
        if !visited[j] && connected[j] < connected[next] {
            next = j
        }
    }
    
    visited[next] = true
    
    for j in 0..<cost.count {
        if !visited[j] && cost[next][j] < Int.max {
            connected[j] = min(connected[j], cost[next][j])
        }
    }
    
}      
```
<br />

#Kruskal
``` swift
var cost = [[ 0, 4, 0, 0, 0, 0, 0, 8, 0],
            [ 4, 0, 8, 0, 0, 0, 0,11, 0],
            [ 0, 8, 0, 7, 0, 4, 0, 0, 2],
            [ 0, 0, 7, 0, 9,14, 0, 0, 0],
            [ 0, 0, 0, 9, 0,10, 0, 0, 0],
            [ 0, 0, 4,14,10, 0, 2, 0, 0],
            [ 0, 0, 0, 0, 0, 2, 0, 1, 6],
            [ 8,11, 0, 0, 0, 0, 1, 0, 7],
            [ 0, 0, 2, 0, 0, 0, 6, 7, 0]]

for i in 0..<cost.count {
    for j in 0..<cost[i].count {
        if cost[i][j] == 0 {
            cost[i][j] = Int.max
        }
    }
}

struct Edge {
    var point1: Int
    var point2: Int
    var cost: Int
}
    
var edges: [Edge] = []
    
for i in 0..<cost.count {
    for j in i..<cost[i].count {
        if cost[i][j] < Int.max {
            edges.append(Edge(point1: i, point2: j, cost: cost[i][j]))
        }
    }
}
    
edges.sortInPlace { (edge1: Edge, edge2: Edge) -> Bool in
    if edge1.cost > edge2.cost {
        return true
    }
    return false
}
    
for i in 0..<edges.count {
    print("\(edges[i].cost)")
}
    
var pointset: [[Bool]] = []
for i in 0..<cost.count {
    pointset.append([])
    for _ in 0..<cost.count {
        pointset[i].append(false)
    }
    pointset[i][i] = true
}
    
var ans: [Int] = []
    
var count = 0
    
while count < cost.count - 1 {
    let edge = edges.popLast()!
    var set1 = -1
    var set2 = -1
    for j in 0..<pointset.count {
        if pointset[j][edge.point1] {
            set1 = j
        }
        if pointset[j][edge.point2] {
            set2 = j
        }
    }
    if set1 != set2 {
        ans.append(edge.cost)
        for j in 0..<cost.count {
            pointset[set1][j] = pointset[set1][j] || pointset[set2][j]
        }
        pointset.removeAtIndex(set2)
        count++
    }
}
    
print("\(ans)")
```