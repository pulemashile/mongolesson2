# mongolesson2
 **Library Management System** project

---

# Library Management System

## Overview

The **Library Management System** is a MongoDB-based application designed to manage books, authors, and patrons of a library. The system allows users to add, update, delete, and search for books, authors, and patrons. It also supports checking out and returning books, as well as querying specific data using MongoDB queries.

## Features

- Manage books, authors, and patrons in separate collections.
- Perform CRUD operations (Create, Read, Update, Delete) on books, authors, and patrons.
- Search for books by title, author, genres, availability, and publication year.
- Track patrons' borrowed books.
- Advanced querying support, such as finding books published after a specific year, retrieving books by a specific author, and more.

## Database Structure

The system consists of three main collections:

1. **Books**: Contains information about each book, such as title, author, genres, publication year, and availability status.
   - Fields: `_id`, `title`, `author_id`, `genres`, `published_year`, `available`
  
2. **Authors**: Contains information about authors, including their name, nationality, birth year, and death year.
   - Fields: `_id`, `name`, `nationality`, `birth_year`, `death_year`
  
3. **Patrons**: Contains information about library patrons, including their name, email, and the books they have borrowed.
   - Fields: `_id`, `name`, `email`, `borrowed_books` (Array of book IDs)

---

## Setup Instructions

### Prerequisites

To run this project, you need the following:

- **MongoDB** installed on your local machine or a MongoDB cloud database.
- A MongoDB client such as **MongoDB Compass** or use the Mongo shell.

### Steps to Set Up

1. **Clone the repository (or download the scripts)**

   Clone this repository to your local machine using Git or download the project files directly.

   ```bash
   git clone https://github.com/your-username/library-management-system.git
   ```

2. **Start MongoDB**  
   If you're running MongoDB locally, make sure MongoDB is running. You can start it using the following command:

   ```bash
   mongod
   ```

   Alternatively, if you're using a cloud MongoDB database, make sure you have the connection string ready.

3. **Connect to MongoDB**  
   Connect to your MongoDB instance via the shell, MongoDB Compass, or any other MongoDB client.

   ```bash
   mongo
   ```

4. **Create the Database**  
   Use the `use` command to create and switch to the database `LibraryDB`.

   ```bash
   use LibraryDB
   ```

5. **Insert Collections and Documents**  
   Insert the collections and data provided in the `insertMany` operations (Books, Authors, and Patrons) using MongoDB commands in the shell or through a script.

---

## Operations

### CRUD Operations

1. **Read All Books**
   ```javascript
   db.Books.find();
   ```

2. **Find a Specific Book by Title**
   ```javascript
   db.Books.find({ title: "To Kill a Mockingbird" });
   ```

3. **Find All Books by a Specific Author (author_id: 5)**
   ```javascript
   db.Books.find({ author_id: 5 });
   ```

4. **Find All Available Books**
   ```javascript
   db.Books.find({ available: true });
   ```

### Update Operations

1. **Mark a Book as Borrowed**
   ```javascript
   db.Books.updateOne({ _id: 3 }, { $set: { available: false } });
   ```

2. **Add a Genre to a Book**
   
   db.Books.updateOne({ _id: 8 }, { $addToSet: { genres: "Epic" } });
   

3. **Add a Borrowed Book to a Patron's Record**

   db.Patrons.updateOne({ _id: 5 }, { $push: { borrowed_books: 6 } })
   ;![find all available books](https://github.com/user-attachments/assets/81ebfb1c-dcbf-4c0e-a3c4-5f67761a9366)
    ![find one with author nid of 5](https://github.com/user-attachments/assets/34c69035-9f6e-48df-be0c-5813f2ca3b23)

   ![methods](https://github.com/user-attachments/assets/e1360557-30f8-42c6-b696-f3899a413cfb)


### Delete Operations![finish](https://github.com/user-attachments/assets/4bad24bc-14f4-4c35-aff3-214d3dce59dd)


1. **Delete a Book by Title**
   
   db.Books.deleteOne({ title: "Brave New World" });
  

2. **Delete an Author**
  
   db.Authors.deleteOne({ _id: 3 });
   

### Advanced Queries

1. **Find Books Published After 1950**
  
   db.Books.find({ published_year: { $gt: 1950 } });
   

2. **Find All American Authors**
  
   db.Authors.find({ nationality: { $eq: "American" } });
  

3. **Set All Books to Available**
  
   db.Books.updateMany({}, { $set: { available: true } });
  

4. **Find Books Available and Published After 1950**
  
   db.Books.find({ available: true, published_year: { $gt: 1950 } });


5. **Find Authors Whose Names Contain "George"**
   
   db.Authors.find({ name: { $regex: "George", $options: "i" } });
  

6. **Increment the Published Year of "War and Peace"**

   db.Books.updateOne({ title: "War and Peace" }, { $inc: { published_year: 1 } });
   s![finish](https://github.com/user-attachments/assets/4bad24bc-14f4-4c35-aff3-214d3dce59dd)






