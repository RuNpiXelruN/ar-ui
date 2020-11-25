# Audience Republic UI styling assessment
This repo contains my solution to the css/styling assessment for Audience Republic.  

Some points to note re the solution,  
- I decided to make the header/search section fixed on desktop and portrait iPad.  
My thoughts behind this were that in production, should there be more than nine events at some point it would be nice to be able to search at any point on the page and not have to scroll back to the top.  
- The fixed header section was reverted for landscape iPad and mobile as I felt it consumed too much real estate and had a negative impact on UX.  
- The green caret/cursor for the input field is taller in the designs than is possible once built. It's height is determined by the font-size which in our case is 14px.  
- An escape key listener was added to the event cards to close the menu and improve accessibility.  

### Setup
git clone this repository and exeucute the below to install dependencies
```
yarn install
```

### To start the development server execute the below and visit `localhost:8080`
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```
