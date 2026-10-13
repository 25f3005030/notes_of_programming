__local__

Declares a local variable (like local filename="$1") so it stays safely tucked inside the function box without 
leaking out into the rest of the terminal environment. 📦

*So NF != 2 translates to: "The number of fields is not equal to 2."*

[ -z "$line" ]	Tests if the variable string length is zero (empty)
---------------------

__while IFS= read -r line || [ -n "$line" ]; do__

IFS=: Setting IFS (Internal Field Separator) to an empty value prevents Bash from trimming leading or trailing spaces from filenames. 🧹

read -r line:

read: Reads a line from stdin and assigns it to the variable $line.

-r: Disables backslash escaping. (Without -r, a filename containing \n or \t would be interpreted incorrectly).

*In Bash, OPTARG is a built-in environment variable used automatically by the getopts command.*

*When you use getopts to parse command-line flags, OPTARG holds the value (argument) that belongs to a specific flag 🏷️.*
-------------------------------------------------

#!/usr/bin/gawk -f

BEGIN {
    print "BEGIN action is processed";
}
{
    print "Default action is processed";
    print $0; # 👈 $0 prints the whole current line!
}
END {
    print "END action is processed";
}

*💡 Bonus Insight: If you define multiple BEGIN blocks (even at the bottom of the script), AWK groups all BEGIN statements together and executes them before reading the input! 🌸*

Passing Input via Arguments:

Bash
./block-ex-1.awk block-ex-1.input 
--------------
Passing Input via Piping (Standard Input):

Bash
cat block-ex-1.input | ./block-ex-1.awk
----------------------------------------------------------------------
FNR 🔢 — File Record Number: Tracks the line counter for the current input file.

NF 🧮 — Number of Fields: Holds the total count of split columns/words in the current record.

$0 📜 — Represents the entire current record (the full line).

$1 🏷️ — Represents the first field (first word/column) of the current line.

FS ✂️ — Field Separator: Sets custom delimiters for line splitting (e.g., FS="[ .;:,-]" splits lines using spaces, dots, semicolons, colons, commas, or hyphens).
---------------------------------------------------------------------
Regex Pattern Matching Operator (~):

$1 ~ /[[:alpha:]]/ — Evaluates to true only if the first field specifically contains an alphabetic character.

Space Sensitivity in Regex:

/ [[:digit:]]/ vs /[[:digit:]]/ — You identified that a leading space inside regex requires a literal space before the digit, which caused attached digits like mm22b901 to be skipped until the space was removed!

Conditional Logic on Field Counts:

NF > 2 vs NF <= 2 — Used conditional statements to filter and tag records based on whether they split into more than two fields.
-----------------------------------------------------------
#!/usr/bin/gawk -f
BEGIN{
        print "BEGIN action is processed";
        FS="[ .;:,-]"
}
NF > 2 {
        print "acceptable record:" FNR ":" $0;
        print "number of fields in the current record:" NF;
}
NF <= 2 {
        print "not acceptable record:" FNR ":" $0;
        print "number of fields in the current record:" NF;
}
END{
        print "END action is processed";
}
----------------------------------------------------------------
🧱 1. Creating/Defining the Function (func-lib.awk)
To define a function in AWK, you use the function keyword, followed by the function name, parameters in parentheses, and the code body inside curly braces {}.

Awk
# func-lib.awk

function myfunc2(a)
{
    b = a + 0       # Coerce 'a' to a number
    return sin(b)   # Return the sine value
}
⚙️ Metaphor: Think of this file as your custom blueprint library 📐. It doesn't run any code on its own—it just defines how tools should work when called!

⚙️ 2. Calling/Using the Function (func-example.awk)
In your main script, you invoke the function by passing arguments to its name, just like built-in functions.

Awk
# func-example.awk

{
    a = $1
    b = myfunc2(a)  # 👈 Calling the function from our library
    print "b=" b
}
🚀 3. Executing Everything Together in the Terminal
Because the definition is in func-lib.awk and the main logic is in func-example.awk, you feed both files to the gawk command using multiple -f flags:

Bash
echo "12.5" | gawk -f func-lib.awk -f func-example.awk
🔄 Execution Order Under the Hood:
Load Phase: gawk reads func-lib.awk first and stores myfunc2 in memory 🧠.

Compile Phase: gawk reads func-example.awk and links the call myfunc2(a) to the loaded definition.

Execution Phase: Data ("12.5") flows in through the pipe |, triggering the program to run and output the result! 🎉
--------------------------------------------------------------
awkAho Weinberger KernighanThe standard specification/command name
📜gawkGNU AWKThe actual GNU implementation installed on Linux 🚀
Bottom Line: You can type awk or gawk interchangeably on Linux—gawk just explicitly specifies the GNU version! ✨
------------------------------------------------------------------
Feature                      echo ""      cat xaa (empty file)
Lines / Records Sent     1 empty record   📄0  records 🕳️
--------------------------------------------------------------------

writing a function in a script : 
function function_name(parameter1, parameter2)
{
    # Code operations
    return value   # Optional
}

# Calling the function in the main body
{
    a = $1
    b = myfunc2(a)   *this is the function that we are calling* 
    print "b=" b
}
--------------------------------------------------------------
⚙️ 2. Executing Modular AWK Scripts
When function definitions live in a separate file (like a library), combine them using multiple -f flags in terminal:

Bash
__gawk -f func-lib.awk -f func-example.awk__
Execution Order: gawk loads func-lib.awk first into memory 🧠, then compiles and executes func-example.awk using those defined tools! 🚀
*func-lib.awk acts as your library/toolbox 🧰 where functions like myfunc1() and myfunc2() are declared and defined.*
*func-example.awk is your main program 🚀 where those functions are called and executed on incoming records (like in the main block and the END block).*
-------------------------------------------------------------
dig +noall +answer -x 34.234.167.93	
Performs a Reverse DNS Lookup using dig with flag options to hide noise (+noall) and display only the PTR answer record (+answer).
------------
__awk 'BEGIN{FS=" "}{d=substr($4,2,11); print d}' access-head.log__
substr($4, 2, 11) ✂️: The substring function extracts a slice of text from field $4.
1st argument ($4): The target string [27/Jan/2022:00:01:11.
2nd argument (2): Start extracting at character position 2 (skipping index 1, which is [).
3rd argument (11): Extract a total length of 11 characters (27/Jan/2022 is 11 characters long).
-----------------------------

1️⃣ awk Command (Run in Bash Terminal)
Bash
awk 'BEGIN{FS=" ";}{print NR, $0;}' input.txt

awk: Invokes the awk interpreter from your terminal shell.' ... ': 
The single quotes tell Bash: "Pass everything inside directly to AWK without expanding variables or changing anything!
"BEGIN{FS=" ";}: Executed before reading any lines; sets the field separator to a space.
{print NR, $0;}: Executed for every line in input.txt.NR $\rightarrow$ Current Record (line) number.$0 $\rightarrow$ 
The entire current line text.input.txt: The target file passed directly to the terminal command.


2️⃣ awk Script (Saved in a File)File: yourScript.awk

Awk

BEGIN { 
    FS = " "; 
} 
{ 
    print NR, $0; 
}

How to run it from Bash:Bashawk -f yourScript.awk input.txt

No Outer Quotes: Since this code lives inside yourScript.awk, Bash doesn't touch it, so you don't need single quotes around the code block!-f Flag: Tells awk to read and execute the program rules stored inside the specified file (yourScript.awk).
----------------------------------------------------------
week-10 (knowing your hardware)

__hwinfo__ for hardware information 
__lshw__ is also for hardware information 
__lshw -c display__  for a particular thing  
__cat /proc/cpuinfo__ for cpu architecture 

__cat /proc/partitions__ tell about partitions 

__lspci__ stands for "List PCI"! 🌸

It is a built-in Linux utility that lists all devices connected to your system's PCI (Peripheral Component Interconnect) bus.

__dmidecode__ to se all information in visualizing format 

__sudo hdparm -Tf /dev/sda__

/dev/sda:
 Timing cached reads:   8504 MB in  2.00 seconds = 4262.03 MB/sec
*test and benchmark your storage drive's speed, specifically checking how fast your system can read data directly from the Linux Kernel RAM Cache without touching the physical disk! 🏎️💨* 

__ifconfig__ (short for Interface Configuration) is used to view and manage your network adapters (Wi-Fi, Ethernet, loopback, virtual bridges).

__df -h__ — Disk Space Usage 💾
df stands for Disk Free. It shows how much storage space is used and available on all mounted file systems.

__iostat -dx /dev/sdb & iostat -dx /dev/sda__

iostat: The core monitoring tool.

-d: Displays the disk utilization report only (hides CPU statistics).

-x: Displays extended statistics (shows extra metrics like wait times, queue sizes, and request sizes).

/dev/sda & /dev/sdb: The specific target storage drives in Linux system syntax:

sda: First storage drive (Disk A).

sdb: Second storage drive (Disk B).
--------------------------------------------------

