# Film Finder

## Project Summary
You’ve caught up on your list of TV shows and movies and want to get recommendations for what to watch next, but aren’t sure where to look. In this project, you’ll use your knowledge of HTTP requests and asynchronous JavaScript to create a movie discovery app that will recommend random movies by genre. You’ll be able to choose from several genres, and like or dislike a movie to get another suggestion.

Before you begin, you’ll need to create an account on The Movie Database website. After you create your account and verify your email address, click on your user icon at the top right corner and navigate to the Settings page.

On the Settings page, navigate to the API section and click on the link to Request an API Key to register as a Developer.

You’ll be asked to enter some personal information like your address and phone number. This is pretty common. Many APIs use this information to keep track of how their data is being used. As a part of your registration, you will also be asked to provide a URL for the site where you will be using this API. Here, you can list "https://codecademy.com". Check out these instructions if you need further assistance with registering for an API key.

After you finish this project, feel free to challenge yourself to continue building it out. For example, you might recommend TV shows instead of movies, or change the information you present about the recommended movies. The possibilities are endless. Next time you find yourself needing new content recommendations, you’ll know where to turn!

If you get stuck during this project or would like to see an experienced developer work through it, click “Get Unstuck“ to see a project walkthrough video.

## Step 1
Save the API key you obtained from the TMDB API to the tmdbKey variable. We’ll be making multiple calls to the TMDB API and will reference this key in the upcoming steps.

## Step 2
Check the TMDB documentation to find the API’s base URL, and save it to the tmdbBaseUrl variable.

We will append specific endpoints to this URL for each of our requests to the TMDB API.

## Step 3
For the next several steps we’ll be working inside the getGenres() function to fetch a list of genres from the API.

Check the TMDB documentation to find the “Genres” API endpoint. Create a variable called genreRequestEndpoint inside getGenres() and set it to the “Genres” API endpoint.

## Step 4
We will use query parameters to add more specificity to our request. Still inside the getGenres() function, create a variable called requestParams and set it to a query string where the key is api_key and the value is tmdbKey.

## Step 5
Let’s put together the URL where we’ll send our fetch request. Create a variable called urlToFetch and set it to a string that consists of tmdbBaseUrl, followed by genreRequestEndpoint, followed by requestParams.

## Step 6
Turn getGenres() into an asynchronous function that returns a promise. We’ll include our fetch() request in this function, and making it asynchronous will simplify handling the promise our API call returns.

## Step7
We need a straightforward way to catch and handle errors if our fetch() request fails. Underneath our variable declarations inside the getGenres() function, add a try/catch statement. Leave the try block empty for now. In the catch block, log caught errors to the console.

## Step 8
In the try block, use fetch() to send a GET request to urlToFetch. Await the response and save it to a variable called response. We need to await the resolution of our fetch() call so that we can do something with the data we get back.

## Step 9
Still inside the try block, create a conditional statement that checks if the .ok property of the response object evaluates to a truthy value.

## Step 10
Inside the if statement of our try block, we’ll capture the data that we need to populate our dropdown menu. To get the requested data, convert the response object to a JSON object. Await the resolution of this method and save it to a variable called jsonResponse.

## Step 11
To make sure your code is working, log jsonResponse to the console inside our if statement. You should see a single object with a single key, genres. The value of genres is an array that lists TMDB’s genres.

Save the genres property of jsonResponse in a variable called genres. Log this variable to the console to confirm that it contains the correct information.

## Step 12
Return genres as the very last line of the if statement inside our try block of the getGenres() function.

When you run your program, you should now be able to see your dropdown menu populated with genres!

## Step 13
For the next several steps we’ll be working inside getMovies() to fetch a list of movies based on the genre selected from the list of genres we returned in getGenres().

Check the TMDB documentation to find the “Movie Discover” API endpoint. Below the selectedGenre variable declaration, save this endpoint to a variable called discoverMovieEndpoint.

## Step 14
Like we did for getGenres(), we’ll create a variable called requestParams. Set it equal to a query string with two parameters. The first will be our api_key with the value, tmdbKey. The second parameter will have the with_genres key with its value set to the selectedGenre variable.

selectedGenre stores the returned value from a helper function (the getSelectedGenre() function in helpers.js) that captures the user’s selected genre.

Let’s also put together the URL where we’ll send our fetch request. Create a variable called urlToFetch. Set it to a string that consists of tmdbBaseUrl, followed by discoverMovieEndpoint, then requestParams.

## Step 15
Turn getMovies() into an asynchronous function that returns a promise. This will simplify handling the promise that our fetch() request will return.

Add try/catch blocks inside getMovies(), after our variable declarations.

In the catch block, log any errors to the console. In the try block, use fetch() to send a GET request to urlToFetch. Await the response and save it to a variable called response.

## Step 16
Still inside the try block, create an if statement that checks if the .ok property of the response object evaluates to a truthy value.

Inside the if statement, convert the response to a JSON object. Await the resolution of this method, and save it to a variable called jsonResponse.

Log the jsonResponse object to the console. To see your output in the console, you will need to call getMovies() after the function declaration. In the console, you’ll see a key called results that holds an array of all the movies in the first page of results.

## Step 17
Below our jsonResponse variable declaration in the if statement, store the results property of jsonResponse in a variable called movies. Log this variable to the console to confirm that it contains the correct information.

Return movies as the last line of the if statement. Later on, we’ll use this list to select a random movie as a suggestion.

After you check what movies logs to the console, remove the getMovies() function call. Otherwise, it will automatically execute every time you run your program, causing unexpected behavior later.

## Step 18
For the next several steps, we’ll be working inside the getMovieInfo() function to fetch the details of a random movie from the list of movies we returned in getMovies().

Modify getMovieInfo() by having it accept a parameter, movie. Then, inside the function, create a variable called movieId that is set to the id property of the movie parameter. We will be using the id property to make another call to the TMDB API.

## Step 19
Reference the TMDB documentation to find the movie “Details” endpoint. Save it to a variable called movieEndpoint and replace {movie_id} in the endpoint with our movieId variable.

## Step 20
Let’s create our query params and the URL where we’ll send our fetch() request. Create a variable called requestParams and set it to be a query string with one parameter with api_key set to tmdbKey.

Create a variable called urlToFetch. Set it equal to a string that consists of tmdbBaseUrl, followed by movieEndpoint, then requestParams.

## Step 21
Turn getMovieInfo() into an asynchronous function that returns a promise. Add a try/catch block inside getMovieInfo(), after our variable declarations.

In the catch block, log any errors to the console. In the try block, use fetch() to send a GET request to urlToFetch. Await the response and save it to a variable called response.

## Step 22
Still inside the try block, create an if statement that checks if the .ok property of the response object evaluates to a truthy value.

Our response contains a single object with details about the given movie. Inside the if statement, convert this response to a JSON object. Await the resolution of this method, and save it to a variable called movieInfo.

## Step 23
Return movieInfo as the last line of the if block.

## Step 24
For this next set of tasks, we’ll be working inside the showRandomMovie() function to piece together our functionality and render a random movie’s info to the page.

Turn showRandomMovie() into an asynchronous function. Then, on the last line of the function, call getMovies(), await its return, and save it to a variable called movies. Since getMovies() returns a promise, we need to await its resolution so that we can do something with its return value in upcoming steps.

## Step 25
Below our movies declaration, call getRandomMovie(), passing movies as the argument. Store the returned value in a variable called randomMovie.

## Step 26
Below our randomMovie declaration, call getMovieInfo(), passing randomMovie as the argument. Await its return and save it to a variable called info.

## Step 27
Finally, as the last line of the showRandomMovie() function, call displayMovie(), passing info as the argument.

Run your program to see movie suggestions. Like or dislike each movie to be shown another random suggestion. Change genres to get different suggestions based on your interests.

Congratulations! You’ve finished building the Film Finder project!