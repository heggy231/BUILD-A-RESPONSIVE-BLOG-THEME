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

  