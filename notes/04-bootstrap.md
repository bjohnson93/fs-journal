# Bootstrap

CODE SNIPPET linktag for bootstrap: link:bs5
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

**REVIEW - breakpoints similar to media queries (col-md-4 col-12 means column 4's on medium screens, otherwise anything under that is col-12)
  *col's are class names on your divs

container>row>col

make things disappear when go to mobile**
Use section tags for rows
no columns in column/rows in rows/containers in containers

dont put margin on x axis of any columns

<!-- Bootstrap utility classes -->
CODE SNIPPET linktag for bootstrap: link:bs5
style:debug put in between head and body (will outline containers blue/red/green) *body class="debug" to make this work

.col-3 and hit enter- quickly makes you div with col-3 class
hit . and information, adds class to div 

<p class="m-4"> bootstrap margin class
m-s margin start
m-e margin end
container-fluid makes it so there's no margin on sides of container

bg-primary   is a blue, applies background color via class to the row
text-light applies color to text via a class to the <p>tag</p>

p-(number between 1-5) adds padding

fs-(#between 1 and 5) stands for fontsize

pe-4 (padding end) padding on right side

fw-bold for font weight

col-12 col-md-6  (tells it to be col12 unless its medium or above)

 d-none says no longer display
  d-md-block medium devices and above are as block
container-fluid for edge to edge

fs-1 for font size (largest)
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

change background color of whole row by .bg-primary
change text color to p tag i(or div) tself-f text-light

bootstrap needs to come in before css link

add padding- p-(number betwen 1-5)- 

change font size (fs-(1-5))

dont like how menu options are on top at right- change by "align-items-center"; find d-flex, "justify-content-end"- 

Remember to use justify on display flex!!

padding on right side pe-4 (padding end)

mb-3 margin bottom 3 pts

py-5 to y axis padding

section.row gives class of row to section

sticky-top class to header makes the head stick to top during scroll, as its direct parent is the body

.col-12+enter creates div with class shortcut

img-fluid, img only allowed to fit in column; can't spill outside of column

rounded class- border radius in bootstrap

.col-6*2 makes to column sixes on divs!

ps-5 is padding Start (left)

btn class on button makes look more new, many diff btn values/classes

pe-0 pe-md-5 would apply padding to medium and above and remove padding to small scrn

<!-- checkpoint requirement below -->
*Make things disappear(menu items)  available breakpoints section on bootstrap; 
  make col6 col-12,   col-12 col-md-6  (tells it to be col12 unless its medium or above)
  d-none says no longer display
  d-md-block medium devices and above are as block
not compatible with d-flex, put d-flex in child div
order doesn't necessarily matter, but its good practive to put default first, conditionals after


main is whole container (container-fluid for edge to edge)
  separate rows for each background change (<sections>)
<!-- #SECTION -  -->
hero sections is big thing on top of webpage
<main class="container-fluid">
  <section class="row">
    <div class="col-12"> 
      <img class="hero-image">  max-height: 40vh;
add text-center to col-12 to center image
add h1
i tag w/class mdi mdi-star for material design icons
add link in material design icons 
resize icon by fs-1
give bg color for section in class
test under icon in p tag
bump up font size in p tag fs-2
add padding to section row py-5 to y axis
margin on bottom image- image class mb-3

bootstrap grid system to lay out webpage biggest concern rn

dont put margin on columns on x axis, but ok to marginate on bootstrap otherwise, y axis is gen safe

<!-- #SECTION -  -->

next section
  section.row gives class of row to section
add h2 and i icon, 
add padding to y axis to space out from top with py-#

need 3 elements stacked next to each other
.col-4 +enter to create, 
add img tag
img too large? bootstrap utility class says to not spill outside img-fluid, img only allowed to fit in column
if you add padding to img fluid will it resize the img or add padding to column
border radius in bootstrap- add rounded class
3 img across col-12 col-md-6 col-lg-4

<!-- #SECTION -  -->

col 12/6/12
.col-6*2 makes to column sixes on divs!
add text-cent to dive and padding to y axis py-5
make fontsize larger again fs-1
p tags x 2 col6
add padding to col itself ps-5, pe-5 to right one
add button free download, 
<button>
  <i class="mdi mdi-tray-arrow-down"></i>
  Free download!
</button>
add text center and padding to y axis on div for button
add bootstrap button class btn btn-
change background of section
text light to section/row
light color button with btn-light
fs-2 to button class
btn-outline-light>>when you hover it goes to solid white
more padding inside row py-5

change p tag col-12 col-md-6 to div classes for responsive
pe-0 pe-md-5 to remove padding for small scrn and add padding for md and above

<!-- #SECTION contact -->

section.row
.col-12
form column 12
<section class="row">
  <div class=" col-12 text-center">
    <h2>Contact us</h2>
    <i class="mdi mdi-star"></i>
  </div>
</section>
form- get from bootstrap
  floating labels
put form under contact us div

form is huge- add padding- css class form-section{padding: 0 30vw}
form col-12 col-md-5
add justify-content-center to section tag

add margin to y axis my-5 to div
bg-secondary to give different background on form
p-4 to add padding

change col-md-6 and add rounded class

add floating label to form for comments section

add button btn btn-success submit

<!-- #!SECTION Social Media -->

section.row
four icons div d-flex puts them next to each other

icons small - fs-2 to enlarge, 
justify content around to space out 

link in html, a tag <a href=""></a> creates hyperlink

check responsiveness

<!-- #!SECTION footer -->

footer container fluid 
div row py3 bg black
div col12 text center text light
p tag with text

#REVIEW - 
swap placement of divs; order-2 order-me-1 on 1st element, order-1 order-md-2 on 2nd element for 1st, order-3 for div


<!-- #!SECTION pet peeve -->
#REVIEW - 
take style debug out for check, take off body class debug

#REVIEW - 
Breakpoint