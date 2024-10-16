
<------------------------------------------------------->
awk.sh


echo `awk '{
    for(i=1; i<=NF; i++) {
        if(length($i) > 4 && ($i ~ /^[0-9]+$/)) {
            print $i
        }
    }
}' random.txt`




<------------------------------------------------------->
calculator.sh


# echo $(( $1 $2 $3 ))    
echo "scale=2; $1 $2 $3" | bc


# #!/bin/bash

# # Function to display the menu
# display_menu() {
#     echo "Simple Calculator"
#     echo "=================="
#     echo "1. Addition"
#     echo "2. Subtraction"
#     echo "3. Multiplication"
#     echo "4. Division"
#     echo "5. Exit"
# }

# # Function to perform calculations
# calculate() {
#     case $1 in
#         1) echo "Result: $(($2 + $3))" ;;
#         2) echo "Result: $(($2 - $3))" ;;
#         3) echo "Result: $(($2 * $3))" ;;
#         4) 
#             if [ $3 -eq 0 ]; then
#                 echo "Error: Division by zero is not allowed."
#             else
#                 echo "Result: $(($2 / $3))"
#             fi
#             ;;
#         *) echo "Invalid option." ;;
#     esac
# }

# # Main loop
# while true; do
#     display_menu
#     read -p "Select an option (1-5): " option

#     if [ "$option" -eq 5 ]; then
#         echo "Exiting..."
#         break
#     fi

#     read -p "Enter first number: " num1
#     read -p "Enter second number: " num2

#     calculate $option $num1 $num2
#     echo ""
# done





<------------------------------------------------------->
compound.sh


read -p "enter principle: " p
read -p "enter number of times: " n
read -p "enter rate: " r
read -p "enter time: " t

pow=`echo "scale=4; $n * $t" | bc`
echo $pow
rate=`echo "scale=4; ( $r / 100 ) / $n" | bc`
echo $rate
sum=`echo "scale=4; 1 + $rate" | bc`
echo $sum
power=`echo "scale=4; $sum ^ $pow" | bc`
echo $power
product=`echo "scale=4; $p * $power" | bc`
echo $product
ci=`echo "scale=4; $product - $p" | bc`
echo "compound interest: $ci"





<------------------------------------------------------->
count.sh


read -p "enter a filename: " name

if [ -f $name ]; then
    count1=`cat $name | tr -d -c '[a-zA-Z]' | wc -c`
    count2=`cat $name | tr -d -c '[0-9]' | wc -c`
    count3=`cat $name | tr -d [a-zA-Z0-9] | wc -c`
    echo `expr $count1 + $count2 + $count3`
fi




<------------------------------------------------------->
index.php


<?php
    $server="localhost";
    $username="trainee";
    $password="tky4U63#MZjVqu";
    $database="test_doom";

    $conn = mysqli_connect($server, $username, $password, $database);

    if ($conn) {
        echo "connection established";
    } else {
        echo "connection failure";
    }
?>




<------------------------------------------------------->
line.sh


#!/usr/bin

read -p "enter file name: " name
if [ -f $name ]; then
    echo `grep -n '' $name` >> $name
fi




<------------------------------------------------------->
mahesh.txt


. nhtetertrd ktit .
i7uliugpigi.
.ir68ro797o9r89p8

;ouy78iyk,uy8y7
.7tio87i7887.





<------------------------------------------------------->
max.sh


filepath=""
max=-1

for file in *; do
    currentMax=`stat -c %s "$file"`
    if [ $currentMax -gt $max ]; then
        max=$currentMax
        filepath=$file
    fi
done

echo "$filepath `wc -c -l -w $filepath` "
cat $filepath




<------------------------------------------------------->
morem.txt


Sohan is a talented programmer with a passion for coding.
He has mastered several programming languages, including Python and Java.
From a young age, Sohan found joy in solving complex problems.
His coding projects showcase his creativity and technical skills.
Sohan enjoys participating in hackathons with fellow programmers.
He often collaborates on innovative solutions during these events.
Beyond programming, Sohan is an avid gamer.
He loves immersing himself in various gaming worlds.
His favorite genres include RPGs and first-person shooters.
Sohan often hosts game nights with friends to unwind.
He believes gaming enhances his problem-solving abilities.
Sohan consistently ranks at the top of his class academically.
His peers admire his ability to balance studies and hobbies.
He enjoys mentoring younger students in programming.
Sohan shares his knowledge to help others grow in tech.
He is particularly interested in artificial intelligence.
Sohan spends hours researching advancements in AI and ML.
His ambition is to create impactful software solutions.
He actively seeks feedback on his projects for continuous improvement.
Sohan remains humble despite his numerous achievements.
He enjoys discussing the latest trends in the gaming industry.
Sohan is known for his strategic thinking in both gaming and coding.
He often analyzes game mechanics to improve his skills.
His dedication to learning drives him to stay updated with technologies.
Sohan’s friends describe him as a well-rounded individual.
He believes in the importance of balancing work and play.




<------------------------------------------------------->
nahak.txt







<------------------------------------------------------->
notesmaker.sh


for file in *; do
    if [ -f $file ]; then
        echo "<------------------------------------------------------->" >> ./php/notesUnix.md
        echo $file >> ./php/notesUnix.md
        echo -e "\n" >> ./php/notesUnix.md
        cat $file >> ./php/notesUnix.md
        echo -e "\n\n" >> ./php/notesUnix.md
        echo -e "\n" >> ./php/notesUnix.md
    fi
done




<------------------------------------------------------->
palindrome.sh


read -p "enter a string: " str

reverse=`echo $str | rev`
echo $reverse
if [ $reverse == $str ]; then
    echo "palindrome"
else 
    echo "not palindrome"
fi




<------------------------------------------------------->
palin.sh


read -p "enter a string: " str

rev=""
len=${#str}
for(( i=0; i<$len; i++ )); do
	char=${str:i:1}
	echo $char
	rev=$char$rev
done
echo $rev






<------------------------------------------------------->
prasad.txt



	she is gupt programmer
	she is hidden topper
	she play little game and study more
	but show inverse of above line
	she loves frontend development
	she is a night owl
	she want to become a full stack developer
	hi hi hi hi hi hi hi hi hi hi hih ih

	hidden
	hidden
	himesh
	hittler
	hittler
	hiking





<------------------------------------------------------->
random.txt


bcabcabca bca bca bca
bca bca bca bca bca bca bca bca
BCA BCA BcA bCa bCA BcA
acb acb 1234 1234, 12.4 1234 12 34 12_34 12345
123456677
12345
11224
12334dsggrfgdf45556 1234567





<------------------------------------------------------->
random.txte


 gamer
  programmer
  
    student
        trainee





<------------------------------------------------------->
replace.sh


read -p "enter a filename: " name

# if [ -f $name ]; then
#     sed -e 's/hi /hello /g' -e 's/she /he /g' $name
# fi

sed





<------------------------------------------------------->
result.txt


1:Sohan is a talented programmer with a passion for coding.
2:He has mastered several programming languages, including Python and Java.
3:From a young age, Sohan found joy in solving complex problems.
4:His coding projects showcase his creativity and technical skills.
5:Sohan enjoys participating in hackathons with fellow programmers.
6:He often collaborates on innovative solutions during these events.
7:Beyond programming, Sohan is an avid gamer.
8:He loves immersing himself in various gaming worlds.
9:His favorite genres include RPGs and first-person shooters.
10:Sohan often hosts game nights with friends to unwind.
11:He believes gaming enhances his problem-solving abilities.
12:Sohan consistently ranks at the top of his class academically.
13:His peers admire his ability to balance studies and hobbies.
14:He enjoys mentoring younger students in programming.
15:Sohan shares his knowledge to help others grow in tech.
16:He is particularly interested in artificial intelligence.
17:Sohan spends hours researching advancements in AI and ML.
18:His ambition is to create impactful software solutions.
19:He actively seeks feedback on his projects for continuous improvement.
20:Sohan remains humble despite his numerous achievements.
21:He enjoys discussing the latest trends in the gaming industry.
22:Sohan is known for his strategic thinking in both gaming and coding.
23:He often analyzes game mechanics to improve his skills.
24:His dedication to learning drives him to stay updated with technologies.
25:Sohan’s friends describe him as a well-rounded individual.
26:He believes in the importance of balancing work and play.





<------------------------------------------------------->
reverse.sh


read -p "enter number: " number

if [ $number -lt 1 ]; then
    echo "enter some number"
    exit
fi

remainder=0
reverse=""
while [ $number -ne 0 ]; do
    remainder=$(( $number % 10 ))
    reverse+=$remainder
    number=`expr $number / 10 `
done

echo $reverse
# i want to reverse a number
# reversed_number=$(echo $number | rev)
# echo $reversed_number
# echo "number of argument $*"




<------------------------------------------------------->
search.sh


#!/usr/bin

read -p "Enter file name: " name
firstchar=${name:0:1}
echo $firstchar

for file in *; do
	if [ "$firstchar" == "${file:0:1}" -a -f "$file" ]; then
		echo "words:`wc -w $file` lines: `wc -l $file`"
	fi
done






<------------------------------------------------------->
secondHighest.sh


len=$#
echo $#
second=-1
max=-1
# for (( i=0; i < $len; i++ )); do
#     if [ $max -lt $i ]; then
#         second=$max
#         max=$i
#     fi
# done

for arg in "$@"; do
echo $arg
    if [ $max -lt $arg ]; then
        second=$max
        max=$arg
    fi
done
echo $second




<------------------------------------------------------->
sum.sh


read -p "enter a number: " number
len=${#number}
even=0
odd=0
for (( i=0; i < $len; i++ )); do
    num=${number:i:1}
    mod=$(( num % 2 ))
    if [ $mod -eq 0 ]; then
        even=$(( num + even ))
    else 
        odd=$(( num + odd ))
    fi
done

echo "even=$even and odd=$odd"




<------------------------------------------------------->
toDeci.sh


read -p "enter hexa number: " hex

sum=0
len=${#hex}
pow=`expr $len - 1`
for (( i=0; i<len; i++ )); do
    char=${hex:$i:1}
    case $char in
        a)
            char=10
        ;;
    esac
    mul=$(( 16 ** pow ))
    current=$(( char * mul ))
    pow=$(( pow - 1 ))
    sum=$(( sum + current ))
done
echo $sum




<------------------------------------------------------->
toHexa.sh


# convert decimal to hexa
# binary to hexa

read -p "enter decimal number only: " number

if [ $number -lt 0 ]; then
    echo "enter again: "
    exit
fi

result=""
remainder=0
while [ $number -ne 0 ]; do
    remainder=`expr $number % 16`
    number=`expr $number / 16`
    if [ $remainder -gt 9 ]; then
        case $remainder in 
            10)
                result="a"$result
            ;;
            11)
                result="b"$result
            ;;
            12)
            result="c"$result
            ;;
            13)
            result="d"$result
            ;;
            14)
            result="e"$result
            ;;
            15)
            # echo $remainder
            result="f"$result
            ;;
        esac
    else
        result=$(( $remainder$result ))
    fi
done
echo $result;




<------------------------------------------------------->
toOcta.sh


read -p "enter a decimal number: " dec

octal=""
while [ $dec -ne 0 ]; do
    remainder=`expr $dec % 8`
    octal=$remainder$octal
    dec=`expr $dec / 8`
done

echo $octal




<------------------------------------------------------->
trim.sh


#!/usr/bin

read -p "enter file name: " filename

if [ -f $filename ]; then
	`sed -e 's/^[ \t]*//' -e '/^$/d' $filename`
fi





<------------------------------------------------------->
whoami.sh


read -p "enter you id: " id
current=`whoami`
actualid=`id -u $current`

if [ $id == $actualid ]; then
    echo  "you are the owner $current"
else    
    echo "get lost"
fi





