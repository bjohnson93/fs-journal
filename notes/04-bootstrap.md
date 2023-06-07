# Bootstrap

a css architectural library
  really good documentation, which is why its preferred

bootstrap grid system
  start with "container" - holds all grids within
  rows go in containers- all rows in bootstrap are flexbox containers
  *put row class on div for flexbox (multiple rows in containers)
  12 units of space for columns in each row
  col-1-you can have 12 columns- you can have 12 in a row col-6 you can have 2 even spaced columns
  each column can hold its own html
  2 col-4s, use justify on row and it spaces them out evenly; add col-12 in same row, it will go below col-4's

breakpoints similar to media queries (col-md-4 col-12 means column 4's on medium screens, otherwise anything under that is col-12)
  *col's are class names on your divs

container>row>col

make things disappear when go to mobile**
Use section tags for rows
no columns in column/rows in rows/containers in containers

<!-- Bootstrap utility classes -->
linktag for bootstrap: link:bs5
style:debug put in between head and body (will outline containers blue/red/green) *body class="debug" to make this work

.col-3 and hit enter- quickly makes you div with col-3 class
hit . and information, adds class to div 

<p class="m-4"> bootstrap margin class
m-s margin start
m-e margin end
container-fluid makes it so there's no margin on sides of container

<!-- steps -->
link in your bootstrap
<header class="container">, 
  <section class="row">, 
    <div class="col-6">
    <div class="col-2">
    <div class="col-2">
    <div class="col-2">
    

main, footer

justify-content-between on row, you can add class of and it evenly spaces them between
justify content center, centers all the columns within a row

d-flex is bootstraps class for display-flex

justify content on x axis- which is horizontal

<p class="m-4"> bootstrap margin class
m-s margin start
m-e margin end

container-fluid makes it so there's no margin on sides of container