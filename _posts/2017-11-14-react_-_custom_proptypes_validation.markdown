---
layout: post
title:      "React - Custom PropTypes Validation"
date:       2017-11-14 17:57:21 +0000
permalink:  react_-_custom_proptypes_validation
---


Alright, let's get straight to it. I found the React documentation on this topic a bit intimidating/sparse, so I'll try to walk through a straightforward example here.

So let's say we have the following file with a Movie component:

```
import React from 'react';
import PropTypes from 'prop-types';

class Movie extends React.Component {
  render() {
      return(
        <div>
          <h3>{this.props.title}</h3>
          <ul>
            <li>Producer: {this.props.releaseYear}</li>
            <li>Genre: {this.props.genre}</li>
          </ul>
        </div>
      );
    )
  }
}

Movie.propTypes = {
  title: PropTypes.string.isRequired,
  releaseYear: PropTypes.number,
  genre: ???
}

export default Movie;
```


We want to check a few conditions for our genre prop:
1. is present
2. is a string
3. doesn't start with a 'R' (just a totally random letter...)

First, let's stub out our validation function. Sure, we could just do it anonymously, but in this context I think it feels a bit cleaner explicitly defined.


```
const validateGenre = () => {

}

Product.propTypes = {
  title: PropTypes.string.isRequired,
  releaseYear: PropTypes.number,
  genre: validateGenre
}
``` 


Next we will want to define 2 to 3 parameters: props (the props values we render with), propName (i.e. genre), and componentName (i.e. Movie). That last one (componentName) is optional because it doesn't affect our functionality here and probably isn't necessary in such a simple context, but it becomes important for clarity and flexibility in an actual codebase. Let's go ahead and add some psuedocode for our conditions while we're at it.


```
const validateGenre = (props, propName, componentName) => {
    // check that genre is defined
	// check that genre is a string
	// check that genre doesn't start with a 'R'
}
```


Before we can test our conditions, we need to actually define the value we're testing them on! Using our local props and propName variables we can get our genre value and store it:


```
const validateGenre = (props, propName, componentName) => {
  
	const genreValue = props[propName];

    // check that genre is defined
	// check that genre is a string
	// check that genre doesn't start with a 'R'
}
```


Now we want to translate each of our genre conditions into individual tests in our custom function. First up is just ensuring a genre was given. It might be tempting to do something like `if (genreValue)`, but that could lead to some unexpected bugs since there are a number of things that evaluate to false in JavaScript (like 0 if we want to test numbers). Instead let's just check for an undefined value. The goal with our validator is to catch errors, so we want to test *for* the failed condition:


```
const validateGenre = (props, propName, componentName) => {
  
	const genreValue = props[propName];

    if (genreValue === undefined) {

    }
	
	// check that genre is a string
	// check that genre doesn't start with a 'R'
}
```

We'll finish our conditional statements, then circle back to what goes inside. Next we want to check that the type of the value is a string, then we'll want to check and see if the first letter is an "R" (being sure to handle upper and lowercase). Pretty straightforward JavaScript fundamentals.

```
const validateGenre = (props, propName, componentName) => {
  
	const genreValue = props[propName];

    if (genreValue === undefined) {

    }
	
	if (typeof genreValue !== "string") {
	
	}
	
	if (genreValue.toLowerCase()[0] === "r") {
	
	}
}
```


Cool, so now we just need to figure out what to actually put inside our conditionals. The goal of our validator is to return an error if our value doesn't satisfy a particular condition, so we want to return an error in each case. Here is where including that third argument could be helpful, as it allows us to provide more descriptive error messages and point to the component we're testing. After implementing this, we'll wind up with something like this:


```
const validateGenre = (props, propName, componentName) => {
  
	const genreValue = props[propName];

    if (genreValue === undefined) {
      return new Error(propName + ' is undefined in ' + componentName);
    }
	
	if (typeof genreValue !== "string") {
	  return new Error(propName + ' is not a string in ' + componentName);
	}
	
	if (genreValue.toLowerCase()[0] === "r") {
	  return new Error(propName + " begins with the letter 'R' in " + componentName);
	}
}
```


And there you have it! You can test it out for yourself and trigger the different errors (these will appear in your console if you run `npm install && npm start` in your root directory), and everything looks good. Like I said, it really is pretty simple! The tricky part, for me at least, was just understanding what I was trying to do (return errors) and what arguments my validation function has access to.

Also note that we tried to avoid hard coding when possible: you could call `props.genre` instead of using the `props[propName]`, and you could hard code the full error message, but that's pointlessly brittle. We might just be using our function for this specific component/prop for now, but flexibility (within reason) is always better. I probably could've abstracted the third test out further in this spirit actually, but you get the idea.

Here is the final result for reference:


```
import React from 'react';
import PropTypes from 'prop-types';

class Movie extends React.Component {
  render() {
      return(
        <div>
          <h3>{this.props.title}</h3>
          <ul>
            <li>Producer: {this.props.releaseYear}</li>
            <li>Genre: {this.props.genre}</li>
          </ul>
        </div>
      );
    )
  }
}

const validateGenre = (props, propName, componentName) => {
  
	const genreValue = props[propName];

    if (genreValue === undefined) {
      return new Error(propName + ' is undefined in ' + componentName);
    }
	
	if (typeof genreValue !== "string") {
	  return new Error(propName + ' is not a string in ' + componentName);
	}
	
	if (genreValue.toLowerCase()[0] === "r") {
	  return new Error(propName + " begins with the letter 'R' in " + componentName);
	}
}

Movie.propTypes = {
  title: PropTypes.string.isRequired,
  releaseYear: PropTypes.number,
  genre: validateGenre
}

export default Movie;
```


Hopefully this was helpful, happy coding! I'm going to go not watch a Rom-Com...
