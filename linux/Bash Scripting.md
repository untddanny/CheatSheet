# Bash Scripting Notes

bash
#!/bin/bash

## Introduction to Bash Scripting
Bash (Bourne Again Shell) scripting is used for automating tasks in Unix-like operating systems. It allows for batch processing, command execution, and file operations. Every script starts with `#!/bin/bash` which specifies that Bash is the interpreter to be used.

## Bash Operators

| Operator | Description                  | Example                              |
|----------|------------------------------|--------------------------------------|
| =        | Assignment operator           | x=10                                |
| +        | Addition                      | sum=$((x + y))                      |
| -        | Subtraction                   | diff=$((x - y))                     |
| *        | Multiplication                | product=$((x * y))                  |
| /        | Division                      | quotient=$((x / y))                 |
| ==       | Equality                      | [[ $x == $y ]]                      |
| !=       | Inequality                    | [[ $x != $y ]]                      |
| -eq      | Equal to                      | [[ $x -eq $y ]]                     |
| -ne      | Not equal to                  | [[ $x -ne $y ]]                     |
| -lt      | Less than                     | [[ $x -lt $y ]]                     |
| -gt      | Greater than                  | [[ $x -gt $y ]]                     |
| -le      | Less than or equal to         | [[ $x -le $y ]]                     |
| -ge      | Greater than or equal to      | [[ $x -ge $y ]]                     |

#!/bin/bash


# Bash Scripting Questions

bash
```
#!/bin/bash
```
## 1. How do you use the `read` command to capture user input in a bash script?
```
read variable_name
```

## 2. How do you declare a variable in bash?
```
variable_name=value
```

## 3. How do you assign a value to a variable in bash?
```
variable_name="Assigned Value"
```

## 4. How do you use the `echo` command in bash scripting?
```
echo "Your message here"
```

## 5. How do you concatenate variables and text in an `echo` statement?
```
echo "This is a variable: $variable_name"
```

## 6. What are some basic commands for file manipulation in bash scripting?
```
touch filename       # Creates a new file
rm filename          # Deletes a file
mv filename new_path # Moves a file
cp filename dest     # Copies a file
```

## 7. How do you list the contents of a directory in bash?
```
ls
```

## 8. How do you create a new directory in bash?
```
mkdir new_directory
```

## 9. How do you delete a file in bash?
```
rm filename
```

## 10. How do you move a file from one location to another in bash?
```
mv source_file destination_directory
```

## 11. How do you check if a file exists in bash scripting?
```
if [ -f filename ]; then
  echo "File exists."
else
  echo "File does not exist."
fi
```

## 12. Take 2 number input from user and print its sum.
```
read num1
read num2
sum=$((num1 + num2))
echo "Sum is: $sum"
```

## 13. Take 2 number input from user and print its minus.
```
read num1
read num2
difference=$((num1 - num2))
echo "Difference is: $difference"
```

## 14. Take 2 number input from user and print its divide.
```
read num1
read num2
if [ $num2 -ne 0 ]; then
  divide=$((num1 / num2))
  echo "Division is: $divide"
else
  echo "Cannot divide by zero."
fi
```

## 15. Take 2 number input from user and print its multiply.
```
read num1
read num2
product=$((num1 * num2))
echo "Product is: $product"
```

## 16. Take 2 number input from user and print its modulo %.
```
read num1
read num2
modulo=$((num1 % num2))
echo "Modulo is: $modulo"
```

# If else conditions

## 17. What is the syntax for comparing two values in an `if` statement?
```
if [ $value1 -eq $value2 ]; then
  echo "Equal"
else
  echo "Not equal"
fi
```

## 18. How do you use the `-eq`, `-ne`, `-lt`, `-gt`, `-le`, and `-ge` operators in bash `if` statements?
```
if [ $a -eq $b ]; then echo "Equal"; fi
if [ $a -ne $b ]; then echo "Not Equal"; fi
if [ $a -lt $b ]; then echo "Less than"; fi
if [ $a -gt $b ]; then echo "Greater than"; fi
if [ $a -le $b ]; then echo "Less than or equal"; fi
if [ $a -ge $b ]; then echo "Greater than or equal"; fi
```


## 22. How do you use logical operators (`&&`, `||`, `!`) in bash `if` statements?
```
if [ $a -eq $b ] && [ $c -gt $d ]; then echo "Both conditions true"; fi
if [ $a -eq $b ] || [ $c -gt $d ]; then echo "At least one condition is true"; fi
if ! [ $a -eq $b ]; then echo "Not equal"; fi
```

## 23. Take any number from the user and print positive, negative, or zero.
```
read num
if [ $num -gt 0 ]; then
  echo "Positive"
elif [ $num -lt 0 ]; then
  echo "Negative"
else
  echo "Zero"
fi
```

## 24. Take any numbers from the user and print max and minimum.
```
read num1
read num2
if [ $num1 -gt $num2 ]; then
  echo "Max: $num1, Min: $num2"
else
  echo "Max: $num2, Min: $num1"
fi
```

## 25. Write a script that if students got marks in the range, it will print grades:
```
read marks
if [ $marks -ge 90 ]; then echo "A"
elif [ $marks -ge 80 ]; then echo "B"
elif [ $marks -ge 70 ]; then echo "C"
elif [ $marks -ge 60 ]; then echo "D"
else echo "F"; fi
bash
```


# String Methods

## 26. How do you concatenate two strings in bash?
```
str1="Hello"
str2="World"
result="$str1 $str2"
echo "$result"
```

## 27. How do you find the length of a string in bash?
```
str="Hello"
length=${#str}
echo "Length: $length"
```

## 28. What is the syntax for extracting a substring from a string in bash?
```
str="Hello World"
substr=${str:0:5}
echo "$substr"
```

## 29. How do you convert a string to uppercase in bash?
```
str="hello"
echo "${str^^}"
```

## 30. How do you convert a string to lowercase in bash?
```
str="HELLO"
echo "${str,,}"
```

## 31. How do you replace a substring within a string in bash?
```
str="Hello World"
new_str=${str/World/Bash}
echo "$new_str"
```

## 32. How do you check if a string contains a substring in bash?
```
str="Hello World"
if [[ $str == *"World"* ]]; then
  echo "Substring found"
fi
```

## 33. How do you trim whitespace from a string in bash?
```
str="   Hello World   "
trimmed=$(echo "$str" | xargs)
echo "Trimmed: '$trimmed'"
```

## 34. How do you reverse a string in bash?
```
str="Hello"
reverse=$(echo "$str" | rev)
echo "Reversed: $reverse"
```

## 35. How do you check if a string is empty in bash?
```
str=""
if [ -z "$str" ]; then
  echo "String is empty"
fi
```

## 36. What is the syntax for removing leading characters from a string in bash?
```
str="abcHello"
result=${str#abc}
echo "$result"
```

## 37. What is the purpose of the `tr` command in string manipulation in bash?
```
It is used to translate or delete characters from input.
echo "Hello" | tr 'H' 'J'
```

## 38. How do you use the `sed` command to perform string substitution in bash?
```
echo "Hello World" | sed 's/World/Bash/'
```

## 39. How do you join multiple strings into a single string in bash?
```
str1="Hello"
str2="World"
joined="$str1$str2"
echo "$joined"
```

## 40. How do you find and count occurrences of a substring within a string in bash?
```
str="Hello Hello World"
count=$(echo "$str" | grep -o "Hello" | wc -l)
echo "Occurrences: $count"
```

## 41. What is the purpose of the `expr` command in performing arithmetic operations on strings in bash?
```
str="3 + 2"
result=$(expr 3 + 2)
echo "$result"
```

## 42. How do you remove all occurrences of a specific character from a string in bash?
```
str="Hello World"
new_str=${str//l/}
echo "$new_str"
```

## 43. How do you truncate a string to a specific length in bash?
```
str="Hello World"
truncate=${str:0:5}
echo "$truncate"
```

## 44. How do you encode or decode a string in base64 format in bash?
```
str="Hello"
encoded=$(echo -n "$str" | base64)
echo "Encoded: $encoded"
decoded=$(echo -n "$encoded" | base64 --decode)
echo "Decoded: $decoded"
```

## 45. How do you find the index of the first occurrence of a substring within a string in bash?
```
str="Hello World"
index=$(expr index "$str" "World")
echo "Index: $index"
```

## 46. How do you find the index of the last occurrence of a substring within a string in bash?
```
str="Hello World World"
last_index=$(echo "$str" | awk '{print index($0,"World",length($0))}')
echo "Last Index: $last_index"
```

## 47. What is the purpose of the `grep` command in string manipulation in bash?
```
It is used to search for a pattern in a string or file.
echo "Hello World" | grep "World"
```

## 48. How do you extract lines from a string that match a specific pattern in bash?
```
str="Hello\nWorld\nBash"
echo -e "$str" | grep "World"
```


# Array Manipulation

## 53. How do you access elements of an array in bash?
```
arr=(1 2 3 4)
echo "${arr[0]}"
```

## 54. How do you find the length of an array in bash?
```
arr=(1 2 3 4)
length=${#arr[@]}
echo "Length: $length"
```

## 55. How do you iterate over all elements of an array in bash?
```
arr=(1 2 3 4)
for i in "${arr[@]}"; do
  echo "$i"
done
```

## 56. What is the role of indexing in arrays in bash?
Indexing allows access to specific elements of an array by position.

## 57. How do you add elements to an array in bash?
```
arr=(1 2 3)
arr+=(4)
echo "${arr[@]}"
```

## 58. How do you remove elements from an array in bash?
```
arr=(1 2 3 4)
unset arr[2]
echo "${arr[@]}"
```

## 59. How do you check if an array is empty in bash?
```
arr=()
if [ ${#arr[@]} -eq 0 ]; then
  echo "Array is empty"
fi
```

## 60. How do you check if a specific element exists in an array in bash?
```
arr=(1 2 3 4)
if [[ " ${arr[@]} " =~ " 3 " ]]; then
  echo "3 exists in array"
fi
```


# Array Manipulation

## 61. How do you add elements to the end of an array in bash?
```
arr=(1 2 3)
arr+=(4)
echo "${arr[@]}"
```

## 62. How do you add elements to the beginning of an array in bash?
```
arr=(2 3 4)
arr=(1 "${arr[@]}")
echo "${arr[@]}"
```

## 63. How do you insert an element at a specific index in an array in bash?
```
arr=(1 2 4 5)
arr=( "${arr[@]:0:2}" 3 "${arr[@]:2}" )
echo "${arr[@]}"
```

## 64. How do you modify the value of a specific element in an array in bash?
```
arr=(1 2 3 4)
arr[1]=10
echo "${arr[@]}"
```

##65. What is the syntax for slicing an array in bash?
```
arr=(1 2 3 4 5 6)
slice=("${arr[@]:1:3}")
echo "${slice[@]}"
```

## 66. How do you remove the last element from an array in bash?
```
arr=(1 2 3 4)
unset arr[-1]
echo "${arr[@]}"
```

## 67.  How do you remove the first element from an array in bash?
```
arr=(1 2 3 4)
unset arr[0]
arr=("${arr[@]}")
echo "${arr[@]}"
```

## 68. How do you remove a specific element from an array by value in bash?
```
arr=(1 2 3 4)
arr=( "${arr[@]/2}" )
echo "${arr[@]}"
```

##69. How do you remove a specific element from an array by index in bash?
```
arr=(1 2 3 4)
unset arr[2]
arr=("${arr[@]}")
echo "${arr[@]}"
```

##70. How do you merge two arrays in bash?
```
arr1=(1 2 3)
arr2=(4 5 6)
merged=("${arr1[@]}" "${arr2[@]}")
echo "${merged[@]}"
```

##71. How do you reverse the order of elements in an array in bash?
```
arr=(1 2 3 4)
reversed=()
for (( i=${#arr[@]}-1 ; i>=0 ; i-- )); do
  reversed+=("${arr[$i]}")
done
echo "${reversed[@]}"
```

##72 How do you sort the elements of an array in bash?
```
arr=(3 1 4 2)
sorted=($(for i in "${arr[@]}"; do echo $i; done | sort))
echo "${sorted[@]}"
```


# Functions

##73. What is the syntax for defining a function in bash?
```
function my_function() {
  echo "Hello, World!"
}
```

##74. How do you call a function in bash?
```
my_function
```

##75. How do you pass arguments to a function in bash?
```
function greet() {
  echo "Hello, $1!"
}
greet "User"
```

##76. How do you return a value from a function in bash?
```
function add() {
  local result=$(( $1 + $2 ))
  echo "$result"
}
sum=$(add 3 5)
echo "Sum: $sum"
```

##77. How do you use local variables within a function in bash?
```
function local_test() {
  local var="I'm local"
  echo "$var"
}
local_test
```


# Python Loops

##78. Write a Python program to print "Hello, World!" 5 times using a for loop.
```
for i in {1..5}; do
  echo "Hello, World!"
done
```

##79 Create a program that prints numbers from 1 to 10 using a for loop.
```
for i in {1..10}; do
  echo "$i"
done
```

##80 Develop a program that prints the even numbers from 1 to 10 using a for loop.
```
for i in {1..10}; do
  if (( $i % 2 == 0 )); then
    echo "$i"
  fi
done
```

##81 Create a program that prints the square of each number from 1 to 5 using a for loop.
```
for i in {1..5}; do
  echo "$((i * i))"
done
```

##82 Develop a program that prints the reverse of 1 to 10 using a for loop.
```
for (( i=10; i>=1; i-- )); do
  echo "$i"
done
```

#83 Write a program that prints the odd numbers from 1 to 10 using a for loop.
```
for i in {1..10}; do
  if (( $i % 2 != 0 )); then
    echo "$i"
  fi
done
```

##84 Write a Python program to print the multiplication table of a given number using a for loop.
```
num=5
for i in {1..10}; do
  echo "$num * $i = $((num * i))"
done
```


# File Manipulating

##85 How do you append data to a file in bash scripting?
```
echo "New data" >> file.txt
```

##86 What command do you use to write data to a file in bash?
```
echo "Some data" > file.txt
```

##87 How do you read data from a file in bash scripting?
```
while read line; do
  echo "$line"
done < file.txt
```

##88 How do you save the output of a command to a file in bash scripting?
```
ls > file.txt
```

##89 How do you overwrite the contents of a file with new data in bash?
```
echo "Overwrite data" > file.txt
```

##90 How do you create a new file in bash scripting?
```
touch newfile.txt
```

##91 How do you search for and replace text within a file in bash scripting?
```
sed -i 's/oldtext/newtext/g' file.txt
```

##92 What command do you use to delete a specific line from a file in bash?
```
sed -i '2d' file.txt
```

##93 How do you read specific lines from a file in bash scripting?
```
sed -n '1,3p' file.txt
```


