Bookmark Documentation
The code below is a simple JavaScript application for managing bookmarks in a web browser. The application saves and retrieves the bookmarks from the local storage.

HTML structure
The HTML document has a <div> container with the id of "bookmarks" which holds the UI of the application.

Inside the container, there are several elements:

A heading "Bookmarks"
An empty <div> with the id of "bookmark-list" which will be used to display the bookmarks.
Two buttons "Add" and "Toggle"
A form for adding bookmarks, with the id "add-bookmark-form", that is initially hidden and contains:
Two text inputs, one for the title and one for the URL of the bookmark, with the ids "title" and "url" respectively.
A checkbox to indicate if the bookmark has a parameter, with the id "param".
A submit button "OK" with the id "add-bookmark-submit".
JavaScript Code
The JavaScript code initializes an array bookmarks by parsing the data stored in the local storage under the key "bookmarks" or an empty array if it does not exist.

It then sets references to various elements in the HTML, such as the bookmark list, form, and buttons, using document.querySelector().

A filter input field is created and added to the UI for filtering the bookmarks by title. The event listener for the input field updates the display of the bookmarks based on the filter value.

The function displayBookmarks() sorts the bookmarks by the timestamp and displays them in the "bookmarklist" <div> with the following structure:

A heading for the title of the bookmark
A paragraph for the URL of the bookmark
A button for editing the bookmark with the id "edit-bookmark-{timestamp}" where {timestamp} is the unique identifier for the bookmark.
A button for removing the bookmark with the id "remove-bookmark-{timestamp}" where {timestamp} is the unique identifier for the bookmark.
The form for adding bookmarks is controlled by the following functions:

showForm(): Shows the form by setting the display style to "block".
hideForm(): Hides the form by setting the display style to "none".
addBookmark(): Adds a new bookmark to the bookmarks array and local storage, and updates the display. The function retrieves the values of the title, URL, and parameter inputs and constructs a new bookmark object with a unique timestamp and the retrieved values. The function then pushes the new object to the bookmarks array and sets the updated array to the local storage.
handleFormSubmit(event): Prevents the default form submission behavior and calls the addBookmark() function.
The toggle button switches between displaying all bookmarks and displaying only bookmarks with parameters. The function displayBookmarks() takes into account this toggle value when displaying the bookmarks.

The editing and removing of bookmarks is done through event delegation. An event listener is set on the "bookmark-list" <div> to listen for click events on the edit and remove buttons. When a button is clicked, the event listener retrieves the corresponding bookmark object from the bookmarks array based on the timestamp and either opens the form with the retrieved values for editing or removes the bookmark from the bookmarks array and local storage and updates the display.
