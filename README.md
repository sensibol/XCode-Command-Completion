# XCode-Command-Completion
Notes on what to do if command completion not working in XCode

Sometimes XCode command completion stops working for no obvious reasons. Following steps can help resolve the issue.

Command completion and other syntax highlighting depend on SourceKit tool. If command completion stops working the obvious place to investigate is Source Kit.

Below are the steps in order

1) Clean Cached Data
---------------------------
Clean the Project -> Cmd+Shift+K
Clean the Build Folder -> Cmd+Shift+Option+K

Delete Derived Data
Xcode Preferences -> Locations -> Arrow Symbol Takes you to DerrivedData -> Delete Folder


2) Advanced
---------------------------

Debug sourcekit. To do so enable logging of source kit. http://www.jpsim.com/uncovering-sourcekit/

export SOURCEKIT_LOGGING=3 && /Applications/Xcode.app/Contents/MacOS/Xcode 

In our case the error was " SourceKit-client: [2:response:121375:838.7050] [3537] error response (Request Failed): error when parsing the compiler arguments"
The commandline arguments that SourceKit was not linking were
"-Xfrontend",
"-debug-time-function-bodies",
"-driver-show-incremental",
