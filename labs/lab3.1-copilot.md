# Lab 2 - Pair Program with GitHub Copilot!

Speed up your developer productivity with [GitHub Copilot](https://github.com/features/copilot).

Code faster with less work by leveraging GitHub Copilot’s ability to convert comments to code, recognize patterns, and make alternative suggestions.

Let's explore how you can pair program with AI in ourb.NET 7 web app. The best part is..you don’t have to be proficient in GitHub Copilot!

## Exercise 1 - Prompting GitHub Copilot

GitHub Copilot is an extension that can be installed in Visual Studio, Visual Studio Code, Neovim, and JetBrains IDEs. 

Fun fact: GitHub Copilot can provide suggestions for numerous languages and a wide variety of frameworks, but works especially well for Python, JavaScript, TypeScript, Ruby, Go, C# and C++.

Let’s try to prompt GitHub Copilot to suggest some code for us! 

### Installation 
In our last lab while setting up our dev container, we enabled the GitHub Copilot extension to be automagically installed. Let’s double check by searching for GitHub Copilot in our extension list. If not, we can install GitHub Copilot.

## Exercise 1 - Using the codebase’s existing context

We’re going to add a new column for ratings in our web application 

*Let's load the web app in our browser and click the View Inventory button. We will see that it renders the title, author, and cover*
1. Create a new branch by running the command:

```bash
 git checkout -b "learning-copilot"
```

2. cd into the current folder `src/ReadingTime6.Web/Views/Book`.
3. Inside that directory, open the file `Index.cshtml`.
4. In that file on line 27, we’ll write the following comment: 

```csharp
// add a heading for ratings
```

5. Press `ENTER` then `TAB` to accept GitHub Copilot's suggestions:

```csharp
            <th>
                @Html.DisplayNameFor(model => model.Ratings)
```

6. On line 47, we’ll write the following comment: 

```csharp
// add a column for ratings
```

7. Press `ENTER` then `TAB` to accept GitHub Copilot's suggestions:

```csharp
         <td>
            @Html.DisplayFor(modelItem => item.Ratings)
        </td>

```
But it won’t work, just yet! We might even get a few errors because the rating variable isn’t defined in other parts of the project.

8. Let’s define it in our Book model. We can find that in this file `src/ReadingTime6.Web/Models/Book.cs`


9. On line 14 of Book.cs, we’ll write the following comment:
```
// Add a property for ratings
```

10. Press `ENTER` and then `TAB` to accept GitHub Copilot’s suggestion

```csharp
   public int Ratings { get; set; }
```

11. On line 34 of Book.cs, we’ll write the following comment:

```csharp
// add a constructor that takes a title, author, cover, and ratings
```

12. Press `ENTER` and then `TAB` to accept GitHub Copilot’s suggestion

```csharp
        public Book(string title, string author, string cover, int ratings)
        {
            Title = title;
            Author = author;
            Cover = cover;
            Ratings = ratings;
        }

```

13. In BookService.cs, we’ll generate the data that it will pull. On line 9, write the following comment:

```csharp
// Add ratings to each book
```

14. Now to each book instance, add a comma, press space and accept GitHub Copilot’s suggestions. It should suggest a random integer for each rating and generate similar results

```csharp
{
            new Book("Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations", "Nicole Forsgren, PhD", "forsgren.jpg", 5),
            new Book("Scrum: The Art of Doing Twice the Work in Half the Time", "Jeff Sutherland", "scrum.jpg", 4),
            new Book("The Lean Startup: How Constant Innovation Creates Radically Successful Businesses","Eric Ries", "lean.jpg", 4),
            new Book("Crossing the Chasm", "Geoffrey A. Moore", "chasm.jpg", 3),
            new Book("The Pragmatic Programmer: From Journeyman to Master", "David Thomas", "pragmatic.jpg", 5),
            new Book("Don't Make Me Think, Revisited: A Common Sense Approach to Web Usability"," Steve Krug", "think.jpg", 4),
        };

```

15. Now, we can rerun the project and see the results in our browser!

### Exercise 2 - Add Unit Tests

1. In BookTests.cs, add the following comment:

```csharp 
// Add unit test for rating property
```

2. Press `Enter` then `Tab` until it generates the following
```csharp
 [Theory]
        [InlineData(1)]
        [InlineData(2)]
        [InlineData(3)]

        public void ExpectValidBookRatingsModelState(int ratings)
        {
            Book book = new Book("Crossing the Chasm", "Geoffrey A.Moore", "cover.jpg", ratings);
            var context = new ValidationContext(book, null, null);
            var result = new List<ValidationResult>();

            var valid = Validator.TryValidateObject(book, context, result, true);

            Assert.True(valid);

        }

```


