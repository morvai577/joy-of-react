# Table of Contents
9. [Range Utility](#range-utility)
10. [Styling In React](#styling-in-react)

# Range Utility
A useful function, especially when you don't have an array of data to work with but still want to display multiple items.

To explain this with an example, let's say you have a website that shows movie ratings using stars. A common way to do this is to use a 5-star system. So, if a movie has a rating of 3, you want to display three stars, and if it has a rating of 5, you want to display five stars.

In the text, the author provides a code example using a function called 'range'. This function is not built into JavaScript, but it's part of utility libraries like lodash. It helps create an array of numbers from 0 to a specified number (in this case, the movie rating):

```jsx
function StarRating({ rating }) {
  return (
    <div className="star-wrapper">
      {range(rating).map((num) => (
        <img
          key={num}
          alt=""
          className="gold-star"
          src="https://sandpack-bundler.vercel.app/img/gold-star.svg"
        />
      ))}
    </div>
  );
}
```

The code example shows a function called 'StarRating' that takes a 'rating' as its input. It uses the 'range' function to create an array of numbers from 0 to the rating number. Then, it uses '.map' to loop through this array and display a star icon for each number.

For example, if the rating is 3, the 'range' function will create an array like [0, 1, 2]. The code will then display a star icon for each of these numbers, resulting in three stars being shown on the website.

This 'range' function is useful because it allows you to easily create an array of numbers from 0 to a given rating, which can then be used to display the appropriate number of stars for that rating.

# Styling In React
React doesn't force you to use a specific method for styling your components (the building blocks of your interface), so you have many options to choose from.

The main idea behind React components is that they should include everything related to that component: the structure (JSX), logic (JavaScript), and style (CSS). When you do this, it makes working with CSS a lot easier.

Many tools have been developed, such as styled-components, emotion, vanilla-extract, and stitches, which make it easier to manage styles in React projects. These tools automatically create unique selectors for your components, which ensures that your styles are scoped properly, meaning they only affect the component they belong to.

In simple terms, React provides you with more organized and efficient ways to style your components, making it easier to manage the appearance of your web application.

## Styling With CSS Modules
CSS Modules is a popular way to style React components. It's a way to write CSS that's scoped to a specific component, meaning that the styles you write won't affect other components.

React apps usually need to be compiled (converted) to make JSX code understandable by web browsers. During this compilation step, we can also manage CSS in a more organized way using tools like Webpack, which can import non-JS files like CSS modules.

When you use CSS modules in a React project, you name your CSS file with a ".module.css" extension and import it as if it was a JavaScript module. When this happens, three things occur:

1. Unique class names are generated for every CSS class in the module.
2. The CSS, with the unique class names, is added to the document's `<head>`.
3. A styles object is created, connecting the original class names to their unique alternatives.

As a result, you get an object that maps the original class names you wrote in your CSS file to their unique, generated alternatives. This ensures that each style is properly scoped to its component and doesn't affect other elements in your application.

When writing your JSX code, you can use these unique class names by referencing the styles object. This provides the benefits of naming methodologies like BEM, without the drawbacks. You don't have to manually create unique names, you don't have long class names cluttering your code, and you don't need to be extremely disciplined to follow the system. Everything is managed automatically for you.

The uniqueness of the class names is guaranteed by using the file's full path as a prefix. Since two files cannot exist in the same location, it's certain that each class will have a unique name. This makes it easier to manage styles in your React application while avoiding conflicts and simplifying the code.

Example:

`Sidenote.js`
```jsx
import styles from './Sidenote.module.css';

function Sidenote({ title, children }) {
  return (
    <aside className={styles.wrapper}>
      <h3 className={styles.title}>{title}</h3>
      <p>{children}</p>
    </aside>
  );
}

export default Sidenote;
```

`Sidenote.module.css`
```css
.wrapper {
  padding: 24px;
  background-color: hsl(210deg 55% 92%);
  border-left: 3px solid hsl(245deg 100% 60%);
  border-radius: 3px 6px 6px 3px;
}

.title {
  font-size: 1rem;
  font-weight: bold;
  margin-bottom: 4px;
}
```

In the example above, the `Sidenote` component is styled using CSS Modules. The CSS is written in a separate file, which is imported into the component. The CSS is scoped to the component, meaning that the styles won't affect other components.

The CSS file is named `Sidenote.module.css`, which is a convention that tells Webpack to treat this file as a CSS module. When the component is compiled, the CSS is converted to unique class names, which are then used in the JSX code.

The `Sidenote` component uses the `wrapper` and `title` classes, which are mapped to their unique alternatives in the 'styles' object. This ensures that the styles are scoped to the component and don't affect other elements in the application.