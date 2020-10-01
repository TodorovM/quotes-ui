# Game UI Inventory

## Description

This are searchable and sortable quotes displayed using Masonry.js

It consists of 3 main parts - the layout, the search bar and sort items

Quotes are arranged in a masonry layout and are sorted by nationality.

You can remove quote by clicking the close button on the top right

To search, just type in your search in the search bar.

Communication of the components happens through the built in EventBus in Vue

## Beforing starting

You need to start the json-server to serve the quotes

```
npm run json-server
```

## Project Scripts

### Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```
### Lints and fixes files
```
npm run lint
```

## Project Structure

``` 
- public/
    - index.html
- src/
    - assets/
        - fonts
            -silka
                - silka-regular.woff
                - silka-regular.woff2
                - silka-regularitalic.woff
                - silka-regularitalic.woff2
        - graphics
            -icons
                - arrow-down.svg
                - arrow-up.svg
                - magnifier.svg
                - quote.svg
                - x.svg
        - styles
            - _fonts.sass
            - _mixins.sass
            - _variables.sass
            - imports.sass
    - components/
        - sub-components
            - Quote.vue
            - SortBy.vue
        - Layout.vue
        - Search.vue
        - Sort.vue
    - utils/
        - eventBus.js
    - App.vue
    - main.js
- .gitignore
- babel.config.js
- db.json
- package.json
- package-lock.json
- README.md
```
