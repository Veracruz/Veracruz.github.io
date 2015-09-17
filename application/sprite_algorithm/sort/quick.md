``` swift
var numbers = [2, 3, 5, 1, 7, 6, 9, 10, 4, 8]

func qsort(start start: Int, end: Int) {
    var i = start
    var j = end
    let pivot = numbers[(i + j) / 2]
    while i < j {
        while numbers[i] < pivot {i++}
        while numbers[j] > pivot {j--}
        if i < j {
            let temp = numbers[i]
            numbers[i] = numbers[j]
            numbers[j] = temp
        }
    }
    if start < j {
        qsort(start: start, end: j)
    }
    if i + 1 < end {
        qsort(start: i + 1, end: end)
    }
}
    
qsort(start: 0, end: numbers.count - 1)
```