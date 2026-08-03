## with echo command , shell variable 

__week 5__ 

__echo hello    world__ without double quote it take these words as in a list and give delimiter 
_hello world_ 

if open with __'__ it will close with __'__ untill then it will ask for more input in next line 
if open with __"__ it will close with __"__ untill then it will ask for more input in next line 

__echo "$USER"__ -> mukul_pandit <- __echo "$USERNAME"__ if user name variable is defined else it will give in user commmand. 
*double quotes is used for shell variables* 

__echo "$HOME"__                __echo "$PWD"__
*/home/mukul_pandit*            */home/mukul_pandit* 

__echo "hostname is $HOSTNAME and username is $USER"__ interpresting inside the double quotes 
\$HOSTNAME for escaping the meaning of $ symbol 

__printenv__ = __env__ printing all shell variable tha are present 
__set__ for all shell variable in detail with there command and some condition 

__printenv HOME__ printing path of home command 

if __alias date="date -R"__ now to run real date you can 
__/usr/bin/date__ or __cd /usr/bin__  mukul_pandit@DESKTOP-O2A5EAO:/usr/bin$ __./date__ or __\date__ to escape the alias 

__echo $PATH__ : tells your terminal where to look for executable programs (commands) when you type them

__echo $$__ process id 
__ps__ processes , __ps --forest__ in forest views 
__ps -f__ for parents id : __ps -e__ -> view every single process currently running on your system. 
__ps -ef__ combining both upper command 

__myvar="hello mahanagrani"__ setting up variable 
__echo $myvar__ ->  hello mahanagrani

__echo $?__ 0 if prev commands works , 1 to 255 if it did not worked 
__[[ -v myvar ]];__ if a variable has been set (defined), use __echo $?__ to check if it worked or not 

__unset myvar__ to unset the value of myvar command 
__[[ -z ${myvar+x} ]];__ check if a variable is completely unset. ,x is commodity you can change it with anything  
 __echo $?__ to check if it has ran or not 

__echo "$myvar.txt" -> FileName.txt__ , __echo "$myvar_txt"__ -> it will think it is file name so use 
flower bracket __echo "${myvar}_txt"__ ->  __FileName_txt__ 

__bash__ for new shell 
__export myvar=3.14__ use export in parent shell so that it can also be used in child shell but
exporting something in child shell does not export or change value in parent shell  

__mydate=`date`__ using back quotes it just gave the value of date to mydate variable in this way you can give command output to variable name 

__echo ${myvar:-hello}__ *-* it means that if the variable does not have value than what is should be printing 
__echo ${myvar:=hello}__  if variable was not set, set it to something else using = command 
__echo ${myvar:+HELLO}__ "If myvar is set and not empty, print 'HELLO'. Otherwise, print nothing."

__echo ${!H*}__ it will return a space-separated list of all currently defined environment and shell variable names that start with the letter "H".

__echo ${#mydate}__ : "length of the value of that variable"
__echo ${myvar:4:7}__ : "first is offset second is no. of character to be displayed from the offset 
__echo ${myvar: -3:3}__ : negative to do from last 
__date +"%d %B %Y"__ date , month , year 

## myvar=myfile.txt.jpeg 
__echo ${myvar#*.}__ : txt.jpeg, only hiding words before one dot 
__echo ${myvar##*.}__ : jpeg, hiding word before two dot 
__echo ${myvar%.*}__ : myfile.txt, to show before one dot   
__echo ${myvar%%.*}__ to show before two dot 
__echo ${myvar/e/E}__ to change small e to capital E only once that occurs first time 
__echo ${myvar//e/E}__ to change every e that occurs to E 
__echo ${myvar/#m/M}__ change m to M if it is in front, else nothing  
__echo ${myvar/%g/G}__ change g to G if it is in back, else nothing 

__echo ${myvar/%jpeg/jpg}__ can also change last of word, use // for change of jpeg in full string 
__echo ${mydate,}__ make everything in lower case 
__echo ${mydate,,}__ make everything in upper case 

__declare -i mynum__ to only store the interger, if try to store string it will give 0, 
__declare -l myvar__ to only store lowercase, automatically converted to lowercase.
__declare -u MYVAR__ to only store uppercase,  
            *use + to remove restriction* 

__declare -r today__ to read only, can not even remove it using + 

## declare -a arr, declaring array, 
arr[0]=sunday 
arr[1]=monday

__echo ${arr[0]}__ to get value 
__echo ${#arr[@]}__ to know the size of array 
__echo ${arr[@]}__ to get the values 
__echo ${!arr[@]}__ to get the index that are there as *here the index can be non continous like 1 2 100* 

__unset `arr[100]`__ to unset the value 
__arr+=(tuesday)__ to add one value 
__arr=(sunday munday tuesday thrusday friday saturday)__ to set the arr value in one go, it is not append, 

__declare -A hash__ creates an associative array (often called a hash map, dictionary, or hash table) named hash.

hash[0]="Amal"
hash[1]="Biaml"
hash["mm1b2001"]="Charlie"
hash["new_baccha"]="Chandalika"
__echo ${hash[new_baccha]}__ to get value 

__find $HOME -print__ searches for and displays the path of every file and directory located inside your home directory.

__find /usr -type d -name 'man*' -print__ searches the /usr directory specifically for directories whose names start with "man" and prints their full paths to the terminal.

The command __du -sh logfiles/__ calculates and displays the total disk space used by the logfiles directory in a human-readable format.

The command __tar -cvf logfiles.tar logfiles/__ creates a new, uncompressed archive file (often called a tarball) containing the contents of the logfiles/ directory.

__gzip logfiles.tar__ Compresses the logfiles.tar file using the DEFLATE compression algorithm.
replaces the original logfiles.tar file with a compressed version named logfiles.tar.gz. (By default, gzip deletes the uncompressed source file after successfully creating the compressed one)

__gunzip logfiles.tar.gz__  Decompresses (unpacks) the logfiles.tar.gz file.  
Result: It reverses the compression process, deleting logfiles.tar.gz and restoring the original uncompressed logfiles.tar file back to its full size. (gunzip is essentially a shorthand shortcut for gzip -d).


__bzip2 logfiles.tar__
What it does: Compresses the logfiles.tar file using the Burrows-Wheeler block sorting text compression algorithm and Huffman coding.

Result: It replaces the original logfiles.tar file with a compressed version named logfiles.tar.bz2 (deleting the uncompressed .tar file in the process).

__bzip2 -d logfiles.tar.bz2__ What it does: Decompresses (unpacks) the logfiles.tar.bz2 file.
Breakdown:
bzip2: The compression utility.

-d: Stands for decompress (you can also use the standalone bunzip2 logfiles.tar.bz2 command for the exact same result).

Result: It removes the .bz2 extension and restores the original uncompressed logfiles.tar file.

1. __compress logfiles.tar__
What it does: Compresses the logfiles.tar file using the older Lempel-Ziv (LZ78) algorithm. 
*Result: It replaces the original file with a compressed version named logfiles.tar.Z (automatically appending a capital .Z extension and deleting the uncompressed .tar file).*

2. __uncompress logfiles.tar__ (or uncompress logfiles.tar.Z)
What it does: Restores the compressed .Z file back to its original uncompressed state.

*Result: It looks for logfiles.tar.Z, extracts it, deletes the .Z file, and leaves you with the original logfiles.tar. (Note: Even if you type uncompress logfiles.tar, the utility is smart enough to look for and find logfiles.tar.Z automatically).*

## content of make.file 
BACKUPDIR=/home/gphani/backup
DATESTAMP:=$(shell date +"%Y-%m-%d_%H.%M")
TARBALL=backup_$(DATESTAMP).tar

backup: file1 file2
	@echo "Backing up file1 file2 to $(DATESTAMP)"
	tar -cvf $(TARBALL) file1 file2
	@ls -l $(TARBALL)
	mv $(TARBALL) $(BACKUPDIR), what does this command do 

*BACKUPDIR=/home/gphani/backup: Defines a variable pointing to the destination directory where the final backup archive will be stored.*

*DATESTAMP:=$(shell date +"%Y-%m-%d_%H.%M"): Runs a shell command to generate a precise timestamp (e.g., year, month, day, hour, and minute) so that every backup file has a unique name.*

*TARBALL=backup_$(DATESTAMP).tar: Creates a filename variable for the archive using that generated timestamp (e.g., backup_2026-07-23_17.11.tar).*

*backup: file1 file2: Declares a target rule named backup which depends on the existence of file1 and file2.*

*@echo ...: Prints a message to your terminal indicating that the backup is running for those files.*

*tar -cvf $(TARBALL) file1 file2: Combines file1 and file2 into a single uncompressed .tar archive file named with your timestamp.*

*@ls -l $(TARBALL): Displays the file details (such as size and permissions) of the newly created archive in your terminal.*

*mv $(TARBALL) $(BACKUPDIR): Moves the completed tarball from your current folder into the specified BACKUPDIR (/home/gphani/backup).*

__make -f make.file backup__ to run this make.file script , now to run it again you need to change the content of either of the file 

## bash script part 1 

__running as a source file__ 
__. s1.sh__ or __source s1.sh__ used to execute the contents of a script file directly within your current shell session. 

__./s1.sh__ Runs in a subshell using the interpreter specified in the shebang; requires chmod +x permission.

__if statement in this thing__
--------------------------------------------
if (condition); then 
            *something something karo*
fi 
--------------------------------------------
__for command__

for i in arg1 arg2 arg3
do
        echo $i
done

--------------------------------------------
for i in $(ls /bin/z*)    <==>    for i in $`ls /bin/z`

__read pname__ : 
Pauses execution and waits for the user to type an answer, saving their input into a variable named $pname.

---------------------------------------------------

case $pname in
        [gG]imp | inkscape)                        *if match this then print this* 
                echo good choice
                ;;                                *breaker that break when it get execute* 
        [aA]dobe*)                                          
                echo that costs a lot and needs cloud  
                ;;
        imagej)
                echo measuring things on the image?
                ;;
        *)
                echo I did not know $pname could do image stuff
                ;;
esac                                                         *closing of case statement* 

----------------------------------------------------------------
#!/bin/bash
begin=1                                               *setting variable*
finish=10                                                 *setting variable*
for (( a = $begin; a < $finish; a++ ))       
do
        b=$(( a**2 ))
        echo $b
done                                *close* 

--------------------------------------------------

#!/bin/bash
filename=largefile.txt           
if [ -e $filename ]             
then
        echo file $filename exists
        exit 1
fi

i=1
while [ $i -lt 10 ]                    *while using*
do
        echo $i $[$i+1]
        (( i++ ))
done > $filename           *sending output to $filename*

echo file $filename written                 
ls -l $filename

*break -> to break a loop or condition* 
In Bash, break n exits n levels of nested loops, counting starting from the innermost loop where the break command is executed:
break 1 (or just break): Exits the innermost (current) loop.
break 2: Exits the innermost loop and its immediate parent loop (2 levels total).
break n: Exits n enclosing loops from the inside out.
-------------------------------------------------------------------
1. the shift keyword renames positional parameters ($1, $2, $3...) by shifting them to the left.
2. When you run shift, the old value of $1 is discarded, the value of $2 becomes the new $1, $3 becomes the new $2, and so on.

Before shift:
$1 = "apple"
$2 = "banana"
$3 = "cherry"

--> Execute 'shift'

After shift:
$1 = "banana"
$2 = "cherry"
---------------------------- 

__important things__ 
1. grep -P (Perl-Compatible Regular Expressions)
Enables PCRE engine in grep.

Provides advanced regex features not available in default BRE (grep) or ERE (grep -E), such as lookarounds.

2. (?=...) (Positive Lookahead)
Purpose: Checks if the text inside (?=...) follows immediately after the current match, without including it in the match output.

Why use it with grep -o?
grep -o only prints what is explicitly matched.

Lookaheads allow you to assert/test surrounding patterns (e.g., ,30) while extracting only the target string (e.g., John Doe).
------------------------------------

__fold -w1 | paste -sd+ - | bc__
How It Works
fold -w1: Breaks the input string from standard input into individual single-character lines.

Input 12345 becomes:

Plaintext
1
2
3
4
5
paste -sd+ -: Combines all lines sequentially (-s), inserting a plus sign (+) as the delimiter (-d+).

Output: 1+2+3+4+5

bc: Evaluates the mathematical string 1+2+3+4+5 and prints the final sum (15) to stdout.
--------------------------------------
__if [ -z "$1" ]; then__ : -z is a string operator that tests if the given string is empty (length is zero). 

__find "$1" -type f -empty -print -delete__ you know it 

__exec command__
----------------------------------------------------
Core Functionality : 
Process Replacement: Replaces the currently running shell process with a new command instead of creating a new child process.

Same PID: The new command inherits the exact Process ID (PID) and environment of the shell that launched it.

No Return: Control never returns to the original shell script or terminal session after exec runs (unless the command fails to execute).

Common Uses
Container Entrypoints: Used in Docker or startup scripts to run the primary application as PID 1, allowing it to receive system signals (like SIGTERM) directly.

Global Redirection: Used in scripts without a command (e.g., exec > log.txt 2>&1) to redirect all standard output and errors globally.

Auto-Exit Sessions: Replaces a shell session with an interactive tool (e.g., exec python3), ensuring the terminal
--------------------------------------------------------

__eval forces Bash to parse the line twice before executing it.__
*eval $cmd $fmt* 
It takes the string arguments you give it, combines them into a single string, evaluates/parses that string as a fresh Bash command, and then executes it in the current shell. 
-------------------------------------------------------------

__while getopts "ab:c:" options;__           

while getopts "ab:c:" options;       *— Flag -a is standalone, b: — The colon : means flag -b requires an*  
                                     *argument , same for c*
do
    case "${options}" in
        b)
            barg=${OPTARG}
            echo accepted: -b $barg
            ;;
        c)
            carg=${OPTARG}
            echo accepted: -c $carg
            ;;
        a)
            echo accepted: -a
            ;;
        *)
            echo Usage: -a -b barg -c carg
            ;;
    esac
done


*options — The name of the variable where getopts stores the current flag letter during each loop iteration.*
*getopts automatically stores the value you passed into the built-in variable $OPTARG.* 
--------------------------------------------------------------

echo select a middle one                  
select i in {1..10}                       *select command use* 
do                                              
    case $i in                                
        1 | 2 | 3)                           
            echo you picked a small one;;
        8 | 9 | 10)
            echo you picked a big one;;
        4 | 5 | 6 | 7)
            echo you picked the right one
            break;;
    esac
done
echo selection completed with $i            


