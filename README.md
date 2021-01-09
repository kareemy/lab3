## Your Name: 


# CIDM 3312 Lab 3: Entity Framework Core 1

The FBI is investigating the West Texas Sanatorium for a myriad of medical and ethical violations. Your task is to keep track of the mad scientists that work there so the FBI can start to build a case.

## Task 0: Preparing the Environment
Open Visual Studio Code, clone the GitHub Lab 3 assignment, and create an Entity Framework Core app. At the terminal type the following:
```
    dotnet new console
    dotnet add package Microsoft.EntityFrameworkCore.Sqlite
    dotnet add package Microsoft.EntityFrameworkCore.Design
```

## Task 1: Create the Data Model
1. Create a folder called `Models`. Within that folder create a file called `DbContext.cs`.
    - This type of file exists in all EF Core applications. It will provide the database context (DbContext). The DbContext is how your code will interact with the database.
2. `DbContext.cs` is an empty file. Fill it in with the proper template code and DbContext class. We will use a SQLite database. Follow the example from the slides. Here is the template code as well:
```
using System;
using Microsoft.EntityFrameworkCore;

namespace lab3 // You may have to change the namespace to match your app namespace in Program.cs
{
    public class AppDbContext : DbContext
    {
        protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
        {
            optionsBuilder.UseSqlite("Data Source=database.db");
        }
    }
}
```

## Task 2: Create the Entity Class
1. Within the `Models` folder, create a file called `MadScientist.cs`. Within that file, create an entity class named `MadScientist` with the following properties:
    ```
        int MadScientistID // This is the "primary key"
        string FirstName
        string LastName
        int Age
        DateTime LastSeen // Date & time this mad scientist was last seen
    ```
    - Remember to use getter/setter syntax when creating these properties.
2. The DbContext needs to know about the MadScientist class to put it in the database. Insert the line of code that will do that into your DbContext class (This is the DbSet<>).

## Task 3: CRUD Operations
1. Add a single mad scientist to the database. Use the new keywortd to create the mad scientist and fill in all the properties. You do not need to fill in the MadScientistID because that is the primary key and gets populated automatically.
    - Look up `DateTime.Parse()` to fill in the `LastSeen` property. You can use:
    `madScientist.LastSeen = DateTime.Parse("1/23/2020");`

How do you access the database? How do you add an object to the database? How do you save the changes? Think about these questions to complete this task.

Open the database in **DB Browser for SQLite**. Click Browse Data. Do you see your mad scientist entry? Run your program again. What happens in the database?

## Task 4: Finishing Up
1. Answer the reflection questions at https://tinyurl.com/CIDM3312-Lab3
2. Save your program and run it. At the terminal prompt, type `dotnet run`
3. Fill in your name in `README.md` and push your changes to GitHub using the VS Code GUI:
    - Click the source control icon in VS Code
    - Type in a commit message
    - Click the checkbox icon to commit. (Click yes on the message box to stage your commit)
    - Click the 3 dots icon (...) for more actions and click Push.
4. Or you can push your changes to GitHub using the Terminal:
    ```
    git add -A
    git commit -m "Your commit message"
    git push
    git status
    ```
5. Visit the URL of your GitHub repository in a web browser and verify that your changes are on GitHub.  
6. Lab is finished. Good work.
