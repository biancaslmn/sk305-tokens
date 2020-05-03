# Sketch+Fajitas - Tokens
Workshop on Design Tokens and how designers and developers can share the same source of design decision tokens for Sketch symbols and Web Components.

## In this session you will learn:

1. What are Design tokens?
2. Why tokens are crucial for design systems?
3. How we can create/import Tokens in Sketch
4. How to use Puzzle Tokens plugin for creating hundreds of Sketch Styles dynamically.
5. How to become your developer best friend 🤩

## Design Tokens are awesome!
As teams increase the maturity level of a product, they tend to find ways for becoming more efficient, by minimizing redundancies and abstracting layers towards better productivity.

Design Tokens is an abstracted layer from typical stylesheets containing at least colors and typography decisions for the user interface.

### Why Design Tokens?
A token is the smallest decision anyone can make when designing and developing the user interface of a product.

**These UI decisions must be shared and maintained.**

> **Design Tokens** allow teams to have a **single source of truth** for the presentation layer.

## Tokens as source of truth
In this workshop, we will design and develop a **button** component  

### Getting Started
This repository was created with cross-functional teams in mind, where product designers and developers work closely, collaborating on user interaction design and development.    

In order to use the method presented in the workshop, you will need to follow the instructions below:

#### For Designers
This method requires the **PuzzleTokens** Sketch plugin to specify and apply design tokens to Sketch layers through shared styles.

1. Download and install [PuzzleTokens](https://github.com/ingrammicro/puzzle-tokens/raw/master/PuzzleTokens.sketchplugin.zip)
2. Download and install [Node.js](https://nodejs.org/en/download/)
3. Then install `LESS` or `SASS` stylesheets pre-processors. this will allow Sketch to read and process the token file and create the styles dynamically. Use the following **Terminal** commands:

```
sudo -s
npm i less -g
npm i sass -g
```

Now you're good to go!

#### For Developers

For this workshop, we will be leveraging the following packages for showcasing the web development side:  

- `GULP` [gulpjs.com](https://gulpjs.com/) - a cross-platform, streaming task runner that lets developers automate many development tasks.
- `PUG` [pugjs.org](https://pugjs.org/) - a simple HTML templating language for coding reusable HTML.

Please refer to the [developers](developers.md) instructions for installing the necessary packages.


## Credits
Thanks to [Andrey Gorokhov](https://github.com/andreyalexeich) for the amazing [Gulp Pug Starter](https://github.com/andreyalexeich/gulp-pug-starter) we used to showcase our web development examples.
