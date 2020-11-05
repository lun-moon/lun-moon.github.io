# Brackets to conform to RangeExpression?

kata link:
<https://www.codewars.com/kata/52fba66badcd10859f00097e/train/swift>


probably the best way to solve this puzzle is right here
<https://developer.apple.com/documentation/swift/string/2997150-removeall>  

But I would like to ask for help with code below, and the background of using brackets to make a string conform to a RangeExpression, because if I use the prcactice in regular code I need to know when it breaks.

(as an aside, I'm aware that if I wanted to work around the Int vs String.Index issue I could use a string extension.
But not sure where to store this in a project so it is clear to the next person that the code exists.
<https://stackoverflow.com/a/46627527>
https://stackoverflow.com/a/26775912
;  as an extra aside, apparently strings use a "count" method now instead of "length", not sure how to retrieve the swift version in each "web notebook for swift" that I'm using however)
```
func disemvowel(_ s: String) -> String {
  var builderString = "" 
  var consonants = "bcdfghjklmnpqrstvwxyz"
  var vowels = "aeiou"
  consonants = consonants + consonants.uppercased()
  vowels = vowels + vowels.uppercased()
  print(vowels)
  for i in 0..<s.length {
    let curIndex = s.index(s.startIndex, offsetBy: i)
    if (!vowels.contains(s[curIndex]) ) {
      print(s[curIndex])
      builderString = builderString + [s[curIndex]]
      print(builderString)
    }
  }
  
  return(builderString)
}
print(disemvowel("some Text")
```
returns "sm Txt"  

However unwrapping the last instance of s[curIndex] from brackets results in

```
func disemvowel(_ s: String) -> String {
  var builderString = "" 
  var consonants = "bcdfghjklmnpqrstvwxyz"
  var vowels = "aeiou"
  consonants = consonants + consonants.uppercased()
  vowels = vowels + vowels.uppercased()
  print(vowels)
  for i in 0..<s.length {
    let curIndex = s.index(s.startIndex, offsetBy: i)
    if (!vowels.contains(s[curIndex]) ) {
      print(s[curIndex])
      builderString = builderString + s[curIndex]
      print(builderString)
    }
  }
  
  return(builderString)
}
print(disemvowel("some Text")

STDERR:

solution.swift:12:40: error: subscript 'subscript(_:)' requires that 'String.Index' conform to 'RangeExpression'
      builderString = builderString + s[curIndex]
                                       ^
Swift.Collection:2:23: note: where 'R' = 'String.Index'
    @inlinable public subscript<R>(r: R) -> Self.SubSequence where R : RangeExpression, Self.Index == R.Bound { get }
```

note if this ine contains a plain string "ik" I can contcatenate it all day

```
truncated
builderString = builderString + "jk" 
truncated
print(disemvowel("some Text")
```

Returns "jkjkjkjkjkjk


