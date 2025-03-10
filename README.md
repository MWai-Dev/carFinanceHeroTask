## To view a local build in a web browser:

1. Once you've cloned the Git repository to your local machine simply go to the downloaded `carFinanceHeroTask` folder

2. Right click the `cfh-task` folder and open the project in vsCode or your IDE of choice

3. You can preview the build by: 
    - In the terminal typing `npm run dev`

4. Then either `ctrl` + left mouse click on the local link the terminal provides to open it in a browser or copy and paste it into a browser.


## To view on a web server:

I have added the distributable build to my own web server as an option for previewing at [https://mwaistell.site/projects/CarFinanceTask/](https://mwaistell.site/projects/CarFinanceTask/)


## Page interactivity:

I've added information regarding my choices for the design in the file: `carFinanceHeroTask/cfh-design/Design Decisions.text` if you want to see more about that. 

The page is quite simple to use. You can click in the 'Loan amount' field and type how much you want to borrow, if you enter below 1000 or 20000 an error message will appear informing you to enter between these set minimum and maximum values, and it will stop you from being able to submit the form.

Once correct you can then select the loan term (6 months is selected as a default) and finally you can click the `Get Your Quote` button to submit the form. It then changes a boolean value which is passed through using Vues `v-model` and props, which triggers the `App.vue` to load the `ApplicationForm` page with the stored values you input and selected from the form.


## Build information:

This project has been built using vue.js with Vite to help speed up the project build and I also used SCSS too, so there are a few extra tool files in this directory that aren't necessarily important to the front end build itself. 

Even though I built it with vue.js I wanted to keep it simple to browse through the code so I didn't build it as too many individual components, there's the: 

1. `app.vue` file in the `src` folder which initially renders the `HeroSection` component page until you complete the form where it instead renders the `ApplicationForm` component page.

2. `HeroSection` file in the `src/components` folder which contains all of the Hero Section build code for this project including the loans form.

3. `ApplicationForm.vue` file also in the `src/components` folder which along with a placeholder message for where the hypothetical application form itself would be added, there are some boxes for confirming what was submitted in the form and estimated monthly and total payments.


Although I kept the component structure simple I wanted to add passing data between the components to allow the use of reactive loan information based upon what the user had input and selected in the loan form as a little extra.

Because I built the styling using SCSS there is both the original `main.scss` and the converted `main.css` file in the `src/assets` folder for the styling.
