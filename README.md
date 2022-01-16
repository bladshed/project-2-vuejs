### PROJECT OVERVIEW
This project was made for people who are into fashion or style. The purpose of this web application is to let people share their fashion/style.

This may also help people that are not yet into fashion, they can look some styles that may help them or give them an idea of how to look good.

I believe this application will be a big help to those people who are undecided with what kind of clothes to wear, because you always aim to look good whenever you go out, especially when you are on a date.

Live link to my Web Application --> [Web Application](https://youthful-poitras-4c446c.netlify.app/)

If the link above didn't work, please initialize the backend API by accessing this link [API](https://fms-project-2-apis.herokuapp.com/outfits)

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

### UI/UX
* [Wireframes link](src/images)

* The design fonts colors revolves in neutral color because the background that I used is a bit wild (colorful). For buttons, I used green, blue and red, I chose these colors because it represents the nature's colors, blue and green are very pleasing to the eyes, red to catch the attention.


### USER STORIES
* US01. As a user, I want to view outfits that are available.
* US02. As a user, I want to add my own style to share it to people. 
* US03. As a user, I want to edit or delete in case I changed my mind with the fashion/style that I added.
* US04. As a user, I want to add some reviews to outfits that were submitted by other users.
* US05. As a user, I want to be able to edit my review/s in case there is a typo. 


### FEATURES
* The main feature of this web application is the reactive programming that handles real-time updates.

* I used vue js for the reactive programming, it's super developer friendly, so easy to use and implement and there are a lot features that they can offer that are very useful too.


### TECHNOLOGIES USED

* Vue js
   * To build my web application

* CSS
   * To customize my html elements

* Javascript
   * I used javascript to control all the functionalities of my application, it is like the brain of my application

* Visual Studio Code
   * IDE that I used for this project because it's easy to code here and easy to manage your files and data


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
      <td>Be able to add an outfit data</td>
   </tr>
   <tr>
      <td>Delete outfit</td>
      <td>Be able to delete an outfit data</td>
   </tr>
   <tr>
      <td>Edit outfit</td>
      <td>Be able to edit an outfit data</td>
   </tr>
   <tr>
      <td>View outfit</td>
      <td>Be able to view an outfit data</td>
   </tr>
   <tr>
      <td>Click View > scroll down, add a review</td>
      <td>Be able to add a review</td>
   </tr>
   <tr>
      <td>Click View > scroll down, edit a review</td>
      <td>Be able to edit a review</td>
   </tr>
   <tr>
      <td>Click View > scroll down, delete a review</td>
      <td>Be able to delete a review</td>
   </tr>
</table>


### PLATFORM USED
* Github for CI/CD
* Dependencies used
   * bootstrap (for my CSS)
      * I used bootstrap in my entire UI web application because it's super easy to manipulate html elements and they also provide basic element designs where I was able to save a lot time in designing like my buttons, navbar, etc.

   * bootstrap-vue
      * I used this for my pop-up modals when adding, editing or viewing outfit data.

   * qs
      * I used query string parsing when passing my query data to my search API.

   * Google fonts and Font awesome
      * These two libraries were used for my fonts and icons. They have cool fonts and icons.


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
        Done (except for dropdown, not applicable)
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
        Used b-modal from bootstrap-vue
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
