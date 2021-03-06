- Start point: Remember basic html structure

  <DOCTYPE! <!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>Page Title</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" type="text/css" media="screen" href="main.css" />
  <script src="main.js"></script>
</head>
<body>
  
</body>
</html>

or more simply

<!DOCTYPE html>
<head>
  <!-- meta info goes here -->
</head>
<body>
  <!-- Content goes here -->
</body>

- Header: <header> a container that holds website's header

- Navigation: list of links
  1) use <ul> for nav bar
  2) Inside of <ul> use list item <li> tag for each link in our nav bar

- Nav bar li needs to be link
  <a> tag with attribute href, controls URL your browser opens when clicking the link on the page.
  <a href="http://www.google.com">Google</a>
  - when we don't know the exact URL yet, we use # (hash) for place holder.  

- Phase 2: 
1) Add CSS reset ext CSS file
2) Style the nav links
3) Style the reset of the header

- 1) Add CSS reset ext CSS file
We already know <style> is one way to include CSS into HTML.  Next, CSS can be included via <link> tag which is external css file.

  * link tag must have 2 things:
    1) href - a URL where the CSS file lives
    2) rel - which should always be set to "stylesheet"
    ex) 
    <link href="http://dash.ga.co/normalize.css" rel="stylesheet">
    - good to always include normalize.css to all web project.

  - by default browser gives some padding to list bullets points which makes links off-center!  We may fix this by using padding property to set 10px of padding on all sides.  As a default, bullet points are part of 40 px padding only left for ul padding.  By giving 10px you move the bullet off the screen and center the ul element.
    ul {
      /* fixing the list nav links be centered */
      padding: 10px; 
    }

    <ul>
      <li><a href="#">About Me</a></li>
      <li><a href="#">Best Poems</a></li>
      <li><a href="#">Worst Poems</a></li>
    </ul>
- Make list to look horizontal
  li {
    display: inline;
  }
  display usu. two types: block or inline.
  * block: stretch whole width of the page
  * inline: <a> is by default display inline. element exist within the normal flow of the text they're contained within - no line breaks, no taking up the whole width of the page.

  * giving links some breathing room:
    li {
      display: inline;
      padding: 0px 10px 0 10px;
    }

- Header style
  header {
    text-align: center;
    background: url("http://dash.ga.co/assets/jeff-bg.png");
    background-size: cover;
  }

- if you want to style links color; you must explicitly set it to the color; unlike heading or paragraph tag; it won't inherit from its parent element.
  a {
    color: white;
  }

- padding (inside) vs margin (outside)

- border CSS to have white border with rounded edges! prop short hand for border-width, border-style, and border-color.
  border: 7px solid white;
  border-radius: 20px;

- Lesson 3:
  1) Give the content a responsive design
  2) Learn about advanced colors
  3) Make our own "like" button in Javascript

- 1) Give the content a responsive design
 * give your site response to different device width gracefully
 first focus on restructuring the site
 - Wrap <article> around each blog post, lets group together multiple HTML elements that forms a single piece of content.

  ex) 
  <article>
    <h2>Succulents freegan vegan letterpress brunch chambray</h2>
      <p>Typewriter synth sustainable enamel pin schlitz fashion axe. Disrupt put a bird on it etsy tofu whatever next level occupy photo booth subway tile synth VHS wayfarers man bun. Meditation echo park cardigan photo booth portland, fanny pack neutra authentic pickled. Lumbersexual actually before they sold out yuccie tousled, retro gluten-free wolf bicycle rights.</p>
  </article>

- Article stretches out too much; narrower, center
(easier to read)

- Center content hack: adding margin 0 auto center my blog.  Margin controls space btwn outside of an element and other elements around it.  When setting 0 auto, 0 margin top/bottom, auto left/right.  Auto means margin stretches all the way to the edge of the page.
  article {
    width: 500px;
    padding: 20px;
    margin: 0 auto; // centers content
  }

!! very useful !! remember margin: 0 auto trick!!

- responsive trick: 
1) content width update width: 500px; to max-width: 500px;
  - Using max-width: instead of width means article elements can be smaller than 500px, but not any larger.

2) nav bar and title looks so squished when browser window is really small.
  * fix using media query, a technique allows CSS styles that only activate when the browser is a certain width.

  /* if browser window smaller than 500px - apply condition */
    @media (max-width: 500px) { // this is setting a condition - when browser is smaller than 500px, if true; activate CSS inside!
      body {
        background: red;
      }
    }

3) Style: Make the page look better at narrower width (mobile devices)
  Few things when things are smaller (mobile screen):
    1) Heading should be smaller!
    
    2) Nav links should sit on top of each other (display: block), rather than horizontally (display: inline)

      ex) 
      // smaller screen
      @media (max-width: 500px) {
        h1 { //Heading should be smaller!
          font-size: 36px; //
        }
        li { //stack nav bar vertical
          display: block;
          padding: 5px;
        }
      }

## learn git 101
mnelson:Desktop mnelson$ cd ~/Desktop
mnelson:Desktop mnelson$ mkdir myproject
mnelson:Desktop mnelson$ cd myproject/

> ls -la // see the detail hidden folders like .git

- Anatomy of Hex color code:
ex) #F00
1) always starts with #
2) first Character controls the amount of redness. It ranges from 0(no red at all) to F(100% red).
3) second Character controls the amount of green. 0 to F
4) third Char controls amount of blue.  0 to F
- TOGETHER RGB!!!  Hex work by "mix" of 3 primary colors!

#000 black (no color)
#FFF white (All color present)

#F00 RED (100 R, 0 G, 0 B)
- rgba() add alpha (transparency) to the mix!

background: rgba(0, 0, 0, 0.5);
// black with 50% opacity

- RGBA color with transparency
rgba(255, 255, 255, 1) // white color (presence of all color)
Instead of 0-F scale RGB, RGBA use 0-255 with A transparency 0-1 scale. 

## Like button using JavaScript!! Make webpage interactive
* it won't save data (we need back-end server such as frameworks like Ruby on Rails to save things)
- Goal: a button that reacts when clicked!!
  1) make button HTML
    <button>Like</button>
  2) Add JS to HTML directly <script> tag
    * Add <script></script> at the bottom, just above </body> tag

  3) Add popup alert when pg loads:
    * Every time you move your mouse, click something, mouse over something, press a key or scroll, your browser fires off an event.
    * By default, these events go unnoticed.  But we can use JavaScript to listen for specific events and take action when they happen.  EX) listen for click even on Like button element!!

- Here ex JS that would listen for a click event on a button element: Note: using jQuery (pop lib makes it easy to select elements and listen for events)

  1) add jQuery CDN from google https://developers.google.com/speed/libraries/#jquery: <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

  2) Add this inside of script tag separate
  $("button").on("click", function() {
    alert("clicked!")
  });

  - How jQuery works?
    1) $ proceeds
    $("button") select button, selector goes inside of quotes and parentheses $ left of it
    - $("p") paragraph
    - $("h1") headings
    2) call the function ex) on(), which set up an event listener for our button element.
    .on( -- here put 2 options (parameters or arguments -- ))

    * basic format: $(element).on(event-type, thing-to-be-done);
    ex) $(element).on("click", function() {
          alert("A button was clicked!")
        });

    * Breakdown how JS click event alert function:
      - The first parameter: type of event to listen to.
      In this case: "click", but we could also listen for hover, scroll, etc. It must be in quotes!
      The reason why it must be in "" is ITs' a String!
      data type: string (other data types: numbers, lists, functions)

      - Second parameter: Function (group together chunks of code and allow them to be executed at a later time.)
        ex) 
        function () {
          alert("I got clicked!")
        }

  - Summary:
  $("button").on("click", function() {
    alert("Button clicked!")
  });
  - $("button)
  The selector chooses the element to listen to.
  - .on
  the .on() function sets up an event listener for the element we selected.
  - "click"
  Type of event we listen for
  - function() { - some action - }
  Some action to take when event occurs!

  1) max-width and @media queries for responsive design
    1) content width update width: 500px; to max-width: 500px;
      - Using max-width: instead of width means article elements can be smaller than 500px, but not any larger.
    article {
      max-width: 500px;
      padding: 20px;
      /* centers the article top,bottom 0, width auto */
      margin: 0 auto;
    }

    /* if browser window smaller than 500px - apply condition */
    @media (max-width: 500px) {
      /* heading should be smaller in small screen */
      h1 {
        font-size: 36px;
      }
      /* stack nav bar vertical */
      li {
        display: block;
        padding: 5px;
      }
    }

  2) hex rgba colors (a is for transparency)
  3) listen for events an react with JS/Jquery

  - final version: https://dash.generalassemb.ly/projects/build-your-own-blog-theme