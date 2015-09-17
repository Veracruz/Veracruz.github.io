``` swift
class Node {
    var index: Int = -1
    var left: Node?
    var right: Node?
}
    
let rootNode = Node()
 
func preorderTraversal(node: Node) {

    print("\(node.index)")
    
    if let left = node.left {
        traversal(left)
    }
    if let right = node.right {
        traversal(right)
    }
}

func inorderTraversal(node: Node) {

    print("\(node.index)")
    
    if let left = node.left {
        traversal(left)
    }
    if let right = node.right {
        traversal(right)
    }
}

func postorderTraversal(node: Node) {

    print("\(node.index)")
    
    if let left = node.left {
        traversal(left)
    }
    if let right = node.right {
        traversal(right)
    }
}
    
preorderTraversal(rootNode)
inorderTraversal(rootNode)
postorderTraversal(rootNode)
```