# Sass

Sass preprocess `.sass` or `.scss` and generate normal `.css` file. It makes you feel writing css in a programing style.

    gem install sass

Sass has two syntaxes. The first syntax, is known as `SCSS` means “Sassy CSS”, is the commonly used syntax which is a superset of CSS3's syntax and uses file extension `.scss`. The second syntax `SCSS` makes use of a intended writing style, and its file extension is `.sass`.

## Usages:

```
# Convert `.sass` to `.scss` or reverse:
sass-convert style.sass style.scss
# Preprocess:
sass input.scss output.css
sass --watch app/sass:public/stylesheets
```


