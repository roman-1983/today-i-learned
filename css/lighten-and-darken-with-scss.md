# Lighten And Darken With SCSS 

With SCSS it is easy to lighten or darken a given color via a vertain percentage value.
To achieve this, i have to use [`lighten`](1) and [`darken`](2) functions.
The following html-code   
```html
<div class='light'></div>
<div class='blue'></div>
<div class='dark'></div>
```

```scss
$box-color: #0074d9;
.blue { background: $box-color; }
.light { background: lighten($box-color, 20%); }
.dark { background: darken($box-color, 20%); }
```

The result looks something like this:  ![](http://i.imgur.com/SaeTL8H.png)

[1]: http://sass-lang.com/documentation/Sass/Script/Functions.html#lighten-instance_method
[2]: http://sass-lang.com/documentation/Sass/Script/Functions.html#darken-instance_method