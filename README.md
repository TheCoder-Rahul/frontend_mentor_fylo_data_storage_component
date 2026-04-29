# Frontend Mentor - Fylo data storage component solution

This is a solution to the [Fylo data storage component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/fylo-data-storage-component-1dZPRbV5n). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size

### Screenshot

![Design screenshot](https://github.com/TheCoder-Rahul/frontend_mentor_fylo_data_storage_component/blob/main/project_screenshot.png)

### Links

- 👉 [Solution URL](https://github.com/TheCoder-Rahul/frontend_mentor_fylo_data_storage_component.git)
- 👉 [Live Site URL](https://thecoder-rahul.github.io/frontend_mentor_fylo_data_storage_component/)

## My process

### Built with

- 👉 **Markup:** Semantic HTML5 for better accessibility and SEO.
- 👉 **Styling:** CSS3 with Custom Properties (variables) for a maintainable color scheme, font-properties, and different sizes.
- 👉 **Layout:** Flexbox for centering the card and managing the internal alignment.
- 👉 **Workflow:** Mobile-first approach and Responsive Design using Media Queries.

### What I learned

Check my code snippets below:

```html
<main>
  <article>
    <img src="./assets/images/logo.svg" alt="Fylo Logo">
    <ul>
      <li>
        <img src="./assets/images/icon-document.svg" alt="Document Icon">
      </li>
      <li>
        <img src="./assets/images/icon-folder.svg" alt="Folder Icon">
      </li>
      <li>
        <img src="./assets/images/icon-upload.svg" alt="Upload Icon">
      </li>
    </ul>
  </article>
  <article>
    <section class="storage-info">
      <h1>185 <span>GB Left</span></h1>
    </section>
    <p>You've used <strong>815 GB</strong> of your storage</p>
    <section class="progress-wrapper">
      <div class="progress-bar"><span></span></div>
    </section>
    <section class="progress-length">
      <p>0 GB</p>
      <p>1000 GB</p>
    </section>
  </article>
</main>
```
```css
@font-face {
  font-style: normal;
  font-display: swap;
  font-weight: 400 700;
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-VariableFont_wght.ttf) format('truetype');
}
@font-face {
  font-style: italic;
  font-display: swap;
  font-weight: 400 700;
  font-family: 'Raleway';
  src: url(./assets/fonts/Raleway-Italic-VariableFont_wght.ttf) format('truetype');
}
:root {
  --fs-base: 0.75rem;
  --base-size: 0.75rem;
  --size-extreme: 3rem;
  --white: hsl(0, 0%, 100%);
  --primary: hsl(228, 56%, 26%);
  --primary-gray: hsl(229, 7%, 55%);
  --primary-dark: hsl(229, 57%, 11%);
  --primary-light: hsl(243, 100%, 93%);
  --mobile-bg: url(./assets/images/bg-mobile.png);
  --desktop-bg: url(./assets/images/bg-desktop.png);
  --progress-gradient: hsl(6, 100%, 80%), hsl(335, 100%, 65%);

  @media (width > 60rem) {
    --fs-base: 0.875rem;
  }
}
@layer reset {
  *, *::before, *::after {
    box-sizing: border-box;
  }
  h1, p {
    margin: 0;
  }
  h1 {
    font-weight: 700;
    font-size: calc(var(--fs-base) * 2.5);
  }
  img {
    display: block;
    max-width: 100%;
  }
  ul {
    list-style: none;
    margin-block: 0;
    padding-inline: 0;
  }
}
@layer base {
  html {
    line-height: 1.2;
    font-family: 'Raleway', sans-serif;
  }
  body {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: var(--fs-base);
    color: var(--primary-light);
    min-block-size: calc(100vh - 1rem);
    background: var(--mobile-bg) center bottom / contain no-repeat var(--primary-dark);

    @media (width > 60rem) {
      background-image: var(--desktop-bg);
    }
  }
}
@layer layout {
  main {
    flex: 1 0 100%;
    margin-inline: auto;
    max-inline-size: min(60rem, 90%);

    @media (width > 60rem) {
      display: grid;
      align-items: flex-end;
      gap: calc(var(--base-size) * 3);
      grid-template-columns: 1fr 1.5fr;
    }
  }
  article {
    border-radius: var(--base-size);
    background-color: var(--primary);
    padding: calc(var(--size-extreme) - var(--base-size));
  }
  article:first-child {
    margin-block-end: var(--base-size);
    border-top-right-radius: calc(2 * var(--size-extreme));

    @media (width > 60rem) {
      margin-block-end: 0;
    }
  }
  article ul {
    display: flex;
    gap: var(--base-size);
    margin-block-start: calc(var(--size-extreme) / 1.5);
  }
  ul li {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: var(--base-size);
    border-radius: var(--base-size);
    min-inline-size: var(--size-extreme);
    background-color: var(--primary-dark);
  }
  article:last-child {
    display: flex;
    position: relative;
    align-items: center;
    flex-direction: column;
    justify-content: center;

    @media (width > 60rem) {
      align-items: flex-start;
    }
  }
  .progress-wrapper {
    --padding: calc(var(--base-size) / 6);
    display: flex;
    min-inline-size: 100%;
    padding: var(--padding);
    margin-block: var(--base-size);
    border-radius: var(--base-size);
    min-block-size: calc(var(--base-size) + 0.125rem);
    background-color: hsl(from var(--primary-dark) h s l / 0.5);
  }
  .progress-bar {
    display: flex;
    align-items: center;
    min-inline-size: 85%;
    padding: var(--padding);
    justify-content: flex-end;
    border-radius: var(--base-size);
    min-block-size: calc(var(--base-size) - 0.125rem);
    background-image: linear-gradient(to right, var(--progress-gradient));
    span {
      display: block;
      border-radius: 50%;
      min-block-size: calc(var(--base-size) - 0.125rem);
      min-inline-size: calc(var(--base-size) - 0.125rem);
      background-color: var(--white);
    }
  }
  .storage-info {
    order: 3;
    position: absolute;
    inset: auto auto 0;
    transform: translateY(50%);
    color: var(--primary-dark);
    padding-block: var(--base-size);
    border-radius: var(--base-size);
    background-color: var(--white);
    padding-inline: calc(var(--base-size) * 2);

    span {
      letter-spacing: 10%;
      vertical-align: middle;
      text-transform: uppercase;
      color: var(--primary-gray);
      font-size: calc(var(--fs-base) * 0.875);
    }

    @media (width > 60rem) {
      order: 1;
      transform: translateY(-50%);
      border-bottom-right-radius: 0;
      inset: 0 calc(var(--size-extreme) - var(--base-size)) auto auto;

      &::before {
        width: 0;
        height: 0;
        content: '';
        position: absolute;
        border-style: solid;
        inset: auto 0 calc(var(--base-size) * -2) auto;
        border-width: var(--base-size);
        border-color: var(--white) var(--white) transparent transparent; 
      }
    }
  }
  .progress-length {
    display: flex;
    font-weight: 700;
    min-inline-size: 100%;
    justify-content: space-between;
  }
  .attribution {
    bottom: 0.5rem;
    position: absolute;
    text-align: center;
    font-size: 0.6875rem;
    color: var(--primary-light);
  }
  .attribution a {
    color: var(--white);
  }
}
```

## Author

- 👉 GitHub - [TheCoder-Rahul](https://github.com/TheCoder-Rahul)
- 👉 Frontend Mentor - [@TheCoder-Rahul](https://www.frontendmentor.io/profile/TheCoder-Rahul)
- 👉 LinkedIn - [@Rahul Kumar](https://www.linkedin.com/in/rahul-the-developer/)