# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}

func applyKTimes(_ K: Int, _ closure: () -> ()) {
    for i in 0..<K {
        closure()
    }
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```


## Question 2

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`

```swift
let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]
let multiples = numbers.filter{ (a) -> Bool in return a % 3 == 0 }
print(multiples)
```

## Question 3

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`

```swift
let numbers = [4, 7, 1, 9, 6, 5, 6, 9]

let largestNum = numbers.reduce(numbers[0], { x, y in x > y ? x : y })
print(largestNum)
```

## Question 4

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`

```swift
let strings = ["We", "Heart", "Swift"]

let sentence = strings.reduce("", { x, y in x + " " + y })
print(sentence)
```


## Question 5

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

```swift
let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]

let sortedAlpha = cities.sorted { (city1, city2) -> Bool in
    return city1 < city2
}

let sortedSecondChar = cities.sorted { (city1, city2) -> Bool in
    let secChar = city1.index(after: city1.startIndex)
    return city1[secChar] < city2[secChar]
}

let sortedLength = cities.sorted { (city1, city2) -> Bool in
    return city1.count > city2.count
}
```


## Question 6

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

```swift
let ascendingPop = citiesWithPopulation.sorted { (city1, city2) -> Bool in
    return city1.1 < city2.1
}
```
b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.
```swift
let reverseAlphaLastChar = citiesWithPopulation.sorted { (city1, city2) -> Bool in
    return String(city1.0.reversed()) > String(city2.0.reversed())
}
```


## Question 7

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
var numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution

func numDivisors(_ num1: Int, _ num2: Int) -> Bool {
    var firstNumDivisors = 0
    var secondNumDivisors = 0
    
    for i in 1...num1 where num1 % i == 0 {
        firstNumDivisors += 1
    }
    for s in 1...num2 where num2 % s == 0 {
        secondNumDivisors += 1
    }

    let ascension = firstNumDivisors < secondNumDivisors ? num1 > num2 : num1 < num2
    
    return ascension
}

let sortedNums = numbers.sorted(by: numDivisors)
print(sortedNums)
```


## Question 8

Find the sum of the squares of all the odd numbers from `numbers` and then print it.

`var numbers = [1, 2, 3, 4, 5, 6]`

a. Write code that removes all the odd numbers from the array.

```swift
func removeOdd(_ numArr: [Int]) -> [Int] {
    var onlyEvens = [Int]()
    for index in 0..<numArr.count where numArr[index] % 2 == 0 {
        onlyEvens.append(numArr[index])
    }
    return onlyEvens
}
```

b. Write code that squares all the numbers in the array.

```swift
func squareNums(_ numArr: [Int]) -> [Int] {
    var squared = [Int]()
    for num in numArr {
        squared.append(num * num)
    }
    return squared
}
```

c. Write code that finds the sum of the array.

```swift
func sumNums(_ numArr: [Int]) -> [Int] {
    return [numArr.reduce(0, +)]
}
```

d. Now use `map`, `filter` and `reduce` to solve this problem.

```swift
numbers = [numbers.filter{ (num) -> Bool in return num % 2 == 1 }.map{ (num) -> Int in return num * num}.reduce(0, {x, y in x + y})]
```

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`


## Question 9

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
func forEach(_ array: [Int], _ closure: (Int) -> ()) {
    for i in 0..<array.count{
        closure(array[i])
    }
}

forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

Output:

```swift
1
4
9
16
```

## Question 10

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
func combineArrays(_ arr1: [Int], _ arr2: [Int], _ closure: (Int, Int) -> Int ) -> [Int] {
    var oneTrueArr = [Int]()
    for i in 0..<arr1.count {
        oneTrueArr.append(closure(arr1[i], arr2[i]))
    }
    return oneTrueArr
}


var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
let oneTrueArray = combineArrays(array1,array2) { $0 * $1 }

print(oneTrueArray)

```

Output: `[5,10,15,12]`


## Question 11

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let theInts = [1, 2, 3, 44, 555, 6600, 10763]

func intsToStrings(arr arr1: [Int], toString closure: (Int) -> String) -> [String] {
    var stringInts = [String]()
    for i in arr1 {
        stringInts.append(closure(i))
    }
    return stringInts
}

let asString: (Int) -> String = { (num) in return String(num) }

let evenOdd: (Int) -> String = { (num) in return num % 2 == 0 ? "even" : "odd" }

let englishWords: (Int) -> String = { (num) in
    let initialNumString = String(num)
    var finalNumString = ""
    
    for digit in initialNumString {
        switch digit {
        case "0":
            finalNumString += "zero "
        case "1":
            finalNumString += "one "
        case "2":
            finalNumString += "two "
        case "3":
            finalNumString += "three "
        case "4":
            finalNumString += "four "
        case "5":
            finalNumString += "five "
        case "6":
            finalNumString += "six "
        case "7":
            finalNumString += "seven "
        case "8":
            finalNumString += "eight "
        case "9":
            finalNumString += "nine "
        default:
            continue
        }
    }
    return finalNumString
}
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```


## Question 12

var myArray = [34,42,42,1,3,4,3,2,49]

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
myArray.sort(ascendingOrder)
let ascendingOrder = { (x: Int, y: Int) -> Bool in return x < y }
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
myArray.sort(descendingOrder)
let descendingOrder = { (x: Int, y: Int) -> Bool in return x > y }
```


## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

```swift
let ascensionByThird = { (arr1: [Int], arr2: [Int]) -> Bool in
    return arr1[2] < arr2[2]
}

let sortedArrayByThird = arrayOfArrays.sorted(by: ascensionByThird)

print(sortedArrayByThird)
```

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.

```swift
let ascensionByThird = { (arr1: [Int], arr2: [Int]) -> Bool in
    if arr1.count >= 3 && arr2.count >= 3{
        return arr1[2] < arr2[2]
    } else if arr1.count >= 3 {
        return true
    } else {
        return false
    }
}

let sortedArrayByThird = arrayOfArrays.sorted(by: ascensionByThird)
print(sortedArrayByThird)
```
## Question 14

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

```swift
var codeString = "aldfjaekwjnfaekjnf"
var arrCodeStringKeys: [Character] = Array(codeString)

let descendingOrder = { (x: Character, y: Character) -> Bool in
    let letterValues = [
        "a" : 54,
        "b" : 24,
        "c" : 42,
        "d" : 31,
        "e" : 35,
        "f" : 14,
        "g" : 15,
        "h" : 311,
        "i" : 312,
        "j" : 32,
        "k" : 93,
        "l" : 203,
        "m" : 212,
        "n" : 41,
        "o" : 102,
        "p" : 999,
        "q" : 1044,
        "r" : 404,
        "s" : 649,
        "t" : 414,
        "u" : 121,
        "v" : 838,
        "w" : 555,
        "x" : 1001,
        "y" : 123,
        "z" : 432
    ]
    return letterValues[String(x)]! > letterValues[String(y)]!
}


var sortedCodeString = String(arrCodeStringKeys.sorted(by: descendingOrder))

print(sortedCodeString)

```

b) Sort the string below in ascending order according the dictionary `letterValues`

```swift
var codeStringTwo = "znwemnrfewpiqn"
var arrCodeStringKeys: [Character] = Array(codeStringTwo)

let descendingOrder = { (x: Character, y: Character) -> Bool in
    let letterValues = [
        "a" : 54,
        "b" : 24,
        "c" : 42,
        "d" : 31,
        "e" : 35,
        "f" : 14,
        "g" : 15,
        "h" : 311,
        "i" : 312,
        "j" : 32,
        "k" : 93,
        "l" : 203,
        "m" : 212,
        "n" : 41,
        "o" : 102,
        "p" : 999,
        "q" : 1044,
        "r" : 404,
        "s" : 649,
        "t" : 414,
        "u" : 121,
        "v" : 838,
        "w" : 555,
        "x" : 1001,
        "y" : 123,
        "z" : 432
    ]
    return letterValues[String(x)]! < letterValues[String(y)]!
}


var sortedCodeString = arrCodeStringKeys.sorted(by: descendingOrder)

print(sortedCodeString)

```

## Question 15

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]

func sortAndFormatNames(_ arrNameTuples: [(String, String)]) {
    let sortLastNames: ((String, String), (String, String)) -> Bool = { (x, y) in return x.1 < y.1 }
    let sortedNames = arrNameTuples.sorted(by: sortLastNames)

    for name in sortedNames {
        print("\(name.1), \(name.0)")
    }
}

sortAndFormatNames(firstAndLastTuples)

```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc
```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`

```swift
func myFilter(arr arrDoubles: [Double], filter closure: (Double) -> Bool ) -> [Double] {
    var newArr = [Double]()
    for num in arrDoubles where closure(num) {
        newArr.append(num)
    }
    return newArr
}
```

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.

```swift
let biggerThanTen: (Double) -> Bool = { (x) -> Bool in return x >= 10 }
```

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.

```swift
let wholeNumber: (Double) -> Bool = { (x) -> Bool in return x.truncatingRemainder(dividingBy: 1.0) == 0 }
```

d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

```swift
let justEven: (Double) -> Bool = { (x) -> Bool in return Int(x) % 2 == 0 }
```

e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

```swift
let biggerThanTen = theDoubles.filter { (x) -> Bool in return x >= 10 }

let wholeNumber = theDoubles.filter { (x) -> Bool in return x.truncatingRemainder(dividingBy: 1) == 0 }

let justEven = theDoubles.filter { (x) -> Bool in return Int(x) % 2 == 0 }
```
Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```
