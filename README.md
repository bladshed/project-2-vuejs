### PROJECT OVERVIEW
This project was made for people who are into fashion or style. The purpose of this web application is to let people share their fashion/style.

This may also help people that are not yet into fashion, they can look some styles that may help them or give them ideas on how to style.

I believe this application will be a big help to those people who are undecided with what kind of clothes to wear, because you always aim to look good whenever you go out, especially when you are on a date.

Live link to my Web Application --> [Web Application](https://youthful-poitras-4c446c.netlify.app/)

If the link above didn't work, please initialize the backend API by accessing this link [API](https://fms-project-2-apis.herokuapp.com/outfits)

## BUSINESS

### Business problem
1) Business problem solving
   * can not find an efficient way to look for an outfit to wear on the internet
   * search engine is too broad and choices are not focused according to user preference
   * no place to share and see other people's reviews (as fashion is heavily dependent on trend so opinions and reviews are very important for them)

2) What was the solution
   * to have a repository of fashion wear suggestion for yuppies and students on the go
   * to focus on the specific outfits they want to see
   * to let people interact with one another and make suggestions
   * a comprehensive online application where people can get suggested fashion wear 24/7 and share suggested fashion wear to the community

3) Results of the implementation
   * the application was tried and tested by selected individuals and made the following comments.
      * User was able to view outfits that are available.
      * User was able add my his/her own style to share it to people. 
      * User was able to edit or delete an outfit from the list.
      * User was able to add reviews to outfits that were submitted by other people.
      * User was able to edit his/her review/s.

4) Lessons learned
   * What was done well?
      * implemented reactive programming and by using it, it was easier for me to develop the application since it lessens the code I need to write
      * client-server communication was done nicely
      * deploying and updating the application was okay
      * testing the application was smooth because some of my friends helped me
   
   * What didn't go that well?
      * UI was not very nice since I didn't have enough time to do it because I was also busy with my work
      * implementing technologies that you are not yet very familiar with was very challenging since you need to learn so many things, it is very time consuming

   * What else could be improved?
      * Improve UI to make it more pleasing to users
      * To have a User Management System


### FEATURES
* Able to view, add, edit, delete an outfit
* People can share their reviews in every outfit
* The main feature of this web application is the reactive programming that handles real-time updates


### USER STORIES
* US01. As a user, I want to view outfits that are available.
* US02. As a user, I want to add my own style to share it to people. 
* US03. As a user, I want to edit or delete in case I changed my mind with the fashion/style that I added.
* US04. As a user, I want to add some reviews to outfits that were submitted by other users.
* US05. As a user, I want to be able to edit my review/s in case there is a typo. 


## TECHNICAL

### Understanding of the business problem
* I need to have a database for storing data
* Build a search engine that returns only what is relevant
* To allow user to do CRUD for an outfit
* To allow user to share their reviews

### UI/UX
* [Wireframes link](src/images)

* The design fonts colors revolves in neutral color because the background that I used is a bit wild (colorful). For buttons, I used green, blue and red, I chose these colors because it represents the nature's colors, blue and green are very pleasing to the eyes, red to catch the attention.


### Architectural decisions and constraints

* Github for CI/CD

* IDE
   * Visual Studio Code
      * Pros:
         * developer friendly
         * can develop both backend and frontend
      * Cons:
         * not yet familiar

* DATABASE
   * Mongo DB
      * Pros:
         * faster
         * lightweight
         * uses javascript for query
      * Cons:
         * data is not consistent
         * not yet familiar

* BACKEND
   * Node js
      * Pros:
         * uses javascript
         * lightweight
         * most language used in development so it is easier to connect to other systems
      * Cons:
         * not yet familiar
   
   * Express framework
      * Pros:
         * provides a thin layer of fundamental web application features
      * Cons:
         * not good for big application

* FRONTEND
   * Vue js
      * Pros:
         * uses javascript
         * reactive programming (real-time update)
         * less development time
      * Cons:
         * new technology, need time to learn

   * Bootstrap
      * Pros:
         * provides basic element designs
         * helps to manipulate html elements 
         * save time in designing your UI
      * Cons:
         * heavyweight
   

### DEPENDENCIES USED
   * bootstrap-vue
      * I used this for my pop-up modals when adding, editing or viewing outfit data.

   * qs
      * I used query string parsing when passing my query data to my search API.

   * Google fonts and Font awesome
      * these two libraries were used for my fonts and icons. They have cool fonts and icons.

### FUNCTIONAL AND NON FUNCTIONAL REQUIREMENTS

* Functional
   * Able to create, read, update and delete an outfit
   * Able to create, read, update and delete a review of an outfit
   * Users are able to see other users added outfits
   * Users are able to see other users reviews

* Non-Functional
   * Performance
      * API calls takes less than 2 seconds
      * Database read/write takes less than 2 second to process
   
   * Storage
      * Cannot store more than 512mb since Im only using free edition

   * Security
      * Application grants access to anyone
      * All users can see data
      * Doesn't show any personal data aside from email

   * Portability and compatibility
      * Works with any browsers
      * Works with any OS as long as it uses web browser
      * Works with phones and tablets

   * Maintainability
      * Bug fix many only take a few minutes since it's a small application
      * Easy to troubleshoot since it uses javascript from backend to frontend
   
   * Availability
      * Application is always accessible to users any time
      * No login needed, can use the web applicaiton right away

   * Usability
      * Application is pretty straight forward
      * UI is very simple and easy to understand
   

### High Level Design
* [HLD link](src/images)

### PROJECT SETUP
```
yarn install
```

#### Compiles and hot-reloads for development
```
yarn serve
```

#### Compiles and minifies for production
```
yarn build
```

#### Lints and fixes files
```
yarn lint
```

#### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Build & Deployment
* Initialize project
   * npm install -g @vue/cli
   * vue create .
   * yarn add bootstrap
   * npm i -g @vue/cli-service-global
   * yarn add axios
   * npm i bootstrap-vue
   * yarn add @fortawesome/fontawesome-svg-core@next (optional)
   * yarn add @fortawesome/free-solid-svg-icons@next (optional)
   * yarn add @fortawesome/free-regular-svg-icons@next (optional)
   * yarn add @fortawesome/vue-fontawesome@latest (optional)
   * yarn add qs (optional)

* Commit and push changes
   * git commit -m "commit message"

* BACKEND
   * Deploy to Heroku
      * Register an account with Heroku at [https://www.heroku.com](https://www.heroku.com)
      * At the terminal, log in to heroku with:
         * heroku login -i
      * heroku create <app-name>
      * Add a start script to package.json
      * git push heroku master
      * Setup the config variables in Heroku client app

* FRONTEND
   * Deploy to Netlify
      * Register an account with Netlify at [https://www.netlify.com](https://www.netlify.com/)
      * Add A New Project
      * Link your Github account and authorize Netlify
      * Select Your Repo
      * Configure Your Settings
   * Every time you commit and push to your github, Netlify will get the latest code


### TEST CASES
<table>
   <tr>
      <th colspan=2>Outfits Page
   </tr>
   <tr>
      <th>
         <img width="441" height="1">
         <small>Action</small>
      </td>
      <th>
         <img width="441" height="1">
         <small>Expected Result</small>
      </td>
   </tr>
   <tr>
      <td>Add outfit</td>
      <td>Added new outfit data</td>
   </tr>
   <tr>
      <td>Delete outfit</td>
      <td>Deleted an outfit data</td>
   </tr>
   <tr>
      <td>Edit outfit</td>
      <td>Edited an outfit data</td>
   </tr>
   <tr>
      <td>View outfit</td>
      <td>Able to view an outfit data</td>
   </tr>
   <tr>
      <td>Click View > scroll down, add a review</td>
      <td>Added new review</td>
   </tr>
   <tr>
      <td>Click View > scroll down, edit a review</td>
      <td>Edited a review</td>
   </tr>
   <tr>
      <td>Click View > scroll down, delete a review</td>
      <td>Deleted a review</td>
   </tr>
</table>

### PROJECT COMPLEXITY
<table>
   <tr>
      <th colspan=2>VUE FRONTEND
   <tr>
   <tr>
      <th>
         <img width="441" height="1">
         <small>Items</small>
      </td>
      <th>
         <img width="441" height="1">
         <small>Actions</small>
      </td>
   <tr>
   <tr>
      <td>
        Using v-model with each of the form control below:
        <ul>
            <li>Text input</li>
            <li>Text area</li>
            <li>Radio button</li>
            <li>Dropdown select single</li>
            <li>Multi-select checkbox</li>
            <li>Multi-select dropdown</li>
        </ul>
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each instance of using v-bind to customize the style attribute of a HTML element
      </td>
      <td>
        Done (see #content-div div in OutfitsPage.vue)
      </td>
   <tr>
   <tr>
      <td>
        Each instance of v-if
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each computed property
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each event handler with v-on
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each instance of list rendering
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each instance of adding to a list
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each instance of removing from a list
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each instance of modifying an item in a list
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each use of a life cycle method in a component (componentDidMount for example)
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each use of props
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each custom event emitted and consumed by a parent component
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Each component used beyond the first two (including App.vue)
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Client side searching
      </td>
      <td>
        Done
      </td>
   <tr>
   <tr>
      <td>
        Every feature not listed above
      </td>
      <td>
        Done (used b-modal from bootstrap-vue)
      </td>
   <tr>
   <tr>
      <td>
        Each customizable component that can be reused
      </td>
      <td>
        Done
      </td>
   <tr>
</table>


### CREDITS
* Thanks to Mr Paul Chor, our teacher for Node js, Express and Vue js
* Thanks to positronx for the sample b-modal implementation
   * [positronx](https://www.positronx.io/how-to-add-and-use-bootstrap-modal-in-vue-js-app/)
* For my code snippets, tutorial, questions and saviour of all developers
   * [Google](https://www.google.com/)
