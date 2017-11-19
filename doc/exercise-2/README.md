# Exercise 2 - Navigation

In this exercise, we will create the navigation bar and split the style in to 2 different files:

![Design website personal - About Me](../../img/personal-website-menu.png)

## Step 1 - Remove margin

Remove top margin from `.pagegrid` to allow navigation bar to take it's place:

```css
.page-grid {
    margin: 0;
}
```

## Step 2 - Create navigation bar

Use the following markup to define the navigation bar:

```html
<nav class="menu">
    <a class="menu-item menu-item-active" href="index.html"><i class="fa fa-user"></i> About me</a>
    <a class="menu-item" href="resume.html"><i class="fa fa-file-text"></i> Resume</a>
    <a class="menu-item" href="portfolio.html"><i class="fa fa-heart"></i> Portfolio</a>
    <a class="menu-item" href="contact.html"><i class="fa fa-envelope"></i> Contact</a>
</nav>
```

Then apply the following styles:

```css
.menu {
    width: 990px;
    margin: 80px auto 0 auto;
    text-align: center;
}
.menu-item {
    display: inline-block;
    margin-right: 10px;
    margin-top: 20px;
    padding: 10px 40px 10px 40px;
    background: white;
    text-decoration: none;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 14px;
    outline: none;
    color: #888;
    vertical-align: bottom;
}
.menu-item-active {
    position: relative;
    bottom: -1px;
    color: #c0392b;
    padding: 15px 40px 15px 40px;
    margin-top: 0;
}
```

## Step 3 - Responsive

Let's add or modify some css rules to make look good on all devices:

```css
@media (max-width: 990px) {
    .menu {
        width: 100%;
    }
}

@media (max-width: 768px) {
    .menu {
        margin: 0;
    }
    .menu-item {
        display: block;
        margin: 0;
        padding: 15px 40px 15px 40px;
        border-top: 1px solid #ccc;
    }
    .menu-item-active {
        position: static;
        margin: 0;
        padding: 15px 40px 15px 40px;
    }
}
```

## Step 4 - Split CSS style into different files

Let's create `about-style.css` and paste all *About* page related styles:

```css
.about-content {
    grid-area: about-content;
    background: white;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 20px;
    grid-template-rows: 1fr fit-content;
    grid-template-areas:
        "my-avatar my-info my-list"
        "my-social my-social my-social";
    padding: 30px 20px;
    border: 1px solid #f1f1f1;
    box-shadow: 0px 6px #c0392b;
    border-radius: 0px 0px 4px 4px;
}

.my-avatar {
    grid-area: my-avatar;
    justify-self: center;
    align-self: center;
}

.my-info {
    grid-area: my-info;
}

.my-list {
    grid-area: my-list;
}

.my-social {
    grid-area: my-social;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 20px;
}

.my-social-item {
    display: grid;
    grid-template-columns: 45px 1fr ;
    grid-template-rows: 45px fit-content;
    grid-template-areas:
        "my-icon my-icon-title"
        "my-icon my-icon-subtitle";
    padding: 6px 6px 6px 10px;
    border: 1px solid #f1f1f1;
    border-radius: 4px;
}

.my-icon {
    grid-area: my-icon;
    font-size: 40px;
    align-self: center;
    justify-self: left;
}

.my-icon-title {
    grid-area: my-icon-title;
    text-decoration: none;
    color: #E74C3C;
    font-weight: 700;
}

.my-icon-subtitle {
    grid-area: my-icon-subtitle;
    color: #999;
    font-size: 12px;
    margin: 5px 0 0 0;
}

.my-info-title {
    margin: 0;
    font-size: 38px;
    font-weight: 700;
    text-transform: uppercase;
}

.my-info-subtitle {
    color: #999;
    font-size: 1.5em;
    line-height: 1em;
    margin: 0 0 1em 0;
}

.my-info-content {
    margin: 0;
    font-size: 1em;
    line-height: 1.5em;
    margin-bottom: 0;
}

.my-list {
    margin: 0 0 0 20px;
    padding-left: 20px;
    list-style-type: none;
    border-left: 1px solid #f1f1f1;
    align-self: center;
}
.my-list-item {
    padding: 10px 0;
    border-bottom: 1px solid #f1f1f1;
}

.my-list-link {
    color: #c0392b;
    text-decoration: none;
}


@media (max-width: 990px) {
    .my-list {
        display: none;
    }
    .about-content {
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr fit-content;
        grid-template-areas:
            "my-avatar my-info"
            "my-social my-social";
        border-radius: 0;
    }
}

@media (max-width: 768px) {
    .about-content {
        display: block;
    }
    .my-avatar {
        display: block;
        margin: 0 auto;
    }
    .my-info-title {
        margin-top: 15px;
        text-align: center;
    }
    .my-info-subtitle {
        text-align: center;
    }
    .my-social {
        display: block;
    }
    .my-social-item {
        margin-top:10px;
    }
}
```

The styles who are still remaining into `style.css`:

```css
html {
    font-family: 'Open Sans', sans-serif;
    color: #555;
}

body {
    background: url('../../img/background.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center center;
    background-size: cover;
}

.page-grid {
    margin: 0;
    display: grid;
    grid-template-columns: 1fr 990px 1fr;
    grid-template-rows: fit-content fit-content;
    grid-template-areas:
        ". about-content ."
        ". footer .";
}

.footer {
    grid-area: footer;
    margin-top: 30px;
    background: white;
    text-align: center;
    padding: 15px;
    box-shadow: 0px 4px #ccc;
    border-radius: 4px;
}

.copyright {
    margin: 0;
}

.menu {
    width: 990px;
    margin: 80px auto 0 auto;
    text-align: center;
}
.menu-item {
    display: inline-block;
    margin-right: 10px;
    margin-top: 20px;
    padding: 10px 40px 10px 40px;
    background: white;
    text-decoration: none;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 14px;
    outline: none;
    color: #888;
    vertical-align: bottom;
}
.menu-item-active {
    position: relative;
    bottom: -1px;
    color: #c0392b;
    padding: 15px 40px 15px 40px;
    margin-top: 0;
}


@media (max-width: 990px) {
    .menu {
        width: 100%;
    }
    .page-grid {
        display: block;
    }
    .footer {
        border-radius: 0;
    }
}

@media (max-width: 768px) {
    body {
        background: none;
    }
    .menu {
        margin: 0;
    }
    .menu-item {
        display: block;
        margin: 0;
        padding: 15px 40px 15px 40px;
        border-top: 1px solid #ccc;
    }
    .menu-item-active {
        position: static;
        margin: 0;
        padding: 15px 40px 15px 40px;
    }
    .footer {
        margin-top: 3px;
    }
}

```

Move the css file into a separated folder. You should name it *css*.