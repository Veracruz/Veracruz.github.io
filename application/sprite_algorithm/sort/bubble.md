``` swift
var numbers = [2, 3, 5, 1, 7, 6, 9, 10, 4, 8]
    
for var i = 0; i < numbers.count; i++ {
    for var j = i + 1; j < numbers.count; j++ {
        if numbers[i] > numbers[j] {
            let temp = numbers[i]
            numbers[i] = numbers[j]
            numbers[j] = temp
        }       
    }
}
```