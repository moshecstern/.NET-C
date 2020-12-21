# .NET-C
Learning .NET with C#

## If you want a detailed list of all commands, enter " dotnet --help " in the terminal.

You can install some packages globally. These packages are not meant to be imported into your project. For that reason, many global packages are CLI tools or templates. You can also install these global tools from a package repository. Install tools by using the " dotnet tool install <name of package> " command. Install templates by using the " dotnet new -i <name of package> " command.

## How to install a package
You use the dotnet add package <dependency name> command to install a normal dependency that's meant to be used as part of your application.

## Restore dependencies
When you create or clone a project, the included dependencies are not downloaded or installed until you build your project. You can manually restore dependencies as well as project-specific tools that are specified in the project file by running the dotnet restore command. In most cases, you don't need to explicitly use the command. NuGet restore is run implicitly, if necessary, when you run commands like new, build, and run.

## Clean up dependencies
Sooner or later, you're likely to realize that you no longer need a package. Or you might realize that the package you installed isn't the one you need. Maybe you've found one that will accomplish a task better. Whatever the reason, you should remove dependencies that you aren't using. Doing so keeps things clean. Also, dependencies take up space.

### To remove a package from your project, you use the remove command like so: dotnet remove <name of dependency>. This command will remove the package from the .csproj file for your project.

### dotnet list package --outdated : To find all outdated packages

### dotnet add package <package name>  : TO update it


up to https://docs.microsoft.com/en-us/learn/modules/dotnet-debug/4-use-visual-studio-code-debugger


## Debugging

Up to this point, we've been using the console to display information to the application user. There are other types of applications that are built with .NET that have user interfaces, such as mobile, web, and desktop apps, and there's no visible console. In these applications, System.Console is used to log messages "behind the scenes." These messages might show up in an output window in Visual Studio or Visual Studio Code. They also might be output to a system log such as Android's logcat. As a result, you should take great consideration when you use System.Console.WriteLine in a non-console application.

This is where System.Diagnostics.Debug and System.Diagnostics.Trace can be used in addition to System.Console. Both Debug and Trace are part of System.Diagnostics and will only write to logs when an appropriate listener is attached.

The choice of which print style API to use is up to you. The key differences are:

System.Console
Always enabled and always writes to the console.
Useful for information that your customer might need to see in the release.
Because it's the simplest approach, it's often used for ad-hoc temporary debugging. This debug code is often never checked in to source control.
System.Diagnostics.Trace
Only enabled when TRACE is defined.
Writes to attached Listeners, by default, the DefaultTraceListener.
Use this API when you create logs that will be enabled in most builds.
System.Diagnostics.Debug
Only enabled when DEBUG is defined (when in debug mode).
Writes to an attached debugger.
Use this API when you create logs that will be enabled only in debug builds.

#### Console.WriteLine("This message is readable by the end user.")
#### Trace.WriteLine("This is a trace message when tracing the app.");
#### Debug.WriteLine("This is a debug message just for developers.");


## Path specification 

#### Console.WriteLine(Path.Combine("stores","201")); // outputs: stores/201

#### OR Console.WriteLine($"stores{Path.DirectorySeparatorChar}201");

// returns:
// stores\201 on Windows
//
// stores/201 on macOS

### Determining file na,e extensions

Console.WriteLine(Path.GetExtension("sales.json")); // outputs: .json

## summary 
string fileName = $"stores{Path.DirectorySeparatorChar}201{Path.DirectorySeparatorChar}sales{Path.DirectorySeparatorChar}sales.json";

FileInfo info = new FileInfo(fileName);

Console.WriteLine($"Full Name: {info.FullName}{Environment.NewLine}Directory: {info.Directory}{Environment.NewLine}Extension: {info.Extension}{Environment.NewLine}Create Date: {info.CreationTime}"); // And many more



Create directories
You use the Directory.CreateDirectory method to create directories. The following method creates a new folder called newDir inside the 201 folder.

C#

Copy
Directory.CreateDirectory(Path.Combine(Directory.GetCurrentDirectory(), "stores","201","newDir"));
If /stores/201 doesn't already exist, it will be created automatically. The CreateDirectory method won't fail. It will create any directories and subdirectories passed to it.

Make sure directories exist
Sometimes you'll need to check if a directory already exists. For example, you might need to check before you create a file in a specified directory to avoid an exception that could cause your program to stop abruptly.

To see if a directory exists, you use the Directory.Exists method.

C#

Copy
bool doesDirectoryExists = Directory.Exists(filePath);
Create files
You can create files by using the File.WriteAllText method. This method takes in a path to the file and the data you want to write to the file. If the file already exists, it will be overwritten.

For instance, this code creates a file called greeting.txt with the text "Hello World!" inside.

C#

Copy
File.WriteAllText(Path.Combine(Directory.GetCurrentDirectory(), "greeting.txt"), "Hello World!");
In the next exercise, you'll use your knowledge of how to create files and directories to extend the program to create a directory that will store the total of all sales files.