# 스위프트(Swift)
2014년 6월 2일 애플이 세계개발자대회(WWDC 2014)에서 C언어 그리고 Objective-C 언어의 좋은 점들을 취합한 것을 기반으로 C언어 호환성에 대한 제약없이 iOS와 OS X 앱을 개발하기 위한 언어입니다.						
애플 플랫폼 개발자들이 주로 이용해온 프로그래밍 언어인 "Object-C"를 대체할 것으로 예상된다.  
 
## Swift를 사용하면서 알아둘 사항						
* 다른 언어들과 유사하게 주석은 한줄 // comment, 블록 /* comment */를 사용합니다
* 명령문 마지막에 ;을 생략이 가능합니다. (JavaScript와 유사)
* if문 같이 조건문을 사용 할때 ()[괄호]가 생략이 가능합니다.
* 같은 모듈 내에서는 import를 사용하지 않아도 사용할 수 있습니다.  


## Swift 타입						
* 정수형 - int						
* 부동소숫점 - Double, Float						
* 논리자료형 - Boolean						
* 문자열 - String						
* 컬렉션 - Array, Dictionary						
* 값의 묶음 타입 - Tuple						
* 선택형 타입						


## 상수와 변수(Constants and Variables)						
상수 값은 한번 설정된 후로는 변경할 수 없으나, 변수는 이후에도 변경될 수 있음.
상수와 변수의 이름을 지정하기 위해서 유니코드를 포함한 어떤 문자든지 사용할 수 있음.						
```swift
상수의 keyword - let
변수의 keyword - var
```

```swift			
let maximumNumberOfLoginAttempts = 10						
var currentLoginAttempt = 0						
var 변수 = "你好世界"						
var 🐶 = "dog"						
```						


## 타입 명시(Type Annotations)	
Swift는 기본적으로 타입을 명시하지 않지만 명확하게 하기 위해 타입 명시를 할 수 있음.
상수 또는 변수 뒤에 콜론을 쓰고 한칸 띄우고 타입을 씀.		
```swift				
var welcomeMessage: String						
welcomeMessage = "Hello"						
```						

Swift는 긴 문자열에서 상수나 변수명을 대체문자로 사용해 Swift가 상수나 변수의 현재 값으로 즉시 대체할 수 있도록 문자열 해석 방식을 사용합니다.						
다음과 같이 이름을 괄호로 감싸고 이스케이프 시키기 위해서는 괄호 앞에 백슬래시를 써주면 됩니다.
```swift	
print("\(welcomeMessage)")						
```						


## 정수(Integers)						
최대값과 최소값은 각 정수 타입의 min과 max 속성에 접근하여 얻음.			
```swift
let minValue = UInt8.min // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max // maxValue is equal to 255, and is of type UInt8	
```											

	
## Int						
* 32-bit 플랫폼 - Int는 Int32와 같은 크기						
* 64-bit 플랫폼 - Int는 Int64와 같은 크기						
	

## Uint						
* 32-bit 플랫폼 - UInt는 UInt32와 같은 크기						
* 64-bit 플랫폼 - UInt는 UInt64와 같은 크기						
	

## 부동 소수점수						
* Double은 64-bit 부동 소수점수						
* Float은 32-bit 부동 소수점수						


## 튜플(Tuples)						
튜플은 여러 값들을 하나의 형태로 처리할 수 있는 타입입니다.				
튜플안의 여러값들은 어느 타입도 가능하고, 각각 동일한 타입일 필요도 없습니다.	
```swift
let http404Error = (404, "Not Found")						
```

튜플의 각 값은 상수나 변수로 분해하여 사용이 가능					
```swift	
let (statusCode, statusMessage) = http404Error						
print("The status code is \(statusCode)")						
// prints “The status code is 404”						
```

튜플 값 중에 몇 개만 필요하다면 무시할 부분에 밑줄(_)을 사용하면 됨.		
```swift					
let (justTheStatusCode, _) = http404Error						
print("The status code is \(justTheStatusCode)")						
// prints “The status code is 404”						
```
	
0번부터 시작하는 index 번호를 통해 각각의 투플 요소를 접근 가능.			
```swift				
print("The status code is \(http404Error.0)")						
// prints “The status code is 404”						
```

튜플에 각 요소들에 명명할 수 있음.	
```swift						
let http200Status = (statusCode: 200, description: "OK")						
print("The Status code is \(http200Status.statusCode)")						
// prints “The status code is 200”						
```						


## 옵셔널(Optionals)						
옵셔널은 값이 없을 수도 있는 상황에 사용됨.						
값이 있다면 상관없지만 값이 없다면 nil을 가짐.		
```swift	
let str = "Hello, playground"						
let convertedStr = Int(str)						
print("\(convertedStr)")						
// toInt는 Int? 타입의 영향을 주기 때문에 convertedStr는 옵셔널 타입을 가지게 됨	
// prints "nil"						

let possibleNumber = "123"						
let convertedNumber = Int(possibleNumber)				
print("\(convertedNumber)")						
// prints "123"						
```

변수 선언시 옵셔널 타입이지만 값을 할당하지 않은 경우 nil값을 자동으로 설정.	
```swift						
var surveyAnswer: String?						
// surveyAnswer is automatically set to nil						
```						


## If 조건문과 언래핑(If Statements and Forced Unwrapping)	
if 조건문에서 옵셔널이 값을 가지고 있는지 판단하기 위해 nil과 비교할 수 있음.	
옵셔널이 값을 가지고 있다면 nil과 같지 않음.	
```swift						
if convertedNumber != nil {						
   print("convertedNumber contains some integer value.")						
}						
// prints "convertedNumber contains some integer value."			
```			

옵셔널이 반드시 값을 가지고 있다고 확신하면 느낌표(!)를 옵셔널 이름 끝에 추가함. 						
이것을 옵셔널 값의 강제 언래핑이라고 함.						
즉, 느낌표(!)는 옵셔널에 값이 반드시 있고, 없으면 Error가 발생함.			
```swift				
var cabBeNil: Int?						
print(cabBeNil)						
// Compile is OK						

print(cabBeNil!)						
// Error, canBeNil is no value						
```						
	
## 옵셔널 바인딩(Optional Binding)						
옵셔널 바인딩은 값이 가지고 있는지를 찾고 임시 상수나 변수에 담아 사용할 수 있도록 함.						
if와 while문에서 옵셔널 값이 있는지를 확인.						
상수나 변수로부터 값을 가져와 if와 while문에 한번 사용하기 위함.
```swift	
if let actualNumber = Int(possibleNumber) {						
    print("\(possibleNumber) has an integer value of \(actualNumber)")						
} else {						
    print("\(possibleNumber) could not be converted to an integer")						
}						
// prints "123 has an integer value of 123"						
```


## 삼항 연산자(Ternary Conditional Operator)						
삼항 조건 연산자는 세 부분과 특별한 연산자이며 question ? answer1 : answer2 식으로 사용.						
question이 true 인지 false 인지에 따라 값을 반환하는 것이 다름.						
삼항 조건 연산자는 다음 코드를 축약함.	
```swift	
if question {						
    answer1						
} else {						
    answer2						
}						
```	
	
## Nil 결합 연산자(Nil Coalescing Operator)						
Nil 결합 연산자(a ?? b)는 옵셔널 a를 풀어 nil인지 확인하여 nil이면 b값을, nil이 아니면 a값을 반환함.						
항상 a는 옵셔널 타입이어야 하며 b는 a와 타입이 일치해야 함.						
```swift
let defaultColorName = "red"						
var userDefinedColorName: String?   // defaults to nil						

var colorNameToUse = userDefinedColorName ?? defaultColorName						
// userDefinedColorName 값이 nil이므로 colorNameToUse는 “red” 값을 가짐.						
```	
	
## 범위 연산자(Range Operators)						
### 닫힌 범위 연산자(Closed Range Operator)						
닫힌 범위 연산자(a...b)는 a에서 b까지 수행되는 범위로, a와 b 값을 포함함. a는 b보다 크면 안됨.						
닫힌 범위 연산자는 for-in 반복문과 같이 값 범위에서 반복해서 사용할 때 유용함.	
```swift
for index in 1...5 {						
    print("\(index) times 5 is \(index * 5)")						
}						
// 1 times 5 is 5						
// 2 times 5 is 10						
// 3 times 5 is 15						
// 4 times 5 is 20						
// 5 times 5 is 25						
```

### 반 열림 범위 연산자(Half-Open Range Operator)						
반 열림 범위 연산자(a..<b)는 a에서 b까지 수행되는 범위이지만 b는 포함되지 않음. 						
처음 값은 포함하지만 마지막 값은 포함하지 않음.						
닫힌 범위 연산자와 같이 a는 b보다 크면 안됨.						
반 열림 범위는 0을 기반으로 한 배열을 작업할 때 유용.
```swift
let names = ["Anna", "Alex", "Brian", "Jack"]						
let count = names.count						
for i in 0..<count {						
    print("Person \(i + 1) is called \(names[i])")						
}						
// Person 1 is called Anna						
// Person 2 is called Alex						
// Person 3 is called Brian						
// Person 4 is called Jack						
```


## 컬렉션 타입(Collection Types)						
Swift는 두 가지 컬렉션 타입 Array와 Dictionary를 제공						
Array는 같은 타입의 값을 순서대로 저장. Dictionary는 같은 타입의 값을 순서 상관없이 저장하며 						
유일한 식별자(Key)를 통해 값을 찾음.						
Array와 Dictionary는 저장 시 키와 값의 타입에 명확해야 하며 실수로 Array나 Dictionary에 실수로						
다른 타입의 값이 저장되지 않음을 의미.						
	
### 배열(Arrays)						
Swift의 Array 타입은 Array<SomeType>으로 작성, SomeType은 배열에 저장될 타입.						
간단하게 쓰면 [SomeType]으로 작성 가능.						
배열 표기법은 값 목록을 콤마(,)로 분리하며 한 쌍의 중괄호로 감싸여 표현함.
```swift
var shoppingList: [String] = ["Eggs", "Milk"]						
```
배열의 개수를 확인하는 읽기 전용 count 속성	
```swift					
print("The shopping list contains \(shoppingList.count) items.")						
// prints "The shopping list contains 2 items."					
```
						
count 속성을 이용하지 않고 isEmpty 속성을 통해 빠르게 배열이 비었는지 확인이 가능
```swift						
if shoppingList.isEmpty {						
    print("The shopping list is empty.")						
} else {						
    print("The shopping list is not empty.")						
}						
// prints "The shopping list is not empty."						
```						
배열에 append 메소드를 통해 배열 끝에 새로운 값을 추가할 수 있음.			
```swift				
shoppingList.append("Flour")						
// shoppingList now contains 3 items, and someone is making pancakes	
```					
						
배열에 인덱스로 접근하여 얻을 수 있음. 또한, 인덱스로 접근하여 값을 변경할 수 있음.
```swift							
var firstItem = shoppingList[0]						
// firstItem is equal to "Eggs"						
						
shoppingList[0] = "Six eggs"						
// the first item in the list is now equal to "Six eggs" rather than "Eggs"	
```					
						
배열에 인덱스 범위를 통해 접근하여 값을 변경하거나 배열을 대체함.			
```swift			
shoppingList[4...6] = ["Bananas", "Apples"]						
// shoppingList now contains 6 items						
// replace "Chocolate Spread", "Cheese" and "Butter" to "Bananas" and "Apples"
```						
						
배열의 insert(atIndex:) 메소드를 호출하여 특정 인덱스에 삽입할 수 있음.		
```swift				
shoppingList.insert("Maple Syrup", atIndex: 0)						
// shoppingList now contains 7 items						
// "Maple Syrup" is now the first item in the list					
```	
						
removeAtIndex 메소드를 호출하여 특정 인덱스의 값을 제거할 수 있음.		
```swift				
let mapleSyrup = shoppingList.removeAtIndex(0)						
// the item that was at index 0 has just been removed						
// shoppingList now contains 6 items, and no Maple Syrup						
// the mapleSyrup constant is now equal to the removed "Maple Syrup" string
```						
						
각 아이템에 정수 인덱스와 그 값이 필요하다면 enumerate 전역 함수를 사용함.						
enumerate 함수는 배열에 각 아이템의 인덱스와 값으로 구성된 튜플을 반환함.	
```swift					
for (index, value) in shoppingList.enumerate() {						
    print("Item \(index + 1): \(value)")						
}						
// Item 1: Six eggs						
// Item 2: Milk						
// Item 3: Flour						
// Item 4: Baking Powder						
// Item 5: Bananas						
```
						
초기화 문법을 사용하여 특정 타입의 빈 배열을 만듬.					
```swift	
var someInts = [Int]()						
print("someInts is of type [Int] with \(someInts.count) items.")						
// prints "someInts is of type [Int] with 0 items."					
```	

						
### 딕셔너리(Dictionaries)						
딕셔너리는 같은 타입의 여러 값을 저장하고 있는 컨테이너.				
각각의 값은 유일한 식별자로서 딕셔너리 안에 값과 연관됨.				
딕셔너리를 사용할 때는 식별자를 기반으로 값을 찾을 때임.				
딕셔너리 표현법으로 딕셔너리를 초기화할 수 있으며 배열 표현법과 유사한 형태임.	
각각의 키와 값으로 쌍을 이루어 콤마로 구분되며 중괄호로 감싸진 형태.		
```swift
var airports: [String: String] = ["TYO": "Tokyo", "DUB": "Dublin"]		
```				
						
딕셔너리에서 아이템 개수를 찾을 때 읽기 전용 count 속성을 통해 확인할 수 있음.	
```swift					
print("The airports dictionary contains \(airports.count) items.")						
// prints "The airports dictionary contains 2 items."				
```		
						
isEmpty 속성을 통해 빈 딕셔너리인지 확인 가능.	
```swift		
if airports.isEmpty {						
    print("The airports dictionary is empty.")						
} else {						
    print("The airports dictionary is not empty.")						
}						
// prints "The airports dictionary is not empty."					
```
						
서브스크립트 문법을 통해 딕셔너리에 새로운 아이템을 추가 가능.			
```swift			
airports["LHR"] = "London"
// the airports dictionary now contains 3 items					
```	
						
서브스크립트 문법을 사용하여 특정 키에 연관된 값을 변경할 수 있음.		
```swift			
airports["LHR"] = "London Heathrow"						
// the value for "LHR" has been changed to "London Heathrow"		
```				
						
서브스크립트 문법 대신하여 딕셔너리의 updateValue(forKey:) 메소드를 사용하여 값 변경 가능.						
updateValue(forKey:) 메소드는 옵셔널 값을 반환하므로 값이 있는지 확인해야 함.	
```swift					
if let oldValue = airports.updateValue("Dublin International", forKey: "DUB") {						
    print("The old value for DUB was \(oldValue).")						
}						
// prints "The old value for DUB was Dublin."					
```	
						
서브스크립트 문법을 통해 값을 확인할 수 있는데, 이때 값이 없다면 nil을 반환함.	
```swift					
if let airportName = airports["DUB"] {						
    print("The name of the airport is \(airportName).")						
} else {						
    print("That airport is not in the airports dictionary.")						
}						
// prints "The name of the airport is Dublin International."			
```			
						
서브스크립트 문법을 통해 딕셔너리에 할당된 값을 nil로 활당하여 key-value를 제거할 수 있음.
```swift						
airports["APL"] = "Apple International"						
// "Apple International" is not the real airport for APL, so delete it						
airports["APL"] = nil						
// APL has now been removed from the dictionary					
```	
						
removeValueForKey 메소드를 통해 key-value를 제거할 수 있음.						
이 메소드는 값이 있으면 제거된 값을 없으면 nil을 반환					
```swift	
if let removedValue = airports.removeValueForKey("DUB") {						
    print("The removed airport's name is \(removedValue).")						
} else {						
    print("The airports dictionary does not contain a value for DUB.")						
}						
// prints "The removed airport's name is Dublin International."			
```			
						
For-in 반복문을 사용.						
각각의 딕셔너리에 아이템은 (key, value) 튜플로 반환되는데 일시적인 상수나 변수로 튜플의 멤버로 분리할 수 있음.
```swift						
for (airportCode, airportName) in airports {						
    print("\(airportCode): \(airportName)")						
}						
// LHR: London Heathrow						
// TYO: Tokyo						
```						
딕셔너리의 keys와 values 속성을 가지고 접근한 키나 값의 컬렉션을 반복하여 검색할 수 있음.
```swift						
for airportCode in airports.keys {						
    print("Airport code: \(airportCode)")						
}						
// Airport code: LHR						
// Airport code: TYO						
						
for airportName in airports.values {						
    print("Airport name: \(airportName)")						
}						
// Airport name: London Heathrow						
// Airport name: Tokyo						
```
						
딕셔너리의 키나 값을 keys나 values 속성을 가지고 새로운 배열 인스턴스를 초기화 가능
```swift						
let airportCodes = [String](airports.keys)						
// airportCodes is ["LHR", "TYO"]						
						
let airportNames = [String](airports.values)						
// airportNames is ["London Heathrow", "Tokyo"]					
```	
						
배열처럼 딕셔너리도 초기화 문법을 사용하여 특정 타입의 빈 딕셔너리를 만들 수 있음.
```swift						
var namesOfIntegers = [Int: String]()						
// namesOfIntegers is an empty [Int: String] dictionary				
```		
						
배열과 마찬가지로 이미 타입이 정해져 있는 딕셔너리를 빈 딕셔너리로 초기화하여도 타입은 그대로 유지.						
빈 딕셔너리 표현법은 [:]로 사용.	
```swift					
namesOfIntegers[16] = "sixteen"						
// namesOfIntegers now contains 1 key-value pair						
namesOfIntegers = [:]						
// namesOfIntegers is once again an empty dictionary of type [Int: String]	
```					
						
						
### For 반복문(For Loops)						
* for-in 반복문은 range, sequence, collection 또는 progression에 각 아이템 만큼 수행함.						
* for 반복문은 특정 조건에 만족할 때까지 수행하며, 반복문이 끝날 때마다 counter가 증가함.						
						
#### For-In						
범위 수, 배열의 항목들, 문자열의 문자와 같이 여러 항목들의 집합을 반복할 때 for-in 반복문을 사용함.
```swift						
for index in 1...5 {						
    print("\(index) times 5 is \(index * 5)")						
}						
// 1 times 5 is 5						
// 2 times 5 is 10						
// 3 times 5 is 15						
// 4 times 5 is 20						
// 5 times 5 is 25						
```
						
범위 내에 있는 값이 필요 없다면 밑줄(_, underscore)를 사용하여 값을 무시할 수 있음.
```swift						
let base = 3						
let power = 10						
var answer = 1						
for _ in 1...power {						
    answer *= base						
}						
print("\(base) to the power of \(power) is \(answer)")						
// prints "3 to the power of 10 is 59049"						
```
						
배열에 for-in 반복문을 사용함.	
```swift					
let names = ["Anna", "Alex", "Brian", "Jack"]						
for name in names {						
    print("Hello, \(name)!")						
}						
// Hello, Anna!						
// Hello, Alex!						
// Hello, Brian!						
// Hello, Jack!						
```
						
딕셔너리에 Key-Value 쌍을 반복하여 접근할 수 있음.
딕셔너리의 각 항목은 (key, value) 튜플로 반환됨.					
딕셔너리가 반복되면 (key, value) 튜플을 각 멤버로 나누어 for-in 반복문 안에서 사용함.
```swift						
let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]						
for (animalName, legCount) in numberOfLegs {						
    print("\(animalName)s have \(legCount) legs")						
}						
// spiders have 8 legs						
// cats have 4 legs						
// ants have 6 legs						
```
						
#### For						
Swift는 전통적인 C언어 형태의 반복문을 지원.
```swift						
for var index = 0; index < 3; ++index {						
    print("index is \(index)")						
}						
// index is 0						
// index is 1						
// index is 2						
```
						
다음은 for 반복문의 일반적인 형태. 
```swift						
for initialization; condition; increment {						
    statements						
}						
```
						
상수와 변수는 초기화 표현 안에 선언하면 for 반복문 범위 안에서만 유효함.		
만약 index를 반복문이 끝난 후에 계속 사용하려면 반복문 전에 미리 선언해야 함.	
```swift					
var index: Int						
for index = 0; index < 3; ++index {						
    print("index is \(index)")						
}						
// index is 0						
// index is 1						
// index is 2						
print("The loop statements were executed \(index) times")						
// prints "The loop statements were executed 3 times"				
```		
						
						
## While 반복문(While Loops)						
While 반복문은 조건이 false가 될 때까지 수행함.						
* while은 반복문 시작시 조건을 검사.						
* do-while은 반복문이 끝난 후에 조건을 검사.						
						
### While						
While문은 한개의 조건을 검사하고 시작함. 조건이 true라면 false가 될 때까지 반복하여 수행.						
While 문의 일반적인 형태	
```swift					
while condition {						
      statements						
}
```
						
```swift						
var m = 1024						
while m < 1000 {						
    m = m * 2						
}						
print(m)						
// prints “1024”						
```						
### repeat-While						
While 반복문과는 다른 do-while 반복문은 먼저 코드를 실행한 후 조건을 검사함.	
만약 조건이 false라면 더이상 돌지 않음.	
```swift					
Do {						
       statements						
} while condition						
						
var n = 1024						
repeat {						
    n = n * 2						
} while n < 1000						
print(n)						
// prints “2048”						
```				
						
## 조건문(Conditional Statements)						
조건에 따라 다른 코드를 실행할 때 유용함.						
에러가 발생했을 때 특정 코드를 실행하거나 값이 너무 높거나 낮다면 메시지를 출력할 수 있음.												
### If						
단순한 형태의 if문은 한 개의 if문을 가지며 조건이 true일 때만 실행됨.			
```swift			
var temperatureInFahrenheit = 30						
if temperatureInFahrenheit <= 32 {						
    print("It's very cold. Consider wearing a scarf.")						
}						
// prints "It's very cold. Consider wearing a scarf."					
```							
여러 if문을 함께 쓰고자 할 때 else if문을 사용함.	
```swift					
temperatureInFahrenheit = 90						
if temperatureInFahrenheit <= 32 {						
    print("It's very cold. Consider wearing a scarf.")						
} else if temperatureInFahrenheit >= 86 {						
    print("It's really warm. Don't forget to wear sunscreen.")						
} else {						
    print("It's not that cold. Wear a t-shirt.")						
}						
// prints "It's really warm. Don't forget to wear sunscreen."			
```			
else 절은 옵션이므로 필요에 따라 작성할 수도 있고 안할 수도 있음.						
						
### Switch						
Switch 문은 값을 검토하여 그 값과 맞는 여러 패턴들과 비교함.				
Switch 문은 if 문보다 여러 경우에 대해 대응할 수 있음.					
```swift	
switch some value to consider {						
    case value 1:						
    respond to value 1						
    case value 2,						
    value 3:						
    respond to value 2 or 3						
    default:						
    otherwise, do something else						
}						
						
let someCharacter: Character = "e"						
switch someCharacter {						
case "a", "e", "i", "o", "u":						
    print("\(someCharacter) is a vowel")						
case "b", "c", "d", "f", "g", "h", "j", "k", "l", "m",						
"n", "p", "q", "r", "s", "t", "v", "w", "x", "y", "z":						
    print("\(someCharacter) is a consonant")						
default:						
    print("\(someCharacter) is not a vowel or a consonant")						
}						
// prints "e is a vowel"						
```						
switch 문은 범위 안에 값이 포함하는지 여부를 확인할 수 있음.				
```swift
let count = 3_000_000_000_000						
let countedThings = "stars in the Milky Way"						
var naturalCount: String						
switch count {						
case 0:						
    naturalCount = "no"						
case 1...3:						
    naturalCount = "a few"						
case 4...9:						
    naturalCount = "several"						
case 10...99:						
    naturalCount = "tens of"						
case 100...999:						
    naturalCount = "hundreds of"						
case 1000...999_999:						
    naturalCount = "thousands of"						
default:						
    naturalCount = "millions and millions of"						
}						
print("There are \(naturalCount) \(countedThings).")						
// prints "There are millions and millions of stars in the Milky Way."		
```				
						
switch 문에서 여러 개의 값을 검증하기 위해선 튜플을 사용할 수 있음.			
임의의 가능한 값만 일치하고자 한다면 밑줄(_) 식별자를 사용함.			
```swift
let somePoint = (1, 1)						
switch somePoint {						
case (0, 0):						
    print("(0, 0) is at the origin")						
case (_, 0):						
    print("(\(somePoint.0), 0) is on the x-axis")						
case (0, _):						
    print("(0, \(somePoint.1)) is on the y-axis")						
case (-2...2, -2...2):						
    print("(\(somePoint.0), \(somePoint.1)) is inside the box")						
default:						
    print("(\(somePoint.0), \(somePoint.1)) is outside of the box")						
}						
// prints "(1, 1) is inside the box"						
```
						
switch의 경우에서는 Where 절은 부가적인 조건을 확인하기 위해 사용함.		
```swift
let yetAnotherPoint = (1, -1)						
switch yetAnotherPoint {						
case let (x, y) where x == y:						
    print("(\(x), \(y)) is on the line x == y")						
case let (x, y) where x == -y:						
    print("(\(x), \(y)) is on the line x == -y")						
case let (x, y):						
    print("(\(x), \(y)) is just some arbitrary point")						
}						
// prints "(1, -1) is on the line x == -y"						
```						
						
## 제어 이동문(Control Transfer Statements)				
제어 이동문은 특정 코드를 다른 곳으로 이동시키는 방법으로 코드 실행 순서를 변경함.
* continue						
* break						
* fallthrough						
* return						
						
### Continue						
Continue 문은 현재 작업을 멈추고 다음 반복문으로 넘어가서 시작하라고 명령함.						
이는 루프에서 빠져나가지 않고 현재 반복 작업은 끝났음을 말함.			
```swift			
let puzzleInput = "great minds think alike"						
var puzzleOutput = ""						
for character in puzzleInput.characters {						
    switch character {						
    case "a", "e", "i", "o", "u", " ":						
        continue						
    default:						
        puzzleOutput.append(character)						
    }						
}						
print(puzzleOutput)						
// prints "grtmndsthnklk"						
```						
### Break						
break 문은 흐름 제어문을 즉시 끝냄. Break 문은 switch 문이나 반복문안에서 사용할 수 있음.
```swift
let numberSymbol: Character = "三"  // Simplified Chinese for the number 3						
var possibleIntegerValue: Int?						
switch numberSymbol {						
case "1", "١", "一", "๑":						
    possibleIntegerValue = 1						
case "2", "٢", "二", "๒":						
    possibleIntegerValue = 2						
case "3", "٣", "三", "๓":						
    possibleIntegerValue = 3						
case "4", "٤", "四", "๔":						
    possibleIntegerValue = 4						
default:						
    break						
}						
if let integerValue = possibleIntegerValue {						
    print("The integer value of \(numberSymbol) is \(integerValue).")						
} else {						
    print("An integer value could not be found for \(numberSymbol).")						
}						
// prints "The integer value of 三 is 3."						
```
						
### Fallthrough						
Swift는 switch 문에서 기본적으로 각 경우 안에 있는 코드가 끝나면 다음 경우로 넘어가지 않음.
C언어에서는 break를 쓰지 않으면 Switch 문의 각 경우가 다음으로 넘어가는데 Swift도 각 경우 안의 코드가 종료된 후에 다음 항목으로 넘어갈려면 `fallthrough`키워드를 사용함.
```swift
let integerToDescribe = 5
var description = "The number \(integerToDescribe) is"
switch integerToDescribe {
case 2, 3, 5, 7, 11, 13, 17, 19:
    description += " a prime number, and also"
    fallthrough
default:
    description += " an integer."
}
print(description)
// prints "The number 5 is a prime number, and also an integer."
```

## 함수(Functions)
함수는 특정 작업을 수행하기 위한 독립적인 코드 집함임. 
함수에 식별할 수 있도록 명명하며, 작업이 필요할 때 함수의 이름을 호출하여 사용함.  
Swift의 모든 함수는 타입을 가지며 함수의 인자 타입과 반환 타입을 고려해야 함. Swift에 다른 타입과 마찬가지로 함수에서 다른 함수로 인자를 넘기고 함수에서 함수로 인자를 반환받는 것이 쉬움.  
함수는 캡슐화를 위해 중첩된 함수 범위 내에서 작성할 수 있음.

### 함수 정의와 호출(Defining and Calling Functions)
함수를 정의할 때, 함수에 입력되는 인자 값에 이름을 정할 수 있으며, 출력 시 값의 타입 정함.  
모든 함수는 함수 이름을 가지며, 이는 어떤 작업을 하는지에 대한 설명임. 함수를 사용하기 위해 이름과 함수 인자의 타입과 일치하는 값을 넘기도록 호출함. 함수의 입력값은 함수의 인자 목록에 순서와 항상 일치함.
```swift
func sayHello(personName: String) -> String {
    let greeting = "Hello, " + personName + "!"
    return greeting
}
print(sayHello("Anna"))
// prints "Hello again, Anna!"
```
`func` 키워드를 앞에 사용하며, 함수의 반환  타입과 반환 방향 ->를 나타내고 그 뒤에 반환 타입의 이름을 사용함.

### 다중 값을 반환하는 함수(Functions with Multiple Return Values)
함수에 반환 타입을 튜플 값을 사용할 수 있으며 하나의 집합으로 된 다중 값을 반환함.  
```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}

let bounds = minMax([8, -6, 2, 109, 3, 71])
print("min is \(bounds.min) and max is \(bounds.max)")
// prints "min is -6 and max is 10
```

  
---
### 참고 
[잉여개발자 블로그](http://minsone.github.io/mac/ios/swift-the-basic-summary/)   
[iOS Developer Library - Swift Programming Language](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-ID309)
