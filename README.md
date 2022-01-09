
# Bash 
Bash stands for Bourne-Again SHell . Bash is a Unix shell and command language. It is widely available on various operating systems, and it is also the default command interpreter on most Linux systems

Let's start by creating a new file with a .sh extension. As an example, we could create a file called `script.sh`.

-  `touch script.sh`

In order to execute/run a bash script file with the bash shell interpreter,
the first line of a script file must indicate the absolute path to the bash
executable:
-  `#!/bin/bash `      This is also called a Shebang.

## Bash Hello World
To do that, open the devdojo.sh file again and add the following after the #!/bin/bash line: 

- #!/bin/bash
   echo "Hello World!" 

Save the file and exit. After that make the script executable by running: 

- `chmod +x script.sh `

After that execute the file: 

- `./script.sh `

You will see a "Hello World" message on the screen. 
Another way to run the script would be: 
- `bash devdojo.sh`


## Bash Variables


As in any other programming language, you can use variables in Bash Scripting as well. However, there are no data types, and a variable in Bash can contain numbers as well as characters.

```
#!/bin/bash 
name="musab"
echo "Hi there $name" 
 
 ```
 After that execute the file: You will see a "Hi there musab " message on the screen. 

 ```
 #!/bin/bash 
 name="musab" 
 greeting="Hello" 
 echo "$greeting $name"
 ```
 
 After that execute the file: You will see a "Hello musab " message on the screen. 
 
 
 ## Bash User Input
 
 
 Now let's go ahead and ask the user for input instead. To do that again, open the file with your favorite text editor and update the script as follows:
 
``` 
 #!/bin/bash 
 echo "What is your name?" 
 read name 
 echo "Hi there $name" 
 echo "Welcome to my script!"
 ```
 
 
- First run the script: ` ./script.sh`
- Then, you would be prompted to enter your name:
```
What is your name? 
musab
 ```
 - Once you've typed your name, just hit enter, and you will get the following output: 
 
Hi there musab
Welcome to my script !
 
 
##  Bash Comments


To do that in Bash, you need to add the `#` symbol at the beginning of the line. Comments will never be rendered on the screen.



## Bash Arguments

You can pass arguments to your shell script when you execute it. To pass an argument, you just need to write it right after the name of your script. For example:

`./scrippt.com your_argument`

In the script, we can then use `$1` in order to reference the first argument that we specified. If we pass a second argument, it would be available as `$2` and so on

Let's create a short script called `arguments.sh` as an example:

```
#!/bin/bash 

echo "Argument one is $1" 
echo "Argument two is $2" 
echo "Argument three is $3"
```

Then run the file and pass 3 arguments: `./arguments.sh dog cat bird`

The output that you would get would be: 
```
Argument one is dog 
Argument two is cat 
Argument three is bird 
```

Another thing that you need to keep in mind is that `$0` is used to reference the script itself. 

This is an excellent way to create self destruct the file if you need to or just get the name of the script. 

For example, let's create a script that prints out the name of the file and deletes the file after that:

```
#!/bin/bash 
echo "The name of the file is: $0 and it is going to be selfdeleted."
rm -f $0
```

## Bash Arrays

You can initialize an array by assigning values devided by space and enclosed in`()`. Example:

`my_array=("value 1" "value 2" "value 3" "value 4")`

Access a single element, this would output: value 2

> echo ${my_array[1]} 

This would return the last element: value 4 

>echo ${my_array[-1]}

As with command line arguments using @ will return all arguments in the array, as follows: value 1 value 2 value 3 value 4 

>echo ${my_array[@]}


Prepending the array with a hash sign (#) would output the total number of elements in the array, in our case it is 4: 

> echo ${#my_array[@]}


### Examples

- example 1

```
#!/bin/bash
files=("file1" "file2" "file3" "file4" "file5")
#files[2]="musab"  							#reples (update) element
echo ${files[*]}
#echo ${#files[@]} 							#number of element on list
#echo ${files[2]}
files+=("file100")							 #add element
unset files[0]  								#delete element
echo ${files[*]}
```


- example 2 

```
list=("musab" 2290 "developer" "bash")

echo "my name is ${list[0]}"
echo "my id is ${list[1]}"
echo "my group is ${list[2]}"
echo "my shell is ${list[3]}"

```


## Substring in Bash :: Slicing

- example 

```
#!/bin/bash 
letters=( "A""B""C""D""E" ) 
b=${letters:0:2} 
echo "${b}"
```


This command wil print array from starting index 0 to 2 where 2 is exclusive.  `$ AB`

- example 2

```
#!/bin/bash
letters=( "A""B""C""D""E" ) 
b=${letters::5} 
echo "${b}" 
```

This command will print from base index 0 to 5, where 5 is exclusive and starting index is default set to 0 .  `$ ABCDE3


- example 3 add str to str

```
str1="mr."
str2="Robot"
all=$str1$str2
echo "add $str1 + $str1  =  $all"

```

output ==> Mr.Robot


- example 4 finding substr

```
word="musab cool"
expr index "$word" "cool"  #return 7
expr index "$word" "345"   # return 0
```

- example 4 extrac substr

```
web="www.facebook.com"
echo $web   	
echo ${web:4}
echo ${web:4:-4}
```

output ==> www.facebook.com
				  facebook.com
				 facebook
				 
				 
- example 5 replace substr

```
site="www.facebook.com"
echo $site
echo ${site/facebook/google}
```

output ==>   www.facebook.com
					www.google.com
					
				
				
- example 6 delete substr	

```
litter="hi musab what's App"
number=192-22-3239-767
echo $litter
echo ${litter/hi} #delete hi 
echo $number
echo  ${number/-} #delete - symble
echo $number
echo  ${number//-} #delete all - symbale
```

output ==>
hi musab what's App
musab what's App
192-22-3239-767
19222-3239-767
192-22-3239-767
192223239767



- example 7 convert upper and lower substr

```
legent="john musab"
actor="ISMAIL ABRAHIM"

echo $legent
echo $actor
echo ${legent^^} #all upper
echo ${actor,,} #all lower
echo ${legent^} #first letter upper
echo ${actor,,} # all lower
```

output  ==>

john musab
ISMAIL ABRAHIM
JOHN MUSAB
ismail abrahim
John musab
ismail abrahim




## Bash Conditional Expressions 


In computer science, conditional statements, conditional expressions, and conditional constructs are features of a programming language, which perform different computations or actions depending on whether a programmer-specified boolean condition evaluates to true or false. 

In Bash, conditional expressions are used by the `[[` compound command and the `[`built-in commands to test file attributes and perform string and arithmetic comparisons. 

Here is a list of the most popular Bash conditional expressions. You do not have to memorize them by heart. You can simply refer back to this list whenever you need it!


- True if file exists. `[[ -a ${file} ]]`
- True if file exists and is a character special file. ` [[ -c ${file} ]]`
- True if file exists and is a directory. `[[ -d ${file} ]] `
- True if file exists. `[[ -e ${file} ]]`
- True if file exists and is readable. `[[ -r ${file} ]] `
- True if file exists and has a size greater than zero.` [[ -s ${file} ]] `
- True if file exists and is writable. `[[ -w ${file} ]] `
- True if file exists and is executable. `[[ -x ${file} ]]`

```
#!/bin/bash

if [ $# -ne 1 ] ; then
	echo "erorr : invalid number of argument (file path)"
	exit 1
fi

file=$1
if [ -f $file ] ; then  # /etc/passwor
	echo "$file is reguler file" 
elif [ -l $file ] ; then 
	echo "$file is soft linnk" 
elif [ -d $file ] ; then #/etc
	echo "$file is directory"
else
	echo "$file does not exist"
fi
```



## Arithmetic operators


- Returns true if the numbers are equal `[[ ${arg1} -eq ${arg2} ]] `
- Returns true if the numbers are not equal ``[[ ${arg1} -ne ${arg2} ]] ``
- Returns true if arg1 is less than arg2 `[[ ${arg1} -lt ${arg2} ]] `
- Returns true if arg1 is less than or equal arg2 `[[ ${arg1} -le ${arg2} ]]` 
- Returns true if arg1 is greater than arg2 `[[ ${arg1} -gt ${arg2} ]]` 
- Returns true if arg1 is greater than or equal arg2 `[[ ${arg1} -ge ${arg2} ]] `


As a side note, arg1 and arg2 may be positive or negative integers. As with other programming languages you can use AND & OR conditions:

`[[ test_case_1 ]] && [[ test_case_2 ]]` #And
`[[ test_case_1 ]] || [[ test_case_2 ]]` #Or

- Exit status operators returns true if the the command was successful without any errors `[[ $? -eq 0 ]]` 
- returns true if the the command was not successful or had errors `[[ $? -gt 0 ]]`



#### Example for oprations on bash 


echo  "__________________sub _________________________"

```
fl1=$(du -b $1 | cut -f1) #see the size of file by byet 
fl2=$(du -b $2 | cut -f1)

echo "file $1 has : $fl1 bytes"
echo "file $2 has : $fl2 bytes"

totall=$(($fl1+$fl2)) # way of sub 

echo "the totall byets $totall"

```


echo  "__________________multi ______________________"

```
G=4
M=$((4 * 1024))
echo "$G*1024 = $M"
echo "$G GB is equal $M MB"
```

echo  "_________________divi ____________________________"

```
f=20
f1=2
x=$(($f / $f1 | bc -l))
echo "$f/$f1 = $x"
```

echo  "__________________power_______________________"

```
p=5
p2=2
p3=$(($p**$p2))
echo "$p^^$p2 = $p3"

```

echo  "__________________reminder_______________________"

```
r=97
r2=9
r3=$(($r%$r2))
echo "$r%$r2 = $r3"
```

echo  "__________________reminder_______________________"

```
c=$3
a=$(($3 * (9/5) + 32| bc -l ))
echo "$3 degree is equal to $a degeee FH"
```


## Bash Conditionals


In the last section, we covered some of the most popular conditional expressions. We can now use them with standard conditional statements like `if, if-else and switch case statements.`


echo  "__________________if statement_______________________"#one condation

```
if [ $(whoami) = "root" ] ; then
	echo "you are the root"
fi
```

echo  "__________________if-else statement_______________________"#two condation

```
if [ $(whoami) = "root" ] ; then
	echo "you are the root"
else
	echo "you are normal user"

fi
```

echo  "__________________elif_______________________"#multi condation

```
age=$1
if [ $age -lt 13 ] ; then
	echo "you are a kid"
elif [ $age -lt 20 ] ; then
	echo "you are a teenager"
elif [ $age -lt 65 ] ; then
	echo "you are a adult"
else
	echo "you are elder"
fi
```

echo  "__________________if inside statement_______________________"#if inside if

```
wether=$2
if [ $wether -gt 5 ] ; then
	if [ $wether -lt 15 ] ; then
		echo "the wether is cool"
	elif [ $wether -lt 25 ] ; then
		echo "the wether is nice"
	else
		echo "the wether is hott"
	fi
else
	echo "the wether is freezing out side"

fi
```


### Switch case statements

As in other programming languages, you can use a case statement to simplify complex conditionals when there are multiple different choices. So rather than using a few if, and if-else statements, you could use a single case statement.

A quick rundown of the structure: 
- All case statements start with the case keyword. 
- On the same like as the case keyword, you need to specify a variable or an expression followed by the in keyword. 
- After that, you have your case patterns, where you need to use `)` to identify the end of the pattern. You can specify multiple patterns divided by a pipe: `|`.
-  After the pattern, you specify the commands that you would like to be executed in case that the pattern matches the variable or the expression that you've specified. 
-  All clauses have to be terminated by adding `;;` at the end. 
-  You can have a default statement by adding a `*` as the pattern. To close the case statement, use the esac (case typed backwards) keyword.


echo  "__________________caase check_______________________" 

```
#!/bin/bash 
echo -n "Enter the name of a car brand: " 
read car 
case $car in Tesla) 
	echo -n "${car}'s factory in the USA."  ;; 
BMW | Mercedes | Audi | Porsche) 
	echo -n "${car}'s factory in Germany."  ;; 
Toyoda | Mazda | Mitsubishi | Subaru)
	echo -n "${car}'s factory in Japan."  ;; 
*) 
	echo -n "${car} is an unknown car brand."  ;; 
esac

```


echo  "__________________case check_______________________"

```
char=$1
case $char in
	[a-z])
	echo "small alphabet" ;;
	[A-Z])
	echo "big alphabet" ;;
	[0-9])
	echo "number" ;;
	*)
	echo "spacial charecter" ;;
esac
```




## Bash loop

As with any other language, loops are very convenient. With Bash you can use `for` loops, `while` loops, and `until` loops.


### For loops

Example:  

```
#!/bin/bash 
users="devdojo bobby tony" 
for user in ${users} do 
	echo "${user}" 
done
```

echo  "__________________C ++ style loop_______________________"

```
for ((i=0 ; i<=10 ; i++)); do
	echo "hello friend $i !"
done
```

echo  "__________________list/range_______________________"

```
 #for i in {11..99} ; do 
for i in forloop.sh ; do
	echo $i 
done
```

echo  "__________________c style_______________________"

```
for ((i=10 ; i>0 ; i--)); do
	echo "hello friend $i !"
done
```

echo  "__________________infinty loop_______________________"

```
for((;;)) ; do
	echo "you pc under the hack now"
done

```

### While loops

Here is an example of a `while` loop: 

```
#!/bin/bash 

counter=1 
while [[ $counter -le 10 ]] do 
	echo $counter 
	((counter++))
done
```

echo  "__________________while loop_______________________"

```
num=1
while [ $num -le 10 ] ; do
	echo $(($num * 3))
	num=$(($num+1))
done
```

echo  "__________________until uposet of while _______________________"  

```
num=1
until [ $num -gt 10 ] ; do
	echo $(($num * 3))
	num=$(($num+1))
done
```

echo  "__________________check name _______________________"  

```
read -p "What is your name? " name 
while [[ -z ${name} ]] do
	echo "Your name can not be blank. Please enter a valid name!" 
	read -p "Enter your name again? " name 
done 
echo "Hi there ${name}"
```


### until loops

```
Example: 
#!/bin/bash 
count=1 
until [ $count -gt 10 ] do 
	echo $count 
	((count++)) 
done

```

### Continue and Break

```
#!/bin/bash

echo  "__________________break _______________________" 

for ((i=1 ; i<=10 ;i++)); do
	echo $i
	if [ $i -eq 3 ] ; then
		break
	fi
done
```


echo  "__________________continus_______________________" 

```
for ((i=1 ; i<=10 ;i++)); do
	
	if [ $(($i % 2)) -eq 0 ] ; then
		continue
	fi
		echo $i
done


```

### Array loops

```
#!/bin/bash

list=(22 33 44 55 66 77 88 99 00 12 13 14 15 23 43 56)
for i in ${list[@]} ; do
	echo $i
done



```


## Bash Functions 

Functions are a great way to reuse code. The structure of a function in bash is quite similar to most languages: 

function function_name()  { 
		your_commands 
}


```
echo  "__________________call function_______________________" 
hello () {
echo "hello $(whoami)"
}

hello
hello
echo " the exist state of thr call function is : $?"
```

echo  "__________________return function value _______________________" 

```
error () {
blababa
#return 0 # check error in function
}

error
echo " the exist state of thr call function is : $?"
```


echo  "__________________pass function argument _______________________" 

```
iseven() {

if [ $(($1 % 2)) -eq 0 ] ; then
	echo $1 is even
else
	echo $1 is odd
fi

}

iseven 3
iseven 2
iseven 22
iseven 7

fun() {

echo "$1 is first argument on fun()"
echo "$2 is second argument on fun()"

}

echo "$1 is first argument to script"
echo "$2 is second argument to script"

fun yes 7

```


echo  "__________________loca and globl varible _______________________"  

```
v1="A"  # gloable fun can call it from any where
v2="B"

myfun(){
local v1="C"  # local mean just on  fun can call it
v2="D"  # update vaarible to value D

echo "inside myfun() : v1 : $v1 and : v2 : $v2"

}

echo "before calling  myfun() : v1 : $v1 and : v2 : $v2"
myfun
echo "after calling myfun() : v1 : $v1 and : v2 : $v2"

```


echo  "__________________recursiv funcation  _______________________" 

#call funcation inside funcation itself
#ex => factoria(n) = n X factoria (n - 1)

```
factoria() {
if [ $1 -le 1 ] ;  then
	echo $1
else
	last=$(factoria $(($1 - 1)) )
	echo $(($1 * last))

fi

}

echo -n "factoria 4 is :"
factoria 4
echo -n "factoria 5 is :"
factoria 5
echo -n "factoria 6 is :"
factoria 6
``` 

#how it work
#4 x factoria(3)
#4 x(3 x factoria (2)
#4 x (3 x(2 x factoria(1)
#4 x 3 x 2 x 1 = 24
















