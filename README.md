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
