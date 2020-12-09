# CSS Grid and Flexbox with Complex Layouts

This was created as a small intro to CSS grid and Flexbox with complex layouts

## Get Started
```
git clone https://github.com/kaydc18/css-grid-flexbox.git
```
## Go through the slides

Click [here](https://docs.google.com/presentation/d/11hKhg3m0wB87o67gsO5tN0E0pdkgC_co7SDnQ9h7Nds/edit?usp=sharing)

## Build Starter Grid

Let’s create a grid! One of the best cases for Grid is being able to create a layout template.

Add the below to the html file.

```HTML
<div id="grid-container">
  <header>Header</header> 
  <menu>Sidebar</menu>
  <main>
    <div class="team-member">info</div> 
  </main>
  <footer>Footer</footer>
</div>
```

First let's set up a container that will apply the grid. Add to layout.css file.

```CSS
#grid-container {
  width: 100%;
  height: 100vh;
  display: grid;
}
```
What this does. We are establishing a container that is the full width of the screen and the entire height of the screen, 100vh = 100% of the view height

Now we dictate how many rows and columns we need.

```CSS
#grid-container {
  width: 100%;
  height: 100vh;
  display: grid;
  grid-template-rows: 50px auto 50px;
  grid-template-columns: repeat(4, 1fr);
}
```
This says our rows are going to be 50px tall, then next row is dependent on the other two, and the last row is 50px. The next section will be a column of 4 all equal sizes. You use repeat to say I want this column to repeat 4 times and have it be 1 fraction of the available space in the container.


Now let's create our areas

```css
header {
  grid-row: 1 / 2;
  grid-column: 1 / 6;
  background-color: #E02020;
  padding: 1rem;
}

main {
  margin: 0;
  grid-row: 2 / 3;
  grid-column: 2 / 6;
  background-color: #eeeeee;
}

menu {
  grid-row: 2 / 3;
  grid-column: 1 / 2;
  background-color: #000000;
  margin: 0;
}

footer {
  grid-row: 3 / 4;
  grid-column: 1 / 6;
  background-color: #E02020;
}
```
## Flexbox
Wow a layout… with nothing in it?
This is where flexbox can be added!

Now let’s update our layout!

```html
    <div id="grid-container">
      <header>
        <div class="logo">SOMELOGO</div>
        <div class="hamburg-menu"><img src="img/hamburgmenu.png"></div>
      </header> 
      <menu>
        <ul>
          <li>item 1</li>
          <li>item 2</li>
          <li>item 3</li>
        </ul>
      </menu>
      <main>
        <div class="team-member">
          name
        </div>
        <div class="team-member">
          name
        </div>
        <div class="team-member">
          name
        </div>
        <div class="team-member">
          name
        </div>
        <div class="team-member">
          name
        </div>
      </main>
      <footer>
        <p>footer info</p>
      </footer>
    </div>
```
```CSS
header {
  grid-row: 1 / 2;
  grid-column: 1 / 6;
  background-color: red;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}

main {
  margin: 0;
  grid-row: 2 / 3;
  grid-column: 2 / 6;
  background-color: #eeeeee;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
}

menu {
  grid-row: 2 / 3;
  grid-column: 1 / 2;
  background-color: #000000;
  display: inline-flex;
  justify-content: center;
  align-items: stretch;
  flex-wrap: wrap;
  margin: 0;
}

footer {
  grid-row: 3 / 4;
  grid-column: 1 / 6;
  background-color: red;
  display: flex;
  justify-content: center;
  align-items: center;
}
```
## More complexity
Wow! This doesn’t look complex at all… just you wait!

Let’s say your designer was like wow, so great, much layout, very nice.
But I want our team members to have an overlapping layout.

Now what?!
	We know we can create this kind of overlapping layout with… GRID. Remember how the child of an item doesn’t apply the previous grid? Well, that’s great because we want to slap a new grid on it.

  replace HTML
  ```html
    <div id="grid-container">
      <header>
        <div class="logo">SOMELOGO</div>
        <div class="hamburg-menu"><img src="img/hamburgmenu.png"></div>
      </header> 
      <menu>
        <ul>
          <li>item 1</li>
          <li>item 2</li>
          <li>item 3</li>
        </ul>
      </menu>
      <main>
        <div class="team-member">
          <div class="member-img">
            <img src="img/benigno-hoyuela-72zsd_fnxYc-unsplash.jpg" />
          </div>
          <div class="member-info">
            <h3>First Last</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ut odio nec orci ultrices vulputate. </p>
            <div class="button">
              View Work
            </div>
          </div>
        </div>
        <div class="team-member">
          <div class="member-img">
            <img src="img/benigno-hoyuela-72zsd_fnxYc-unsplash.jpg" />
          </div>
          <div class="member-info">
            <h3>First Last</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ut odio nec orci ultrices vulputate. </p>
            <div class="button">
              View Work
            </div>
          </div>
        </div>
        <div class="team-member">
          <div class="member-img">
            <img src="img/benigno-hoyuela-72zsd_fnxYc-unsplash.jpg" />
          </div>
          <div class="member-info">
            <h3>First Last</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ut odio nec orci ultrices vulputate. </p>
            <div class="button">
              View Work
            </div>
          </div>
        </div>
      </main>
      <footer>
        <p>footer info</p>
      </footer>
    </div>
```

Add this to the bottom

```css
.team-member {
  margin: 1rem;
  max-width: 350px;
  display: grid;
  grid-template-rows: repeat(5, 50px);
  grid-template-columns: repeat(5, 1fr);
  border: none;
}

.member-img {
  grid-row: 1 / 6;
  grid-column: 1 / 3;
}

.member-info {
  grid-row: 2 / 5;
  grid-column: 3 / 6;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: stretch;
  color: white;
  background-color: rgb(0, 0, 0, .85);
  padding: 1rem;
  border-radius: 10px;
}
```

## Make it mobile-friendly

So this... doesn't look the best on mobile right now. Lets make it a little bit better by eliminating the sidebar, and increasing the main content size.

add the ability to use media queries to the html head
```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
```

```css
@media (max-width: 768px) {
  main {
    margin: 0;
    grid-row: 2 / 3;
    grid-column: 1 / 6;
    background-color: #eeeeee;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-wrap: wrap;
  }
  
  menu {
   display: none;
  }
}
```