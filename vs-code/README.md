# VS Code

Download and Install  VS Code. (This is different from Visual Studio)

{% embed url="https://code.visualstudio.com/" %}

### Windows Users

Create a new folder on your c:\\

Let's call it

**c:\learning\rustpgm** &#x20;

**Open VS Code**

Goto File > Add Folder to Workspace

Choose  c:\learning\rustpgm and click Add

Click Trust / Ok if it prompts.

Goto File > Save Workspace and save the workspace as **rustpgm.code-workspace**



Right-click on rustpgm and choose New File

Name the file as 01.rs

Copy the sample rust code

```
// Sample Code

fn main(){
    println!("Hello World");
}

```

Save the Script (press Ctrl + S  or File > Save)

**Click New Terminal**

Make sure you are in this folder  c:\learning\rustpgm

type

**rustc 01.rs**

once compilation is done.

Verify  the result by listing the file contents

**dir**

Execute the program by typing the following

**./01.exe**



**Mac Users**

Create a new folder on your Documents folder

Let's call it

**/Documents/learning/rustpgm** &#x20;

**Open VS Code**

Goto File > Add Folder to Workspace

Choose  /Documents/learning/rustpgm and click Add

Click Trust / Ok if it prompts.

Goto File > Save Workspace and save the workspace as **rustpgm.code-workspace**



Right-click on rustpgm and choose New File

Name the file as 01.rs

Copy the sample rust code

```

fn main(){
    println!("Hello World");
}

```

Save the Script (press Ctrl + S  or File > Save)

**Click New Terminal**

Make sure you are in this folder  Documents/learning/rustpgm

type

**rustc 01.rs**

once compilation is done.

Verify  the result by listing the file contents

ls

Execute the program by typing the following

**./01**



