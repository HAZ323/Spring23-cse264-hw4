##CSE 264 – Web Systems Programming – Spring 2023
##Homework Assignment 4 - Top 40 Song Search
##Due Thursday, March 2nd, 11:59pm

###Objective
To gain more experience using Node.js and Express on the server, to gain experience using Ajax, and to gain experience using a functional style of programming.

###Description
You will create a simple app that allows a user to search a list of Top 40 songs and display the results.

##How the app works
Refer to the file Top40_Search.pdf. The app presents a user with a form containing fields for 

###Instructions

0. Any instruction that says "use xxx to ......" means you must use technique xxx to accomplish the task.

1. Use npm init to create a package.json file.

2. Use npm to install the express, path, and fs modules. (I found out that in recent versions of npm, the --save option is the default so each module will be added as a dependency in package.json)

####Server Script

3. Edit app.js and create a class Song with a constructor that creates three fields: title, artist, and numone.

4. Do an initial git add, commit, and push.

5. Use fs.readFileSync to read the file top40.csv into a variable.

6. Split the string containing the contents of the file into an array of individual lines by calling the js split method on "\r\n". NB: top40.csv must be used exactly as provided; no editing of the file may be done.

7. Use the js map method to map the array of lines into an array of Song objects using the Song class. Store 
the array in the variable songs.
  7a. Call the split method on a line to separate the comma separated fields into elements of a string array. Strip off any surrounding ' characters from the fields.
  7b. Use the new operator to create a song object using the 2nd array element as the artist and the 3rd element as the song name. If the 4th field is 0 then use false for the numone field and if it is 1 then use true.

8. Write a few of the song objects to the console to make sure the code is working. (Feel free to remove this code once your app is complete.)

9. Create a "get" router on the path "/search" that does the following:
  10a. Retrieve the title and artist query string values and convert them to lower case.
  10b. Use the js filter method on the songs array from step 7 to create a new array with only the songs where the artist field (converted to lower case) contains the artist keyword or the title field (converted to lower case) contains the title keyword. If the artist or title keywords are empty strings then ignore that part of the test.
  10c. Use JSON.stringify to convert the filtered array of songs to a string and then send that string to the client.

10. Do another git add, commit, push.

####Client html, css and js

11. Edit the provided index.html file and create a form with a title keyword and artist keyword field. Use fieldset and legend elements to surround the form. Use label and input type=text elements to define the fields. Create a button (of type=button) labeled Search. Put a heading at the top of the page.

12. Below the form create a skeletin table with an Artist column and a Title column. 

13. Put any necessary css styles in the styles.css file. No css may appear in the html file.

14. Put all the js described below in the script.js file. No js may appear in the html file.

15. Use jQuery to create an event handler for the click event on the Search button that does the following:
  15a. Use jQuery to retrieve the title and artist keywords from the text boxes.
  15b. Use jQuery to make a "get" Ajax call to the "/search" path on the server. Pass the title and artist keyword strings by setting the processData: and data: fields appropriately. 
  15c. In the success: function, empty out the results table, use the forEach method on the array of songs returned from the server to create each row in the table and use jquery to append each row to the table. If a song has numone set to true then make the background color of the row gold. (Hint: If you have a DOM element (like a table row) wrapped in a jQuery object, you can call the addClass method to add a class to that element). 
  
(NB: Use the Example I reviewed during Wednesday's class as a guideline.)

16. Test your app by running node app.js and typing localhost:3000 in the browser address bar. Try various combinations of artist and title keywords (including leaving one or both empty) and checking the results.

17. Make sure you have a comment with your name, etc. in each file.

18. No ejs templates or form submission may be used on the project.

18. Do your final git add, commit, push.

###Rubric
- Reasonably clean html page. (5 pts)
- Comments in each file (3 pts)
- Working code - the correct songs (number one songs in gold background) are displayed for given keywords. (40 pts)
- Correct use of the map, filter and forEach methods. (30 pts)
- Correct use of the $.ajax call. (20 pts)
- Required commits. (2 pts)

###Extra Credit
- In order to prevent the csv file comma problem discussed in class from occuring, I changed all the embedded commas to semicolons. Convert all the semicolons to commas and the asterisks to apostrophes as you read in the csv file. (5 pts)
- Convert all the artists and titles to initial capitals except for "little words" (a an the of). Example: 'Jennifer Warnes','Right Time of the Night'. (5pts)
- Add 2 radio buttons to the form labeled And & Or. If And is selected then select a song only where both the title and artist keywords match. If Or is selected, then select a song if either matches (this is the default behavior).



     


