<img src="https://i.imgur.com/sX12DTc.png">

# Unit 3 Assessment

## Introduction 

Students are to have their laptops closed until directed to open them.

Students will be self-directed beginning with the **Instructions & Time Guidelines** section below.

### GOAL

The goal of this project assessment is to gauge your ability to develop a minimal full-stack web application using the Django framework, including your ability to:

- Create and configure a Django project.
- Create a "main_app" app within the Django project.
- Create a `urls.py` for the "main_app" app and include it within the project's `urls.py`.
- Define a Model.
- Make and run migrations.
- Define views that perform basic CRUD and redirect or render templates.
- Code a template that displays a list of data.
- Code a template that displays a form for entering data.

### DEMO

The instructor will now demonstrate the app you will be building.

### OVERALL APPLICATION REQUIREMENTS

As you saw, the application consist of:

- A template with a title of "Wish List", that displays all wish items in the database and provides a "link" to view a form within another template to add a new wish item.

- When browsing to the root route of the application (`http://localhost:8000`), the "Wish List" page is displayed - not the Django welcome page.

- The wish items were displayed in a `<table>`.

- Each wish item's `<tr>` had three `<td>`s to display:
	- The `description` field
	- The `quantity` field
	- A "X" link used to delete a wish item

- **NOTE: The delete functionality is OPTIONAL**

- After a wish item is added or deleted, the app redirects back to the "Wish Items" page (the root route).

- Note for optional Delete functionality: When a wish item is deleted, it is not a requirement to confirm the delete - this is optional. It will probably come down to whether you use a simple View Function or a DeleteView to implement the deletion.

- If there are no wish items in the database, show a message "No Wish Items Exist" instead of the table of widgets.

Use the screenshots below as your "wireframes".

There are a few "hints" offered along the way.

The layout and styling of this assessment is secondary to its functionality. As long as the app behaves as required and displays all elements specified, you will pass.

There is a link to a minimalistic CSS framework (Pure.css) which defines several classes. Each step includes custom CSS and what classes to use from the framework - feel free to use them.

### PROCESS

This assessment is an **individual** assignment - no collaboration please.

It's "open book" - you may reference anything on your computer, Google, use notes, etc. 

It is anticipated that it will take approximately **60 - 90 minutes** to complete this assessment, however, if necessary, you have up to 3 hours to finish.

When finished you will demo your app to an instructor and slack them the link to your personal GitHub repo.

The app will not be deployed, just pushed to your Git Hub.

## Instructions & Estimated Time Guidelines (You've Got This!)

Please follow the following steps in order:

- **STEP 1 - Prepare** (&asymp; 5 minutes)
- **STEP 2 - Set Up the App** (&asymp; 10 minutes)
- **STEP 3 - Implement the App's Requirements** (&asymp; 75 minutes)
- **STEP 4 - Demo & Slack Link to Your Instructor**

> The above times are just guidelines

## Assessment Steps to Complete

### STEP 1 - Prepare (&asymp; 5 minutes)

Briefly read through the rest of this assignment to better understand what is required before starting to code.

### STEP 2 - Set Up the App (&asymp; 10 minutes)

Follow the standard workflow for creating a new Django project.

You can start the project by running this command:

```
$ django-admin startproject wishitems
```

You will have to slack your instructors a link to your personal GitHub repo so be sure to `git init` in the root of your project folder, create your repo on GitHub (without a README), and follow the instructions to add the remote.

You will not have to deploy this app, so do not waste time switching to use PostgreSQL, the default SQLite database is fine.

However, you will still have to create & migrate migrations.

The app does not use the built-in User model or authentication.

This app will require only one Model.

The app will require more than one template, however, the decision to use and extend a _base.html_ template is left up to you.

The demo application was built using the [Pure.css](https://purecss.io/) CSS library. You can add the following to your template's `<head>` to play along:

```html
<link rel="stylesheet" href="https://unpkg.com/purecss@1.0.0/build/pure-min.css" integrity="sha384-nn4HPE8lTHyVtfCBi5yW9d20FjT8BJwUXyWZT9InLYax14RDjBj46LmSztkmNP9w" crossorigin="anonymous">
```

The inclusion of _Pure.css_ will make HTML tables, buttons and Django's forms, look better simply by adding some classes - which are provided in each step below.

However, feel free to add your own stylesheet to perform custom styling such as adding margin, centering, etc. Some basic CSS is also provided to you.

### STEP 3 - Implement the App's Requirements (&asymp; 75 minutes)

#### Planning

Before you start coding, think about what Django technique you are going to use to implement the app's functionality. Are you going to use your own **view functions**? Or are you planning on using class-based views that inherit from the `ListView`, `CreateView`, etc.? The choice is yours, so you should use whatever you are most comfortable with.

#### STEP 3.1 - Root Route

Browsing to the root route of the application should **not** display the Django welcome page:

<img src="https://i.imgur.com/sTE406T.png"> 

Instead, the root route should display your app's single template, i.e., _index.html_, with a title of "Wish List Items":

<img src="https://i.imgur.com/dpfP1h5.png">

The "Wish List Items" page title is an `<h1>` element.

The following custom CSS has been added:

```css
body {
    text-align: center;
    margin: 2rem;
}
```

#### STEP 3.2 - No Wish Items in the Database

After this step is completed, your app should look something like this:

<img src="https://i.imgur.com/QT3JjC5.png">

When there are no wish items in the database, a "No Wish Items Exist" message should be displayed.

The `Item` Model only has one field:

- `description` -  a `TextField` with a `max_length` of your choosing

The "No Wish Items Exist" is an `<h3>` followed by an `<hr>`.

##### Hint

You can use the `for`/ `empty` template tags to render different things depending upon whether there's data or not like this:

```html
{% for item in item_list %}

{% empty %}

{% endfor %}
```

Note: IF using an `IndexView`, a variable named `item_list` that holds the list of items in the database will automatically be passed to the template.

#### STEP 3.3 - Adding Items

After adding a link that goes to the page for adding a new item, the display should look something like this:

<img src="https://i.imgur.com/fimRYba.png">

The "Add Wish Item" is an `<a>` element below the `<hr>` styled to look like a button by adding a class of `pure-button`.

Clicking **Add Wish Item** will show a "Add Wish Item" page that looks like:

<img src="https://i.imgur.com/IzCmlOj.png"> 

##### Hints

- A `CreateView` is an excellent way to implement the Add Wish Item functionality.

##### Styling

The `form` has a class of `pure-form` added to it.

The `button` in the `form` has a class of `pure-button` added to it.

#### STEP 3.4

When there are items in the database, the display should look something like this:

<img src="https://i.imgur.com/pLMcQf3.png">

The `table` has a `<thead>` with a header row (`<tr>`) that has two header cells (`<th>`): **Description** & **Delete**.

Each wish item is being displayed as a `<tr>` with two `<td>` elements.

The red "X" is an `<a>` element that, when clicked, delete's that wish item from the database. For example, no more Pink Socks:

<img src="https://i.imgur.com/osiI38H.png">

> Note: Although implementing the delete function is optional, you should render the "Delete" column in the table and the red "X" `<a>` element for each item.

##### Styling

The `table` has classes of `pure-table` and `pure-table-striped` added to it.

The following custom CSS centers the table and styles the "X" link:

```css
table {
    margin: 2rem auto;
}

table a {
    color: red;
    text-decoration: none;
}
```

**Congrats, you're done!**

### STEP 4 - Demo & Slack Link to Your Instructor

**Take your computer and demo the app's functionality to your instructor.**

Do a final commit and push to your GitHub.

**Slack your  app's link to your instructors**




