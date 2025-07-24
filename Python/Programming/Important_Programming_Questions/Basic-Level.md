✅ EASY LEVEL (Basics & String Manipulation)
1.Reverse a String without using slicing.
  def reversedString(string):
    reversed_Str = ""
    for char in string:
        reversed_Str = char+reversed_Str
    return reversed_Str
print(reversedString("Hello"))

2.Check if a string is a palindrome (ignore spaces & case).
