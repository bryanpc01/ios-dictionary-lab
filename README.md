# Dictionaries lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

- Create an instance of a dictionary called `citiesDict` that maps 3 countries to their capital cities.

- Add two more countries to your dictionary.

- Translate at least 3 of the capital names into another language.

```swift
// Create an instance of a dictionary called `citiesDict` that maps 3 countries to their capital cities.
var citiesDict = ["Kenya" : "Nairobi", "Nigeria" : "Abuja", "Liberia" : "Monrovia"]
print(citiesDict)

// Add two more countries to your dictionary.
citiesDict["Tanzania"] = "Dodoma"
citiesDict["Zimbabwe"] = "Harare"
print(citiesDict)

// Translate at least 3 of the capital names into another language.
if let harareTranslation = citiesDict["Zimbabwe"], let dodomaTranslation = citiesDict["Tanzania"], let nairobiTranslation = citiesDict["Kenya"] {
    print(harareTranslation,"is ሐረር in Amharic.")
    print(dodomaTranslation,"is ዶዶማ in Amharic.")
    print(nairobiTranslation,"is ናይሮቢ in Amharic.")
}
```


## Question 2

`var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]`

- Using `someDict`, add together the values associated with "Three" and "Five" and print the result.

- Add values to the dictionary for the keys "Six" and "Seven".

- Make a key called `productUpToSeven` and set its value equal to the product of all the values.

- Make a key called `sumUpToSix` and set its value equal to the sum of the keys "One", "Two", "Three", "Four", "Five" and "Six".

- Remove the new keys made in the previous two steps

- Add 2 to every value inside of `someDict`.


```swift
var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]

// Using `someDict`, add together the values associated with "Three" and "Five" and print the result.
if let valueInThree = someDict["Three"], let valueInFive = someDict["Five"] {
    let sum = valueInThree + valueInFive
    print("The sum of the value in \'Three\' and \'Five\' is: \(sum)")
}

// Add values to the dictionary for the keys "Six" and "Seven".
someDict["Six"] = 36
someDict["Seven"] = 49

// Make a key called `productUpToSeven` and set its value equal to the product of all the values.
var product = 1
for value in someDict.values {
    product *= value
}
someDict["productUpToSeven"] = product

// Make a key called `sumUpToSix` and set its value equal to the sum of the keys "One", "Two", "Three", "Four", "Five" and "Six".
var sumToSix = 0
for (key,value) in someDict where key != "productUpToSeven" && key != "Seven"{
    sumToSix += value
}
someDict["sumUpToSix"] = sumToSix
print(someDict)

// Remove the new keys made in the previous two steps
someDict.removeValue(forKey: "sumUpToSix")
someDict.removeValue(forKey: "productUpToSeven")
print(someDict)

// Add 2 to every value inside of `someDict`.
for (key,value) in someDict {
    someDict[key] = value + 2
}
print(someDict)
```

## Question 3

Create a variable that is explicitly typed as a dictionary that maps strings to floating point numbers. Initialize the variable to the data shown in the table below which lists an author name and their comprehensibility score.

| Author Name |	Score |
| :--: | :--: |
| Mark Twain |	8.9 |
| Nathaniel Hawthorne	| 5.1 |
| John Steinbeck	| 2.3 |
| C.S. Lewis | 9.9 |
| Jon Krakauer | 6.1 |

Using the dictionary created in the previous problem, do the following:

- Print out the floating-point score for “John Steinbeck”.

- Add an additional author named “Erik Larson” with an assigned score of 9.2.

- Write an if/else statement that compares the score of John Krakaur with Mark Twain. Print out the name of the author with the highest score.

- Use a for-loop to iterate through the dictionary you created at the beginning of the problem, and print out the content in the form of key: value, one entry per line.

```swift
// Create a variable that is explicitly typed as a dictionary that maps strings to floating point numbers.
var authorScore: [String : Double]

// Initialize the variable to the data shown in the table below which lists an author name and their comprehensibility score.
authorScore = ["Mark Twain" : 8.9, "Nathaniel Hawthorne" : 5.1, "John Steinbeck" : 2.3, "C.S. Lewis" : 9.9, "Jon Krakauer" : 6.1]

// Print out the floating-point score for “John Steinbeck”.
if let john = authorScore["John Steinbeck"] {
    print("John Steinbeck has a score of \(john)")
}

// Add an additional author named “Erik Larson” with an assigned score of 9.2.
authorScore["Erik Larson"] = 9.2

// Write an if/else statement that compares the score of Jon Krakauer with Mark Twain. Print out the name of the author with the highest score.
if let jonScore = authorScore["Jon Krakauer"], let markScore = authorScore["Mark Twain"] {
    if jonScore > markScore {
        print("Jon Krakauer has a higher score than Mark Twain.")
    } else {
        print("Mark Twain has a higher score than John Krakauer.")
    }
}

// Use a for-loop to iterate through the dictionary you created at the beginning of the problem, and print out the content in the form of key: value, one entry per line.
for (key, value) in authorScore {
    print("\(key): \(value)")
}
```


## Question 4

You are given a dictionary code of type [String:String] which has values for all lowercase letters. The code dictionary represents a way to encode a message. For example if code["a"] = "z" and code["b"] = "x" the encoded version if "ababa" will be "zxzxz". You are also given a message which contains only lowercase letters and spaces. Use the `code` dictionary below to encode the message and print it.

```swift
var code = [
    "a" : "b",
    "b" : "c",
    "c" : "d",
    "d" : "e",
    "e" : "f",
    "f" : "g",
    "g" : "h",
    "h" : "i",
    "i" : "j",
    "j" : "k",
    "k" : "l",
    "l" : "m",
    "m" : "n",
    "n" : "o",
    "o" : "p",
    "p" : "q",
    "q" : "r",
    "r" : "s",
    "s" : "t",
    "t" : "u",
    "u" : "v",
    "v" : "w",
    "w" : "x",
    "x" : "y",
    "y" : "z",
    "z" : "a"
]

var message = "hello world"
var outPutMessage = ""

// add spaces to the dictionary
code[" "] = " "

// loop through the message
for character in message {
    // loop through the dictionary to find the encoded letter
    for (key, value) in code where String(character) == key {
        outPutMessage += value
        continue
    }
}

print(outPutMessage)
```

You are also given an `encodedMessage` which contains only lowercase letters and spaces. Use the `code` dictionary to decode the message and print it.
`var encodedMessage = "uijt nfttbhf jt ibse up sfbe"`

```swift
var encodedMessage = "uijt nfttbhf jt ibse up sfbe"
var decodedMessage = ""
for character in encodedMessage {
    for (key, value) in code where String(character) == value {
        decodedMessage += key
        continue
    }
}
print(decodedMessage)
```


## Question 5

You are given an array of dictionaries. Each dictionary in the array contains exactly 2 keys `“firstName”` and `“lastName”`. Create an array of strings called `firstNames` that contains only the values for `“firstName”` from each dictionary.

```swift
var people: [[String:String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen"
    ]
]
var firstNames = [String]()

for fullNamesDict in people {
    for (key, value) in fullNamesDict where key == "firstName"{
        firstNames.append(value)
    }
}
print(firstNames)

// Now, create an array of strings called `fullNames` that contains the values for `“firstName”` and `“lastName”` from the dictionary separated by a space.

var fullNames = [String]()

for fullNamesDict in people {
    let keys = fullNamesDict.keys.sorted()
    var name = ""
    for key in keys {
        if let nameString = fullNamesDict[key] {
            name += " \(nameString)"
        }
    }
    fullNames.append(name.trimmingCharacters(in: .whitespaces))
}
print(fullNames)
```

## Question 6

You are given an array of dictionaries. Each dictionary in the array describes the score of a person. Find the person with the best score and print his full name.

```swift
var peopleWithScores: [[String: String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton",
        "score": "13"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie",
        "score": "23"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera",
        "score": "10"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno",
        "score": "3"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen",
        "score": "16"
    ]
]

var topScorer = (fname: "", lname: "", score: "0")

for arrayOfDictionaries in peopleWithScores {
    let keys = arrayOfDictionaries.keys.sorted()
    var fname = "", lname = "", score = ""
    for key in keys{
        if key == "firstName", let fn = arrayOfDictionaries[key]{
            fname = fn
        }
        if key == "lastName", let ln = arrayOfDictionaries[key]{
            lname = ln
        }
        if key == "score", let sc = arrayOfDictionaries[key]{
            score = sc
        }
    }
    if let score = Int(score), let topScore = Int(topScorer.score), score > topScore {
        topScorer = (fname,lname,String(score))
    }
}

print("The best score, \(topScorer.score), is held by \(topScorer.fname) \(topScorer.lname).")

// Print out the dictionary above in the following format:  **full name - score**
var nameAndScore = (fname: "", lname: "", score: "")

for arrOfDictionaries in peopleWithScores {
    let keys = arrOfDictionaries.keys.sorted()
    var fname = "", lname = "", score = ""
    for key in keys{
        if key == "firstName", let fn = arrOfDictionaries[key]{
            fname = fn
        }
        if key == "lastName", let ln = arrOfDictionaries[key]{
            lname = ln
        }
        if key == "score", let sc = arrOfDictionaries[key]{
            score = sc
        }
    }
    print("\(fname) \(lname) - \(score)")
}
```


## Question 7

`var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]`

You are given an array of integers. The frequency of a number is the number of times it appears in the array. Find out the frequency of each one.

Print the numbers in ascending order followed by their frequency.

```swift
var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]

var frequencyOfNumbers = [Int : Int]()

numbers.sort()

var currentNum = numbers[0]
var counter = 0

for number in numbers {
    if number == currentNum {
        counter += 1
        frequencyOfNumbers[number] = counter
    } else {
        currentNum = number
        counter = 1
        frequencyOfNumbers[number] = counter
    }
}
let keys = frequencyOfNumbers.keys.sorted()
for key in keys {
    if let value = frequencyOfNumbers[key] {
        print("(\(key): \(value))", terminator: " ")
    }
}
```


## Question 8

Print the most common letter in the string below:

`var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."`


```swift
var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."

var myStringArray = Array(myString.lowercased())

var frequencyOfChars = [String : Int]()

myStringArray.sort()

var currentChar = myStringArray[0]
var counter = 0
var topValue = 0
var output = ("", 0)

let ommitedChars = [" ", "'", "."]

for character in myStringArray where !ommitedChars.contains(String(character)) {
    if character == currentChar {
        counter += 1
        frequencyOfChars[String(character)] = counter
    } else {
        currentChar = character
        counter = 1
        frequencyOfChars[String(character)] = counter
    }
    if counter > topValue {
        output = (String(currentChar), counter)
        topValue = counter
    }
}
print("\"\(output.0)\" has the most occurrences with \(output.1).")
```

## Question 9

Write code that creates a dictionary where the keys are Ints between 0 and 20 inclusive, and each key's value is its cube.

```swift
var cubedNumbers = [Int: Int]()
for number in 0...20 {
   cubedNumbers[number] = number * number * number
}

print(cubedNumbers)
```

## Question 10

Write code that iterates through `testStates` and prints out whether or not that key is in `statePop`.

```swift
let statePop = ["Alabama": 4.8, "Alaska": 0.7, "Arizona": 6.7, "Arkansas": 3.0]
let testStates = ["California","Arizona", "Alabama", "New Mexico"]

let statePopKeys = statePop.keys
for state in testStates {
    if statePopKeys.contains(state) {
        print("\(state) is a key in statePop.")
    } else {
        print("\(state) is not a key in statePop.")
    }
}
```


## Question 11

You are given the dictionary `deposits`, which maps a persons name to an array of deposits that have been made to their account.

a) Write code to to print the name and total amount deposited of the person who recieved the most money.

b) Create an array called `stolenCents`, iterate over deposits for each person and steal their cents! ... like Office Space or Superman 3. Calculate the decimal part of each value, add it to the `stolenCents` array and round down the value in the dict.

c) How much money did you steal?

```swift
var deposits: [String: [Double]] = [
 "Williams" : [300.65, 270.45, 24.70, 52.00, 99.99],
 "Cooper" : [200.56, 55.00, 600.78, 305.15, 410.76, 35.00],
 "Davies" : [400.98, 56.98, 300.00],
 "Clark" : [555.23, 45.67, 99.95, 80.76, 56.99, 46.50, 265.70],
 "Johnson" : [12.56, 300.00, 640.50, 255.60, 26.88]
]

// a) Write code to to print the name and total amount deposited of the person who recieved the most money.
let peopleMakingDeposits = deposits.keys
var mostMoney = ("", 0.0)

for person in peopleMakingDeposits {
    if let deposits = deposits[person] {
        var sum = 0.0
        for deposit in deposits {
            sum += deposit
        }
        if sum > mostMoney.1 {
            mostMoney = (person,sum)
        }
    }
}
print("Deposits Dict:",deposits, separator: "\n")
print(mostMoney.0,"has the most money with","\(String(format: "$%.02f", mostMoney.1))")

// b) Create an array called `stolenCents`, iterate over deposits for each person and steal their cents! ... like Office Space or Superman 3. Calculate the decimal part of each value, add it to the `stolenCents` array and round down the value in the dict.
var stolenCents = [String]()
var stolenCentsTotal = 0.0

for person in peopleMakingDeposits {
    if var depositsMade = deposits[person] {
        for (index,deposit) in depositsMade.enumerated() {
            let cents = deposit - floor(deposit)
            stolenCents.append(String(format: "$%.02f",cents))
            stolenCentsTotal += cents
            depositsMade[index] = floor(deposit)
        }
         deposits[person] = depositsMade
    }
}

print("Deposits Dict after editing:",deposits, separator: "\n")
print("Cents Taken Array:",stolenCents, separator: "\n")

// c) How much money did you steal?
print("Total Amount Taken:",String(format: "$%.02f", stolenCentsTotal), separator: "\n")
```


## Question 12

Print the second most common letter in the string below:

`var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."`

```swift
var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."

let charactersToOmmit = [" ", "'", "."]

var arrayOfMyString = Array(myString.lowercased().sorted())

var frequencyOfLetters = [Character: Int]()
var counter = 0
var currentLetter = arrayOfMyString[0]

for character in arrayOfMyString where !charactersToOmmit.contains(String(character)){
    if character == currentLetter {
        counter += 1
    } else {
        frequencyOfLetters[currentLetter] = counter
        currentLetter = character
        counter = 1
    }
}
// add final Letter and count
frequencyOfLetters[currentLetter] = counter

let arrayOfValues = frequencyOfLetters.values.sorted(by: >)
var secondMostLetter =  (Character(" "),Int.min)

for (key,value) in frequencyOfLetters where value == arrayOfValues[1] {
    secondMostLetter = (key, value)
}

print("\"\(secondMostLetter.0)\" has the second most values with \(secondMostLetter.1)")
```


## Question 13

Given the below 4 arrays of Ints,

a) create a new array, sorted in ascending order, that contains all the values without duplicates.

b) create another new array that contains unique values that appear in all 4 arrays.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]

// a) create a new array, sorted in ascending order, that contains all the values without duplicates.
var arrOfAllValues = [Int]()
var currentNum = Int.min
for number in (arr1+arr2+arr3+arr4).sorted() where number != currentNum {
    arrOfAllValues.append(number)
    currentNum = number
}
print("Sorted array without duplicates:",arrOfAllValues, separator: "\n")

// b) create another new array that contains unique values that appear in all 4 arrays.
var arrOfUniqueValuesInAllArrays = [Int]()
currentNum = Int.min
for number in arr1 where arr2.contains(number) && arr3.contains(number) && arr4.contains(number) {
    arrOfUniqueValuesInAllArrays.append(number)
}
print("Unique values that appear in all 4 arrays:",arrOfUniqueValuesInAllArrays, separator: "\n")
```


## Question 14

Given the following exert from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use `components(separatedBy:)` to break up the string into an array.

 - use `CharacterSet.punctuationCharacters` in union with any other characters you don't want in your array, like spaces and new lines.

 ```swift
let declarationOfIndependence = """
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.

We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""

let arrayOfWords = declarationOfIndependence.lowercased().components(separatedBy: CharacterSet([".", ";", "\n", " ", "!", "?", ","]))
var wordFrequency = [String: Int]()


for word in arrayOfWords where word.count > 5 {
    if let countOfWord = wordFrequency[word] {
        wordFrequency[word] = countOfWord + 1
    } else {
        wordFrequency[word] = 1
    }
}

var mostFrequentWord = ("", Int.min)

for (key,value) in wordFrequency where value > mostFrequentWord.1{
    mostFrequentWord = (key,value)
}

print("The most frequent word is \"\(mostFrequentWord.0)\" with a count of \(mostFrequentWord.1).")
```
