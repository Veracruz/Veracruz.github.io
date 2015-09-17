``` swift
let numbers = [2, 3, 5, 1, 7, 6, 9, 10, 4, 8]

class Node {
    var number: Int
    var left: Node?
    var right: Node?
    
    init(number: Int) {
        self.number = number
    }
}
        
let rootNode = Node(number: self.numbers.first!)
    
func createBinarySortTree(node: Node, number: Int) {

    if number < node.number {
        if let leftNode = node.left {
            createBinarySortTree(leftNode, number: number)
        } else {
            node.left = Node(number: number)
        }
    } else {
        if let rightNode = node.right {
            createBinarySortTree(rightNode, number: number)
        } else {
            node.right = Node(number: number)
        }
    }
    
}
    
for var i = 1; i < numbers.count; i++ {
    createBinarySortTree(rootNode, number: numbers[i])
}
    
func printBinarySortTree(node: Node) {
    if let left = node.left {
        printBinarySortTree(left)
    }
    print("\(node.number) ", appendNewline: false)
    if let right = node.right {
        printBinarySortTree(right)
    }
}
    
printBinarySortTree(rootNode)
```