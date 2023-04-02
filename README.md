## GSOC'23 Proposal - Sugarlabs

### Sugarizer VueJS Core

### Basic Details:

- Full Name: Abhinav Kumar
- Email: [kumar.kr.abhinav@gmail.com](mailto:kumar.kr.abhinav@gmail.com)
- Github Username: [kr-2003](https://github.com/kr-2003)
- Your first language: Hindi
- Location and Timezone: Time zone in Kasturba Gram, Indore, Madhya Pradesh 452020 (GMT+5:30)
- Link to Resume/CV: [https://drive.google.com/file/d/1NF6XMtUzyY6VVbtgp5eKkO2Zp9vEayeB/view?usp=sharing](https://drive.google.com/file/d/1NF6XMtUzyY6VVbtgp5eKkO2Zp9vEayeB/view?usp=sharing)
- I previously contributed to CircuitVerse on their cv-frontend-vue repo. These are the links:
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/87](https://github.com/CircuitVerse/cv-frontend-vue/pull/87)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/97](https://github.com/CircuitVerse/cv-frontend-vue/pull/97)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/130](https://github.com/CircuitVerse/cv-frontend-vue/pull/130)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/127](https://github.com/CircuitVerse/cv-frontend-vue/pull/127)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/122](https://github.com/CircuitVerse/cv-frontend-vue/pull/122)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/116](https://github.com/CircuitVerse/cv-frontend-vue/pull/116)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/112](https://github.com/CircuitVerse/cv-frontend-vue/pull/112)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/111](https://github.com/CircuitVerse/cv-frontend-vue/pull/111)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/103](https://github.com/CircuitVerse/cv-frontend-vue/pull/103)
  - [https://github.com/CircuitVerse/cv-frontend-vue/pull/102](https://github.com/CircuitVerse/cv-frontend-vue/pull/102)
  - [https://github.com/CircuitVerse/cv-frontend-vue/issues/115](https://github.com/CircuitVerse/cv-frontend-vue/issues/115)
  - [https://github.com/CircuitVerse/cv-frontend-vue/issues/109](https://github.com/CircuitVerse/cv-frontend-vue/issues/109)
- Convince us that you will be a good fit for this project, by sharing links to your contribution to Sugar Labs
  - Since I want to contribute to the VueJS implementation of Sugarizer, I tried implementing some components by myself. This is the link to the repository for the same:
    - [https://github.com/kr-2003/sugarizer_personal_vuej](https://github.com/kr-2003/sugarizer_personal_vuejs)s
  - I am Abhinav Kumar, a current undergraduate pursuing a degree in Computer Science from IIT Indore in India. My passions lie in software development, competitive programming, and cybersecurity. Throughout the past year, I have been refining my skills in software development and data structures and algorithms. More recently, I have started to contribute to open-source projects, with a specific interest in cybersecurity. I am well-versed in various tech stacks, including VueJS, ReactJS, NextJS, Javascript, ExpressJS, FastAPI, and MongoDB. I have built an online gaming website with five multiplayer games, heavily utilizing Javascript, DOM manipulation, and Websockets. I have designed the logic behind these games, providing me with a wealth of experience with Vanilla JS and DOM manipulation. Furthermore, I have developed multiple websites using ReactJS and VueJS, giving me hands-on experience with JS frameworks.
  - Since I already have good experience with Javascript, Typescript, VueJS and I have also contributed to open source projects based on these tech stacks, I find myself suitable for this project.

## Overview of Project:

Sugarizer Core UI rely on EnyoJS, a deprecated frameworks initially developed for WebOS.  
The idea of this new project is to reimplement a part of Sugarizer Core UI using VueJS components.

**Tasks**

Use Sugarizer VueJS components and Sugarizer Server API to implement screens:

- First screen
- Login
- Home view
- List view
- Settings

Each screen should integrate unit testing and code coverage.

## Details:

This project requires us to implement Sugarizer Core UI components in VueJS components. I have already tried to do some work.  [Click here](https://github.com/kr-2003/sugarizer_personal_vuejs) for the repo. The file structure is like this:

<img src="https://33333.cdn.cke-cs.com/kSW7V9NHUXugvhoQeFaf/images/2f2d497b35f880e50a0ce6654fdcc3bea1a7269883cafcde.png" width="50%" height="50%"></img>

- The project is using a build setup based on [Vite](https://vitejs.dev/) and allowing us to use Vue [Single-File Components](https://vuejs.org/guide/scaling-up/sfc.html) (SFCs).
- I have added Vitest for unit testing.
- Also added Cypress for E2E testing.
- All the icons for the project are under “/src/assets/icons”.
- [Vue I18n](https://kazupon.github.io/vue-i18n/introduction.html) is internationalization plugin of Vue.js. It easily integrates some localization features to your Vue.js Application.
  - All the localization files are under `/locales` directory.
  - The localization is initialized in `main.js` file like this:

```javascript
import { createApp } from "vue";
import { createPinia } from "pinia";
import { createI18n } from "vue-i18n";
import en from "../locales/en.json";
import ar from "../locales/ar.json";
import de from "../locales/de.json";
import eu from "../locales/eu.json";
import es from "../locales/es.json";
import fr from "../locales/fr.json";
import ibo from "../locales/ibo.json";
import ja from "../locales/ja.json";
import pl from "../locales/pl.json";
import pt from "../locales/pt.json";
import yor from "../locales/yor.json";

import App from "./App.vue";
import router from "./router";

import "./assets/main.css";

const app = createApp(App);

const i18n = createI18n({
  locale: "en",
  messages: {
    en: en,
    ar: ar,
    de: de,
    es: es,
    eu: eu,
    fr: fr,
    ibo: ibo,
    ja: ja,
    pl: pl,
    pt: pt,
    yor: yor,
  },
});

app.use(createPinia());
app.use(router);
app.use(i18n);

app.mount("#app");
```

- To get translation of any word, just use the following template:

```javascript
<p class="icon-label">{{ $t('Login') }}</p>
```

This will give the translation of 'Login' in language that is set as 'locale' while initializing `createI18n`.

- [Pinia](https://pinia.vuejs.org/introduction.html) is a store library for Vue, it allows you to share a state across components/pages. For this project, I have used Pinia for state management.

#### First Screen

![](https://33333.cdn.cke-cs.com/kSW7V9NHUXugvhoQeFaf/animations/baf6a1a33467c2d498a15ef005f8ee82648cb25e1fcd142a.gif)

- All the components of firstScreen are under “/src/components/firstScreen”.
- The page for firstScreen is under “src/views/FirstScreenView.vue”.

```javascript
<template>
  <main>

    <div class="firstScreen-menu">
      <NewUserView></NewUserView>
      <router-link :to="{name: 'login'}"><LoginView></LoginView></router-link>
    </div>
  </main>
</template>

<script setup>
import NewUserView from '../components/firstScreen/NewUserView.vue'
import LoginView from '../components/firstScreen/LoginView.vue'
</script>

<style scoped>
.firstScreen-menu {
  position: absolute;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
}

</style>
```

- \<router-link> is used for navigating through links.

#### Intro/Guide Tour

- Currently, I haven't worked upon intro/guide tour.
- The `intro.js` file in the main Sugarizer repo has around 3300 lines of JS code.
- There could be two ways to implement into guide in our Vue components:
  - First: Just directly copy-paste the logic of `intro.js` into the `<script>` tag of intro component.
  - Second: Re-write the logic of `intro.js` using Vue modern features.
- Obviously, the first way is easy and fast.
- If the time permits, I would try to implement `intro.js` in Vue modern syntax.

#### Login Screen

<img src="/assets/images/login.gif"></img>

- All the components of loginScreen are under “/src/components/loginScreen”.
- The page for loginScreen is under “src/views/LoginView.vue”.

```javascript
<template>
  <div>
    <div class="login-wrapper">
      <div class="name-label">Name:</div>
      <loginInput></loginInput>
    </div>
    <IconButton
      @click="$router.go(-1)"
      id="left-button"
      iconButtonText="Back"
      iconButtonLink="go-left-icon"
    ></IconButton>
    <IconButton id="right-button" iconButtonText="Next" iconButtonLink="go-right-icon"></IconButton>
  </div>
</template>

<script setup>
import IconButton from '../components/IconButton.vue'
import loginInput from '../components/loginScreen/loginInput.vue'
</script>

<style scoped>
.name-label {
  position: relative;
  left: 20px;
  margin-top: 20px;
  color: #808080;
  margin-bottom: 20px;
  text-align: center;
}
.login-wrapper {
  position: absolute;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
}
</style>

```

- Vue-Router is used for navigation between different pages.
- Currently, only the frontend is implemented for the login screen.

#### Home View

This is the HomeView of original Sugarizer.
<img style="margin-top: 20px" src="assets/images/home.png"></img>


- This is [link](https://github.com/kr-2003/sugarizer/blob/master/js/homeview.js) to homeview.js of original sugarizer.
- This contains the javascript logic of the homeview.
- After seeing the code, and seeing how the website works, I obeserved that most of the components are dynamically rendered.
- It means that after meeting certain conditions and requirement, then we draw/show the components on the screen.
- We can implement this in Vue in following way:

  - Dynamically rendering of components.
  - First, we can already make components.
  - And then dynamically toggle components based on event listeners.
  - For example,

  ```javascript
  import Card1 from "./components/card1.vue";
  import Card2 from "./components/card2.vue";

  export default {
    data() {
      return {
        currentComponent: "Card1",
      };
    },
    methods: {
      toggle() {
        this.currentComponent =
          this.currentComponent === "Card1" ? "Card2" : "Card1";
      },
    },
    components: {
      Card1,
      Card2,
    },
  };
  ```

  ```javascript
  <template>
  <center>
    <h1 style="text-align: center;
        color: green">
        Sugarizer
    </h1>
    <strong>
        Vue.js Dynamic Components
    </strong>
    <br />
  </center>
  <center>
    <component :is="currentComponent" />
    <button @click="toggle">Toggle</button>
  </center>
  </template>
  ```

    * The above code when clicked on toggle button, the "toggle" method is called and accordingly current component is changed.
    * The components is bind to currentComponent.
    * This is how we can render dynamic components in VueJS.


* homeview.js is a huge file with around 900 lines of code. This isn't good practice. 
* We can refactor this code and split multiple functions into different files.
* And then import these functions in the main component in ```<script>``` tag.

#### List View

* This is [link](https://github.com/kr-2003/sugarizer/blob/master/js/listview.js) listview.js of original sugarizer.
* The way explained about HomeView, we can implement ListView in the same way.

#### Settings

* This is settings component of main Sugarizer.

<img src="./assets/images/settings.png"></img>

* This is [link](https://github.com/kr-2003/sugarizer/blob/master/js/dialog.js) settings.js of original sugarizer.
* We can implement dialog in the same way as we will be implementing other components.
* We can implement modal/dialog this way:

```javascript 
<template>
  <div id="app">
    <button
      type="button"
      class="btn"
      @click="showModal"
    >
      Open Modal!
    </button>

    <Modal
      v-show="isModalVisible"
      @close="closeModal"
    />
  </div>
</template>

<script>
  import modal from './components/Modal.vue';

  export default {
    name: 'App',
    components: {
      Modal,
    },
    data() {
      return {
        isModalVisible: false,
      };
    },
    methods: {
      showModal() {
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      }
    }
  };
</script>

```

* The core concept behind this code is same as that for dynamically rendering components.
* Just this code is more specific towards dialog/modal.
* Initially, isModalVisible is false for the components.
* And it is toggled when appropriate method is called upon clicking.
