<div id="top"></div>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url] [![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

  <h3 align="center">Book Search Engine</h3>

  <p align="left">
    A Google Books API search engine built with a RESTful API, refactored to be a GraphQL API built with Apollo Server. The app was built using the MERN stack with a React front end, MongoDB database, and Node.js/Express.js server and API. It's already set up to allow users to save book searches to the back end.
    <br />
    <a href="https://github.com/heranYang93/book-search-engin"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://book-search-engine-hy.herokuapp.com/">View Demo</a>
    ·
    <a href="https://github.com/heranYang93/book-search-engin/issues">Report Bug</a>
    ·
    <a href="https://github.com/heranYang93/book-search-engin/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#user-story">User story</a></li>
        <li><a href="#acceptance-criteria">Acceptance Criteria</a></li>
        <li><a href="#back-end-specifications">Back-End Specifications/a></li>
        <li><a href="#front-end-specifications">Front-End Specifications</a></li>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#prerequisites">Prerequisites</a></li>
      </ul>
    </li>
    <li><a href="#dependencies">npm dependencies</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

## About The Project

[![Product Name Screen Shot][product-screenshot]](https://example.com)

- Set up an Apollo Server to use GraphQL queries and mutations to fetch and modify data, replacing the existing RESTful API.
- Modified the existing authentication middleware so that it works in the context of a GraphQL API.
- Created an Apollo Provider so that requests can communicate with an Apollo Server.
- Deployed the application to Heroku with a MongoDB database using MongoDB Atlas.

<p align="right">(<a href="#top">back to top</a>)</p>

### User Story

```md
AS AN avid reader

I WANT to search for new books to read
SO THAT I can keep a list of books to purchase
```

images.

## Acceptance Criteria

```md
GIVEN a book search engine

WHEN I load the search engine
THEN I am presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button

WHEN I click on the Search for Books menu option
THEN I am presented with an input field to search for books and a submit button

WHEN I am not logged in and enter a search term in the input field and click the submit button
THEN I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site

WHEN I click on the Login/Signup menu option
THEN a modal appears on the screen with a toggle between the option to log in or sign up

WHEN the toggle is set to Signup
THEN I am presented with three inputs for a username, an email address, and a password, and a signup button

WHEN the toggle is set to Login
THEN I am presented with two inputs for an email address and a password and login button

WHEN I enter a valid email address and create a password and click on the signup button
THEN my user account is created and I am logged in to the site

WHEN I enter my account’s email address and password and click on the login button
THEN I the modal closes and I am logged in to the site

WHEN I am logged in to the site
THEN the menu options change to Search for Books, an option to see my saved books, and Logout

WHEN I am logged in and enter a search term in the input field and click the submit button
THEN I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site and a button to save a book to my account

WHEN I click on the Save button on a book
THEN that book’s information is saved to my account

WHEN I click on the option to see my saved books
THEN I am presented with all of the books I have saved to my account, each featuring the book’s title, author, description, image, and a link to that book on the Google Books site and a button to remove a book from my account

WHEN I click on the Remove button on a book
THEN that book is deleted from my saved books list

WHEN I click on the Logout button
THEN I am logged out of the site and presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button
```

### Back-End Specifications

You’ll need to complete the following tasks in each of these back-end files:

- `auth.js`: Update the auth middleware function to work with the GraphQL API.

- `server.js`: Implement the Apollo Server and apply it to the Express server as middleware.

- `Schemas` directory:

  - `index.js`: Export your typeDefs and resolvers.

  - `resolvers.js`: Define the query and mutation functionality to work with the Mongoose models.

  - `typeDefs.js`: Define the necessary `Query` and `Mutation` types:

    - `Query` type:

      - `me`: Which returns a `User` type.

    - `Mutation` type:

      - `login`: Accepts an email and password as parameters; returns an `Auth` type.

      - `addUser`: Accepts a username, email, and password as parameters; returns an `Auth` type.

      - `saveBook`: Accepts a book author's array, description, title, bookId, image, and link as parameters; returns a `User` type. (Look into creating what's known as an `input` type to handle all of these parameters!)

      - `removeBook`: Accepts a book's `bookId` as a parameter; returns a `User` type.

    - `User` type:

      - `_id`

      - `username`

      - `email`

      - `bookCount`

      - `savedBooks` (This will be an array of the `Book` type.)

    - `Book` type:

      - `bookId` (Not the `_id`, but the book's `id` value returned from Google's Book API.)

      - `authors` (An array of strings, as there may be more than one author.)

      - `description`

      - `title`

      - `image`

      - `link`

    - `Auth` type:

      - `token`

      - `user` (References the `User` type.)

### Front-End Specifications

You'll need to create the following front-end files:

- `queries.js`: This will hold the query `GET_ME`, which will execute the `me` query set up using Apollo Server.

- `mutations.js`:

  - `LOGIN_USER` will execute the `loginUser` mutation set up using Apollo Server.

  - `ADD_USER` will execute the `addUser` mutation.

  - `SAVE_BOOK` will execute the `saveBook` mutation.

  - `REMOVE_BOOK` will execute the `removeBook` mutation.

Additionally, you’ll need to complete the following tasks in each of these front-end files:

- `App.js`: Create an Apollo Provider to make every request work with the Apollo Server.
- `SearchBooks.js`:

  - Use the Apollo `useMutation()` Hook to execute the `SAVE_BOOK` mutation in the `handleSaveBook()` function instead of the `saveBook()` function imported from the `API` file.

  - Make sure you keep the logic for saving the book's ID to state in the `try...catch` block!

- `SavedBooks.js`:

  - Remove the `useEffect()` Hook that sets the state for `UserData`.

  - Instead, use the `useQuery()` Hook to execute the `GET_ME` query on load and save it to a variable named `userData`.

  - Use the `useMutation()` Hook to execute the `REMOVE_BOOK` mutation in the `handleDeleteBook()` function instead of the `deleteBook()` function that's imported from `API` file. (Make sure you keep the `removeBookId()` function in place!)

- `SignupForm.js`: Replace the `addUser()` functionality imported from the `API` file with the `ADD_USER` mutation functionality.

- `LoginForm.js`: Replace the `loginUser()` functionality imported from the `API` file with the `LOGIN_USER` mutation functionality.

### Built With

- [GraphQL](https://www.javascript.com/)
- [MongoDB](https://https://www.mongodb.com/)
- [Express](https://expressjs.com/)
- [React](https://reactjs.org/)
- [Node.js](https://nodejs.org/en/)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

### Installation

0. Run deployed app at: https://book-search-engine-hy.herokuapp.com/
1. Clone the repo
   ```sh
   git clone git@github.com:heranYang93/book-search-engin.git
   ```
2. Install NPM packages
   ```sh
   npm i
   ```
3. run

```sh
   npm run develop
```

### Prerequisites

Install all necessary dependencies by executing:

```sh
npm i
```

## Dependencies

```javascript
    "apollo-server-express": "^3.6.7",
    "bcrypt": "^4.0.1",
    "dotenv": "^16.0.0",
    "express": "^4.17.1",
    "graphql": "^16.4.0",
    "jsonwebtoken": "^8.5.1",
    "mongoose": "^5.9.10"
    "@apollo/client": "^3.5.10",
    "@testing-library/jest-dom": "^4.2.4",
    "@testing-library/react": "^9.3.2",
    "@testing-library/user-event": "^7.1.2",
    "bootstrap": "^4.4.1",
    "graphql": "^16.4.0",
    "jwt-decode": "^2.2.0",
    "react": "^16.13.1",
    "react-bootstrap": "^1.0.1",
    "react-dom": "^16.13.1",
    "react-router-dom": "^6.2.1",
    "react-scripts": "^4.0.2"
```

<p align="right">(<a href="#top">back to top</a>)</p>

## Contributing

If you have a suggestion that would make this better, please fork the repo and
create a pull request. You can also simply open an issue with the tag
"enhancement". Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- LICENSE -->

## Hosting

| Project            | URL                                            |
| ------------------ | ---------------------------------------------- |
| book search engine | <https://book-search-engine-hy.herokuapp.com/> |

<p align="right">(<a href="#top">back to top</a>)</p>

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- CONTACT -->

## Contact

> Heran Yang
> ![GitHub followers](https://img.shields.io/github/followers/heranYang93?style=social)

<!-- > ![GitHub followers](https://img.shields.io/github/followers/heranYang93?style=social) -->

Project Link:
[github.com/heranYang93/book-search-engine](https://github.com/heranYang93/book-search-engin)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->

<p align="right">(<a href="#top">back to top</a>)</p>

[contributors-shield]: https://img.shields.io/github/contributors/heranYang93/book-search-engin.svg?style=for-the-badge
[contributors-url]: https://github.com/heranYang93/book-search-engin/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/heranYang93/book-search-engin.svg?style=for-the-badge
[forks-url]: https://github.com/heranYang93/book-search-engin/network/members
[stars-shield]: https://img.shields.io/github/stars/heranYang93/book-search-engin.svg?style=for-the-badge
[stars-url]: https://github.com/heranYang93/book-search-engin/stargazers
[issues-shield]: https://img.shields.io/github/issues/heranYang93/book-search-engin.svg?style=for-the-badge
[issues-url]: https://github.com/heranYang93/book-search-engin/issues
[license-shield]: https://img.shields.io/github/license/heranYang93/book-search-engin.svg?style=for-the-badge
[license-url]: https://github.com/heranYang93/book-search-engin/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url-md]: https://www.linkedin.com/in/muhammad-daaboul-38470046/
[github-follow-shield-md]: https://img.shields.io/github/followers/heranYang93?style=social
[linkedin-url-hy]: https://linkedin.com/in/heranyang/
[github-follow-shield-hy]: https://img.shields.io/github/followers/moedaaboul?style=social
[linkedin-url-eh]: https://linkedin.com/in/eoin-harkin-229115216/
[linkedin-url-iw]: https://linkedin.com/in/iler-watson-643442158/
[linkedin-url-man]: https://linkedin.com/in/mbongeni-allan-ngwenya-220375170/
[product-screenshot]: /__demo.gif
