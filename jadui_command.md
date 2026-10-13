In Linux shell scripting (specifically in Bash, Zsh, and KornShell), [[ ]] is an extended test command used to evaluate conditional expressions! 🧪✨ Think of it as an upgraded, supercharged version of the classic single bracket [ ] test command.

When you write [[ condition ]] inside a script or command line, the shell evaluates whatever is inside and returns a status code:

0 = TRUE ✅

1 = FALSE ❌
--------------------------------
*When creating a symlink inside a subfolder, you have to write the target path from the link's point of view*
*Symlinks don't remember where you were sitting when you created them.*
*They resolve relative to where the link file itself lives (Workspace/links/)*


links/... means "the links folder right here inside Workspace/".
/links/... means "the links folder at the root level of the entire computer system" (the same level as system files like /bin, /usr, /etc).

Prepending bash ./run.sh forces the Bash interpreter to read and execute the file directly, bypassing the need for chmod +x execute permissions entirely! 🧱

In Bash case statements, operators at the end of a clause control the execution flow:

;; — Normal termination; exits the case block.

;& — Unconditional fall-through; executes the next clause's command list without testing its pattern.

;;& — Resume testing; tests the next pattern in the list against $val and executes its commands if it matches.