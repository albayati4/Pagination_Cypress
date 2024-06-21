![Image](https://media.licdn.com/dms/image/C5112AQEi3UU4OEjOzA/article-cover_image-shrink_600_2000/0/1580304392113?e=2147483647&v=beta&t=p7dkkyO4guUHym_Ee-cizoYaqPPgu7IP9mjx3-pPXMU)

## Date: 06/18/2024

### By: Abdullah Albayati

### Testing Front end project-05

#### Validating 3 test scenarios for all the components of a Pagination Function.

#### Creator Linkedin page

[Abdullah Albayati](https://www.linkedin.com/in/albayati-abdullah/)

---

#### This project was creatated and executed with the use of JaveScript, Node.js, Cypress, CSS selectors, POM, BDD with Cucumber.

---

### _Getting Started_

- In all test scenarios we are required to visit this page [project-5](https://www.techglobal-training.com/frontend/project-5)
- So I used `Background` In my features file with `Given the user is on` to handel visiting this website before each test scenario.
- I Created a separate folder called Pages with a PaginationPage.js file inside to be able to use POM (Page Object Model)
- In my PaginationPage.js I created a class called PaginationPage and I added all my locators and methods then I exported this class with
  ```JavaScript
  export default PaginationPage
  ```
- In order to use this page I had to imported in my pagination.js and create a new instance of this object to use it.
  ```JavaScript
  import PaginationPage from "../../../pages/PaginationPage";
  const pagination = new PaginationPage();
  ```
- I created a method inside my page to get to visit the web page everytime it's called.

  ```JavaScript
  // Methods

  /**
   * This function visits a web page when passed as an argument
   */
   goToTheWebPage(url) {
    return cy.visit(url);
  }
  ```

- I created an array from my data table in my feature file that I would use few times so I made it global

  ```JavaScript
  const tokyoInfo = dataTable.rawTable.flat();
  ```

- I used each to handel validating multiple detalis with their text from an array

  ```JavaScript
  Then(/^the user should see “Tokyo” City with the info below and an image$/, (dataTable) => {
  pagination.getCityImage().should("be.visible");
  const tokyoInfo = dataTable.rawTable.flat();
  pagination.getCityInfo().each(($el, index) => {
    cy.wrap($el).should("have.text", tokyoInfo[index]);
    });
  });
  ```

- I used `pagination.getNextButton().should("be.enabled")` to check if a button is clickable.

### _Screenshots_

![Image](https://i.ibb.co/6ZTfyPD/Screenshot-2024-06-18-at-1-18-25-PM.png)
