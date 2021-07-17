# Installation & Setup

## Installing Git: Terminal vs. GUIs

Git is (primarily) a Terminal tool<br />
Git was created as command-line tool. To use it, we run various git commands in a Unix shell. This is not the most user friendly experience, but it's at the very core of Git!<br />
The Rise of GUI's<br />
Over the last few years, companies have created graphical user interfaces for Git that allow people to use Git without having to be a command-line expert. Popular Git <a href="https://git-scm.com/downloads/guis">GUI's</a> include:<br />

<ul>   
    <li>Github Desktop</li>
    <li>SourceTree</li>
    <li>Tower</li>
    <li>GitKraken</li>
    <li>Ungit</li>
</ul>

## GUI Clients

<strong>Pros</strong><br/>

<ul>
    <li>Way lower barrier-of-entry for beginners compared to the command-line.</li>
    <li>Friendlier to use. Can be a much better experience (when it works).</li>
    <li>Some people prefer the visual experience, even those who can use the command-line.</li>
</ul>
<strong>Cons</strong><br />
<ul>
    <li>At times, there is lots of "magic" involved. The inner-workings of Git are obfuscated and hidden away with GUI's.</li> 
    <li>Often leads to dependance on a particular piece of software.</li>
    <li>When things go seriously wrong, it can be very challenging to fix without the command-line.</li>
    <li>The interfaces, buttons, and menus vary between GUI's.</li>
</ul>

## The Command Line

<strong>Pros</strong><br/>

<ul>
    <li>Git is a command-line tool. All the documentation and resources online will refer to the command-line.</li>
    <li>The command-line can be way faster once you get comfortable with it!</li>
    <li>Some of the more advanced Git features are only available on the command-line.</li>
    <li>The commands are always the same, no matter what machine you are on!</li>
</ul>
<strong>Cons</strong><br />
<ul>
    <li>Not beginner-friendly. At all. Can be difficult to learn and remember the commands at first.</li>
    <li>Even for some practiced users, the command-line interface is just not a good experience. It's really a matter of preference.</li>
</ul>

## WINDOWS/MAC Git Installation

Git Bash emulates the unix-based Git command-line experience for Windows machines, and it's super easy to install! Why git Bash?<br />
Bash is a command line interface that is widely used by developers. It is the default shell for Linux and Mac. Git was designed to run on a Unix-based interface (like Bash). Windows comes with a different default command line interface called Command Prompt that is not Unix-based. Fortunately, we have Git Bash! Git Bash is a tool that emulates a Bash experience on a Windows machine. And of course it comes with Git too.

## Configuring Your Git Name & Email

Now that Git is hopefully installed, it's time to configure some basic information. You do not need to register for an account or anything, but you will need to provide:

<ul>
    <li>Your name</li>
    <li>Your email</li>
</ul>
If you are using a GUI, it should prompt you for your name and email the first time you open the app.<br />
To configure the name that GIt will associate with your work, run this command:<br />

```
git config --global user.name "Tom Hulce"
git config user.name
```

Do the same thing for your email using the following command. When we get to GitHub, you will want your Git email address to match your GitHub account.

```
git config --global user.email blah@blah.com
```

## Terminal Crash Course: Navigation, Creating, Deleting Files and Folders

List the contents and open folder of your current directory

```
ls
ls -a
open .
```

Print Working Directory to show you the exact file/folder location

```
pwd
```

Change Directory

```
cd <directory>
```

Change Directory (move back one folder)

```
cd ..
```

Create a new file (or files)

```
touch <file_name_1.py> <file_name_2.pdf> <file_name_3.txt>
```

Make a new folder (or folders)

```
mkdir <folder_1> <folder_2>
```

Delete a file (make sure you're in the right folder directory)<br />
Reminder: This permanently deletes a file<br />

```
rm <file_name>
```

Delete a folder
Reminder: This permanently deletes a file<br />

```
rm -rf <folder_name>
```
