# ***linux commands***
## ps gives a snapshot of current progress 


## cd ->
  __to change the directory__ 
  __***cd ~*** for home directory__
  __***cd -*** for getting in previous directory 
  
## mkdir ->
  __to make a directory__   
  -> eg -> mkdir level1 
  
## chmod g-r level1  
  -> __removed the read permission from the group__  
  -> __+__ to give permission __-__ to remove the permission   
  -> __u__ for user, __g__ for group, __o__ for others    
  -> __r__ for read , __w__ for write and **x** for executable   
  
  ___using code for change___ 
  -> __chmod 700 level1__ ie. only having user permission and removing permission for group and other 
  
## creating files in directory 
  -> __touch file1__ 
  
## ***making copy of a file***
  -> __cp file1 file2__
  
## moving file to one above 
  -> __mv file2 ..__  
  --> using mv to change file name   
    --> __mv file2 file2a__  
  --> moving file inside:  
    --> __mv file2a level1__  
    
## man--> for manual 
  -> eg: man rm   
  
## making an alias so that it ask everytime: 
  -> __alias rm="rm -i"__   
  -> it will ask "y" or "n"  
  __unalias rm__ to remove the rm as an alias

  
## removing a file
  -> __rm "file one"__  
## i node number
  -> __ls -li__  
  __combining the i node and showing all__  
  -> __ls -lia__    
  -> hard link means that the same i node number is there in direcoty and its sub directory   
## ***whoami*** to ask your name!! 
## reading inside file   
  -> __less filename__       
  --> you can read inside the file, press q for exit   
## get to know type of file     
  -> file filename    
  
## timestamp 
## to show inside the sub direcotry   
  -> __ls -l level1__  
## to get long version of directory    
  -> __ls -ld level1__  
  -> __ls -ldi level1__ -> to get the i node number     
  -> __very flexibele__ -> ls -l level1 -di <==> ls -d level1 -li <==> ls -i level1 -dl <==> ls level1 -idl      
  --> also like __ls -l --directory --inode level1__ some has long form some does not, use man command for it 

## knowing files better wali command   
  -> __less profile__ to see content of a file, here profile is name of the file     
  -> __cat profile__  to concatente the file data on screen, it just dump the data     
  --> __more profile__ similar to less   
  -> __head profile__ just print the first 10 lines of a file     
  -> __head -n 5 profile__ print the number of lines you want   
  -> __tail profile__ last ten lines of profile 

## more commands    
  -> __wc profile__ give us lines words and bytes of a file   
  -> __wc -l profile__ for just number of  lines  
  -> __which less__ gets to know the location of command  
  -> __whatis which__ gives us a short description of how things are  

## get to know more commands  
  -> __apropos__ or __man -k__ get to know new command by keyword   

## shell commands:  
  -> __help__ get to know shell and its commands  
  -> __info__ get informaton about commands and then click on star to enter inside to see inside commands   
    -> use __<__ to get one step out  
  -> __type ls__ give us information about a particular command one liner 

## setting a shortcut 
  -> __alias ll="ls -l"__ it makes shortcut to command  
  use -> ll   

  -> __alias__ to get to know all alias present   
  -> __unalias ll__ to remover the alias  

## multiple argument 
  -> __touch file1 file2 file3__ three files creating 

  __remove a filled directory -> not possible, so either make it empty or__ 
  use __rm -r mydir__ forced removal of directory   

  -> copying one direcotry to other __  
  __mv dir1/file1 dir2/__ directly moving files without changing directory , source destination   
  __cp -r mydir mydir2__  copy command does not assume recurssion we have to give -r so that it can work  
  but _mv_ commands assumer recursssion so we dont have to tell explicitly  

  __cp -r level1/* new_direct/__ copying inside content of level1 directory to new_direct   

## links : _make links between files_ 
  __ln -s file1 file2 => ln -l source destination__  (soft link ) 
  __ln file1 file2__ creating without s will give them the same i node number (hard link )    

## file size:
_files if they are less than a block take whole block or take {no block}, they will never take part of a block_ 
__stat znew__ for file size   
__du znew__ for aliean , __du -h znew__ for human   
  __uname -a__ give all comprehnsive system information   
  __free__ or __free -h__ gives more readable form about somethings   
  __cat partitions__ tells about partitions __df__ for more   
  
## -----------------------------------------------------------------------------------  

## command line editor (ed editor )
__echo "line-1 hello world" > test.txt__ --> creates a new file named test.txt (or overwrites it if it already exists) and inserts the  string "line-1 hello world" into it.  
__echo "line-2 this is a new line" >> test.txt__ append a second line to this file without erasing the first  

__cat test.txt__ to see the file  

__ed test.txt__ enterning a interactive shell where you can edit a file line by line  
__q__ to quit the shell   

__P__ TO ACTIVATE THE COMMANDS  
  -> __*1__ for first line  
  -> __*$__ for last line of file   
  -> __*,p__ for all content of the fle   
  -> __*2,3p__ for second and third line  
  -> __*/hello/__ search for the pattern (words) in which line it is  
  -> 
  -> __*1__ first line then __*+__ go to the next line, __*-__ go to the previous line  
  -> __*;p__ you go the end of the buffer, from that line in which you are (printing all lines in between ) 
  -> __*%p__ to see all the line  
  -> __*.__ for current line  
  -> __*!date__ give me the date  
  -> 
  -> _i am adding the line_   

  -> __*4__ setting the fourth.   
  -> __*r !date__ read the date, __*,p__ now i will get all lines and then date at bottom but it is not added at the bottom yet  
  -> now, __*w__ to write date into the file  

-> __.d__ to delete the current line  
-> __*1__ selecting position of line(here 1 ), __*a__ write in next line then __.__ to finish line in next line and then enter.  

-> __*2__ go to the line  (this is the line after first line) 

-> __*s/this/This/__ here s for search /word/replacment word/ 

-> __*2p__ you are printing second line (This is the line after first line) 

->  _you have to write __*w__ after making any change_  

-> __*5,6j__ to join 5th and 6th line with each other   
-> __*m1__ moving the current line on position on 1st (line postion start with 0) __*m0__ for 0th position.   
-> __*u__ undo the change that i have done  
##  __1,$s/\(.*\)/PREFIX \1/__    

__1,$__ for the first to last line ,__(.*__: The dot . matches any character, and the asterisk * matches zero or more of those  characters. Together, entire content of the line.)  

PREFIX :text insert at the beginning of each line,  
_\1: This is a back-reference. It tells ed to take the text that was captured inside the \(...\) in the "Find" section and place it here  ._ 

__3,5s/PREFIX/prefix/__ from third to fifth i am substituting the PREFIX to prefix  

## readlink -f /usr/bin/pico  
-> it is pointing to /usr/bin/nano  

.bashrc _the bash shell code_ _copy it for making any change_ 
## nano editor  
  -> visual 
  nano test.bashrc ( i made a copy earlier by cp command of bashrc-> test.bashrc )  
  -> ctrl + o to overwrite the command press enter and ctl+x to out of file   
  _see notes for all commands and features_   

## vi editor 
_just see the pdf bro it has all the commands_ 
__dmseg > dmseg.txt__ to copy this file , *this is only in home/mukul_pandit* 
__100dd__ will delete 100 lines
__....:..__ it means that there are four character than colon two character so in this way like __%s/...:../hello/g__ g for global in that file .

## emacs editor 
__emacs -nw filename__ it force it to open in terminal 

__ifconfig__: Your initial attempt to view network interfaces (which triggered the discussion on modern alternatives).
__ip addr__: The modern command used to successfully list your network interfaces and IP addresses.
__nslookup www.iitm.ac.in__: Your first attempt at a DNS lookup.
__dig google.com__: Suggested for practice to see a successful forward DNS query.
__traceroute www.iitm.ac.in__: Suggested for visualizing network paths.


## combining commands and files 
__ls ; date ; wc -l /etc/profile ;__ execute all commands one by one 
__(ls ; date ; wc -l /etc/profile ;)__ execute in a subshelll 
__echo $BASH_SUBSHELL__ to see the subshell no.

__(echo $BASH_SUBSHELL)__ 
__1__
to see what subshell is there (when you use bracket it executes in a subshell)

__ls /blah && date__ it means that second command only works if first commands works (like and )
__ls /blah || date__ it means second is only executed if first fails 

______________________________  
__ls -1 /usr/bin__ it will give one command per line of the output 
__ls -1 /usr/bin > file1__ redirect the content of the file to file1
__ls -1 /blah > file1__ give error and overwrite the file (now content is 0)

__hwinfo__ give information about hardware __hwinfo > hwinfo.txt__ redirect it to file 

__cat > file1__ if you have not specify any file you can type from keyboard in this command 
come out using ctrl + D 

__cat__ it will just type and show the word on screen line by line, ctl +d for come out 

__command >> file1__ it will append the file and if not exist it will be created 

__ls $HOME /blah 2> error.txt__ first it will redirect the eroor to eroor.txt file , it will not show error that occured on screen bcoz it redirect it into error.txt file 

## REDIRECTIONS 

__cat < error.txt__ (redirecting the input from keyboard to use file content )
-
__wc < error.txt__ it means content has to be read form command line 
__ls $HOME /blah > file1 2>&1__ redirect both output and error to file1 

__ls /usr/bin | wc -l__ redirecting output of one command to input of second command , but error are only directed to screen 

__ls /usr/bin | wc -l > file1__ (upper command and )redirect output of second command to file1 

__/dev/null__ black hole to direct things (dev is very sensitive do not use anythings else) 

__tee - Copy standard input to each FILE, and also to standard output__ 

__lsb_release -a__  for operating system of linux 

__apt cache search package fortune__ get to know where fortune keyword is (so many fortune type things )

__apt-cache pkgnames__ installed package names 

__apt-cache pkgnames nm__ package starting with nm 

__apt-cache show fortunes__ show information about things 

__md5sum file1.txt__
it gives the stritg that is different for every file (471c7f53bae1ec7c12553dd2424604f2  file1.txt)

__sha1um file1.txt__

__sha256sum file2.txt__ 

## software managment part 2 

__sudo cat /etc/sudoers__ sudo give us permission to get root privilage if we are added on it 

__/etc/apt__ it has all installed files from website that you have installed 

__cat sources.list__ you will get the another adress after that in new one __/etc/apt/sources.list.d/ubuntu.sources__ 

__sudo apt-get updates__ to get the updates 
__sudo apt-get upgrade__ to upgrade the packages that you have installed 

__sudo apt autoremove__  to remove the unesscdery package after upgrading bcoz they were just there to supprt some download and now we have the newer version of that 

__sudo apt-get remove fortunes__ it remove the package __sudo apt-get remove fortune-mod__ it remove the cookies  

__sudo apt-get install fortune-mod__ to install the fortune package

__sudo apt-get reinstall fortune-mod__ to reinstall the package ,to refresh old one 

__cd /var/lib/dpkg/__ -> __less status__ to see status of packages 

__mukul_pandit@DESKTOP-O2A5EAO:/var/lib/dpkg/info$ more wget.md5sums__ 
*mukul_pandit@DESKTOP-O2A5EAO:/var/lib/dpkg/info$ md5sum /usr/bin/wget* 
_c57c56d1d70b45a9327bbb679c8bd43  /usr/bin/wget_

to see if the file has been tempered or not 
__apt search fortune__ to search commands related to it 
## use dpkg

*gives us information about a package* 

__dpkg -l nmap__ gives informatin about the architecture (list)
__dpkg -L nmap__ give us the various files that are installed with nmap package (list files) 
__apt-cache show (package_name)__ == __dpkg -s nmap__  gives utilites about that package (status)

*dpkg -S /usr/bin/perl* (search)
*perl-base: /usr/bin/perl*  shows from where this particular package has come (location ) 

__dpkg -S /usr/bin/perl__ search for which installed package owns a specific file. (search)

**dpkg-query -W -f='${Section} ${binary:package}\n'** it will give me a list of all the section and within each section what are the binary package  

__dpkg-query -W -f='${Section} ${binary:package}\n' | grep shells__ it filter the line that only have the 

## linux operating system 

**sleep 3** making it sleep for 3 second 

__coproc sleep 10__ getting 10 second to type anything in sleep and then session gets over 
__ps --forest__ to see the p ID of the bash shell and now 
__kill -9 754__ that 954 is pid , that is used to kill the process 

__sleep 30 &__ , _&_ to put the process in background , type _fg_ to put it in foregroung and then use ctrl + c to kill it 

__jobs__ to see the backgroung process 
__top__ tell about the process running in cpu ,_q_ or _ctrl+c_ for kill, _ctrl+z_ for suspending the task then _fg_ for getting in foregroung and then kill it 

__bash -c "echo \$-"__ initiating a child shell 

__bash -c "echo \$$; echo \$-; ps --forest"__ first is giving the pid ,second is shell that lacks interatcive thing , and third is forest 

__history__ 
__echo{a..z}__ print all alphabet a to z 
__echo*__ to list all the files in pwd

## error code wala method 
__echo $?__ will give zero if previous code ran without error , but give between 1 to 255 if the prev. code had some error , the number depend on type of error 

__ps -e__ list the all process that is running in the background 

_he instructor is demonstrating that Linux exit codes are limited to a range of 0–255, so any value higher than that is treated as a modulo 256 operation._

__comm -12__: The comm command compares two files line by line.
*-1 suppresses the output of lines unique to the first file.*
*-2 suppresses the output of lines unique to the second file.*
*By using -12, only the third column (lines common to both files) is displayed.* 

**tr**: *A character-translation utility. It operates by mapping individual characters from one set to another rather than performing* *string-level replacements.*

*wc -l < twingle: Redirects the file into wc so that only the number is printed, without the filename.*

*ls -p: Lists all items in the directory. The -p flag appends a forward slash (/) to the end of names that are directories, making them *easy to identify.*
*grep /: Filters the list to only include lines containing a / (which are the directories).* 

__tee -a log__ : default, tee overwrites a file. The -a flag tells tee to append the output to the end of the file

## week -> 4 

__grep 'Raman' names.txt__  *serch for word Raman in names.txt* 
__cat names.txt | grep 'S.a'__ *search for S then one character then a* 
__cat names.txt | grep '.am'__ *a character then am*
__cat names.txt | grep 'am$'__ *that $ means am at last*
__cat names.txt | grep '\.'__ *search for dot as \ is escape character*
__cat names.txt | grep '^M'__ *search for capital M in starting bcoz of ^*
__cat names.txt | grep -i '^e'__ *search for e in starting , -i for case insensitive*  

__sed -i 's/ *$//' names.txt__ _-i: Edits the file in place._
_s/ *$//: Replaces any trailing spaces at the end of the line with nothing._

__cat -e names.txt__ to see trailing space between end of the line and $ 
__cat names.txt | grep 'am\b'__ am at the end of the word 
__cat names.txt | grep 'M[ME]'__ M IN starting than either M or E  
__cat names.txt | grep 'S.*[mn]'__ _S in starting then anything then either m or n in last, it does not matter wheather ther is space in between or not_

__cat names.txt | grep '\bS.*[mn]'__ /b giving one word boundry and then same as upper (no space ) 
__cat names.txt | grep '[aeiou][aeiou]'__ two times vowels continious 
__cat names.txt | grep 'B90[1-5]'__ for all B901... B905
__cat names.txt | grep 'B90[^5-7]'__ GIVING NEGATION(^) 

__cat names.txt | grep 'M\{2\}'__ M should repeat two times 
__cat names.txt | grep 'M\{1,2\}'__ either one or two times 
__cat names.txt | grep  '\(ma\)'__ ma should be matching anywhere 
__cat names.txt | grep  '\(ma\).*/1'__ should match ma then something then again ma --> _Umair Ahmad_ 

__cat names.txt | grep  '\(a.\)\{2\}__ first a then a single character, and it is two times in continus eg: Raman,Anumpama Sridhar,Vel Sankaran

__cat names.txt | grep  'M+'__ it has one m or more than one m 
__cat names.txt | egrep  'M*a'__ word that has ma or a only ( m is optional to be there)

__cat names.txt | egrep  'ma+'__ either one ma or two ma 
__cat names.txt | egrep  'Anu|Raman'__ either Anu or Raman 

## pattern making part-2 

__cat chartypes.txt | grep '[[:alpha:]]'__ lines where there are albhabet 
__cat chartypes.txt | grep '[[:cntrl:]]'__ where there is control like tab or ctrl command 
__cat chartypes.txt | grep -v '[[:cntrl:]]'__ -v means negation here 
see pdf for that , [[:punct:]],[[:lower:]],[[:upper:]],
[[:print:]] printable character 
,[[:blank:]] *only the lines in your file that contain at least one horizontal space or a tab character.*
,[[:graph:]] match any nono space character 

__cat chartypes.txt | grep '^$'__  give empty lines that are in file 


