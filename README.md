# InjugBuggyCRUD ft. Erika G.
My Debugged version of BuggyCRUD activity from Mr. Jules' Lab assignment

# ***Привет!*** 👋 Welcome to my Revised and debugged version of BuggyCRUD

Below are the notes, obstacles, and solutions I made to make the program work

# ⚠️⚠️Trigger Warning!! EXTREME YAPPING
You have been appropriately warned


## Git Issues
I have some git problems I have encountered (Since this is my first tiem cloning a repo tbh, so I kind of had some problem run-ins at the beginning)

### Cloning
Cloning wasn't directly the issue, the issue arose when I tried:

```bash
git init
git add .
```

Errors went haywire when I did that, I suspected it was because of the file location, or improper remote setup since I was cloning, and I was partially right

### Cloning solutions (and localization)

So firstly I cloned the repo right? And then I removed the subfolder .git file using `rm --rf .git` successfully removing git history in my local folder, and removing its connectivity with the original owner's git connection

then I ran these commands in the following in order:
```bash
git init
git add .
git commit -m "Initial commit blah3"
git remote add origin https://github.com/your-username/InjugBuggyCRUD.git
```
I successfully connected, but there were still Issues, particularly with the fact that I have a README.md in my newly made github repo, and that I had to do a pull first, but it wasn't that simple, since the error is pointing out that `There is a particular problem with the two repositories' version history` or something haha. So ofc I went and searched for another solution. And I arrived at this one:

```bash
git pull origin main --allow-unrelated-histories
```

This opened a vim editor terminal (or so I think it looks like haha, pls don't attack me askhjdakjhsdfhbsdf), and I didn't change any of the contents, I just executed `:wq` and pressed `Enter` then voila, it bypassed the pull conflict thingy ✨✨✨

Goodness, with all that away, Let us proceed with the **ACTUAL** activity, sheesh

# Creating new database for BuggyCRUD

While I was looking around the file, I fortunately found the README conmtaining instructions and clues. You thought you were slick weren't you sir? Hehe just kidding, I know most students fall into the mistake of not exploring the project file and missing out on the contents of the README, I mean, I almost fell into that mistake lmfao

### Database Creation
As per instruction, the Database Name should be appropriately the same as the `appsettings.json` database, which was *drum roll* 🥁🥁 `BuggyStudentCRUDDb` yeyy! 🎊🎊

### Table creation
Just the standard procedure, I also took the details for these in the Model folder, since iT repReSentS tHe DatAbAse DaTa In OuR CodE or something lmao

It contains the ff:
- Id (PK)            | int
- FirstName          | nvarchar(50)
- LastName           | nvarchar(50)
- Email              | nvarchar(50)   *I just assumed this*
- Course             | nvarchar(100)
- YearLevel          | int
- GPA                | decimal(2,1)   *I just assumed this*
- EnrollmentDate     | datetime
- FullName           | nvarchar(100)  *I just assumed this*

- Table Name         | Student        *Assummed according to the Model.cs Name*


# Actuall Debugging Phase 💨💨🪳

## List Summary of Known and Fixed bugs
| # | Location                | Bug                       | Solution                                                         |
|---|-------------------------|---------------------------|------------------------------------------------------------------|
| 1 | GET: Students           | Searchbar                 | Changes: from && condition to \|\|                               |
| 2 | GET: Students/Details/5 | Getting Student Details   | Changes: change != to == on (m.Id == id)                         |
| 3 | POST: Students/Create   | Validation Issue          | Changes: Remove ! from !ModelState                               |
| 4 | POST: Students/Edit/5   | Does not update           | Changes: Changed .Add() to .Update()                             |
| 5 | POST: Students/Delete/5 | No delete content         | Changes: Add _context.Students.Remove(student);                  |
| 6 | Edit.cshtml             | Wrong max num accepted    | Changes: From 4.0 max to 5.0 max                                 |
| 7 | Details.cshtml          | Wrong Display of FName    | Changes: DisplayFor model.FirstName from LastName (Interchanged) | 
| 8 | Details.cshtml	        | Wrong Display of LName    | Changes: DisplayFor model.LastName from FirstName (Interchanged) | 
| 9 | Student.cs              | Sorting of names is wrong | Changes: Sorting Issue fix, interchanged LastName and FirstName  |

