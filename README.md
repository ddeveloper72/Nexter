<link href="https://github.com/ddeveloper72/Nexter/blob/master/css/markdown.css"rel="stylesheet"></link>

# Advanced CSS tutorial

## [Nexter](https://ddeveloper72.github.io/Nexter/)

  _from a Udemy tutorial presented by [Jonas Schmedtmann](https://github.com/jonasschmedtmann)_

## Preface

In this tutorial, I'm looking for ways in which to improve and expand on my experience in front-end development.  I love the platforms that I've been working on before, namely Django and Angular along with all the backend services and deployment processes and I believe that the look and feel of these applications can be vastly improved by the better use of advanced CSS.  

In this tutorial Jonas introduces CSS grid and he combines it with flexbox for the finer elements of this purely frontend website.

CSS grid makes this site beautifully responsive straight out of the box.  This tutorial used the desktop first approach.  It used a pre-build site as the wire-frame and then worked to build a visually similar one page site.

![Welcome](https://github.com/ddeveloper72/Nexter/blob/master/img/git/header.png "Desktop view")

The project begins with building out the basic html mark-up.

HTML Mark-up:

````html
<body class="container">
        <div class="sidebar">
            Sidebar
        </div>
        <div class="header">
            Header
        </div>
        <div class="realtors">
            Top 3 realtors
        </div>
        <div class="features">
            Features
        </div>
        <div class="story__pictures">
            Story pictures
        </div>
        <div class="story__content">
            Story content
        </div>
        <section class="homes">
            Homes
        </section>
        <section class="gallery">
            Gallery
        </section>
        <footer class="footer">
            Footer
        </footer>
    </body>
````

The project then sass files for each of the sections above, which provides better management of the SASS build.

One of the many benefits of using CSS grid, is that one can name the grid column and row elements of the grid.  This helps better mental visualization of the grid and so speeds up development.

This is an example of what I mean.

````css

container {
    display: grid;
    grid-template-rows: 80vh min-content 40vw repeat(3, min-content);
    grid-template-columns: [sidebar-start] 8rem [sidebar-end full-start] minmax(6rem, 1fr) [center-start] repeat(8, [col-start] minmax(min-content, 14rem) [col-end]) [center-end] minmax(6rem, 1fr) [full-end];

````

Below is a visual representation of the above.  The page is made up of 12 columns; 4 explicit rows and 2 implicit rows, the latter resize automatically based on their content.

<table>
<thead>
    <tr>
        <thc colspan="12">Grid Names</th>
    </tr>
</thead>
<tbody>
    <tr>
        <td></td>
        <td>[sidebar-start]</td>
        <td>[sidebar-end full-start]</td>
        <td colspan="8">[center-start col-start]</td>
        <td colspan="2">[col-end center-end]</td>                
        <td>[full-end]</td>
    </tr>
    <tr>
        <td>Col/Row Size</td>
        <td>8rem</td>
        <td>6rem, 1fr</td>
        <td colspan="10">Each column width is min-content, 14rem</td>
        <td>6rem, 1fr</td>
    </tr>
    <tr>
        <td>80vh min-content</td>
        <td>sidebar</td>
        <td colspan="9">header</td>
        <td colspan=3>realtor</td>
    </tr>
    <tr>
        <td>40vw min-content</td>
        <td>sidebar</td>
        <td colspan="12">feature</td>
    </tr>
    <tr>
        <td>40vw min-content</td>
        <td>sidebar</td>
        <td colspan="6">story pic</td>
        <td colspan="6">story txt</td>
    </tr>
    <tr>
        <td>40vw min-content</td>
        <td>sidebar</td>
        <td colspan="12">homes</td>
    </tr>
    <tr>
        <td></td>
        <td>sidebar</td>
        <td colspan="12">gallery</td>        
    </tr>
    <tr>
        <td></td>
        <td>sidebar</td>
        <td colspan="12">footer</td>
    </tr>
</tbod>
</table>

## Demonstration of the features CSS grid mark-up

The features grid class makes use of the column naming principle use in the table above.

````css

.features {
  // column names are used instead of numerical representation of the column
    grid-column: center-start / center-end;

    // defining the column size withing the container grid.
    grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
    grid-gap: 6rem;
    align-items: start;
}

````

This is the outcome:

![Features](https://github.com/ddeveloper72/Nexter/blob/master/img/git/features.png "Desktop view")
![Features](https://github.com/ddeveloper72/Nexter/blob/master/img/git/features-ipad.png "Ipad view")
![Features](https://github.com/ddeveloper72/Nexter/blob/master/img/git/features-iphone7.png "Iphone6/7 view")

## Demonstration of the homes CSS grid mark-up

This section is broken up into 3 columns, the spacing provided by row-gutters. The each home is broken into further columns and rows, primarily 2 columns and 5 rows.

This is the home class:

````css

.homes {
    grid-column: center-start / center-end;
    margin: 15rem 0;

    display: grid;
    // defined a dynamic column size
    grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
    grid-gap: 7rem;
}

````

The content of this container is then further divided into another grid to contain the separate grid elements.  styles have been remove to just show the method of grid naming for placement of the grid elements.

````css

.home {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-row-gap: 3.5rem;
    // styling removed

    &__img {

        // defined row location for img grid element
        grid-row: 1 / 2;
        grid-column: 1 / -1;
        // styling removed
    }

    &__like {
        // define row position of svg grid element
        grid-row: 1 / 2;
        grid-column: 2 / 3;
        // styling removed

    }

    &__name {

        // move the name grid item to the top row
        grid-row: 1 / 2;
        grid-column: 1 / -1;
        // styling removed

    }

    &__location,
    &__rooms {
        // styling removed
    }

    &__location,
    &__rooms,
    &__area,
    &__price {
        // use flexbox to align the smaller items
        display: flex;
        align-items: center;
        // styling removed

        svg {
            // styling removed
        }

    }

    &__btn {
        grid-column: 1 / -1;
    }

}

````

## summary

CSS grid and Flexbox are powerful tools for any front-end, full stack developer to have available to them.  

The Advanced CSS course is a great way to learn the basics of writing SASS as well as more advanced CSS features.  There is a good deal of work gone into using NPM tools to run scripts from your package.json 

The scripts are written to let one run a local instance of SASS watch, SASS compile, which is a great if one wants to demonstrate and alternative SASS watch tool to what is available with VSCode.  One is also shown how to write browser tests from within the SASS code as well as make use autoprefixer such that the CSS code will be made compatible with older browsers.

Remember to Practice Practice Practice! 🚀
Happy Coding
