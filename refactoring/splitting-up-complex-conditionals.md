# Splitting Up Complex Conditionals

Years ago i worked in an agency which only coded perl. There was a guy how really liked code that nobody beside him could read - he was a `WiSe` guy ;-) Everywhere where i ran over his code, i had to refactor his complex conditional functions.

To make it easy understandable, here are php-examples:

**Complex conditional**
```php
if ( isset( $settings['wp-uploads'] ) && $settings['wp-uploads'] && in_array( $key, array( 'copy-to-s3', 'serve-from-s3' ) ) ) {
    return '1';
}
```
This example is hard to understand - you have to read the full conditional to known if it is true or not.


**Same conditional, easy to read and understand**
```php
if ( upload_is_valid( $settings, $key ) ) {
    return '1';
}
function upload_is_valid( $settings, $key ) {
    return isset( $settings['wp-uploads'] ) && $settings['wp-uploads'] && in_array( $key, array( 'copy-to-s3', 'serve-from-s3' ) );
}
```
I have not changed the conditional, but i have introduced a function, which has an easy to understand function-name. The conditional is now easy reusable and understandable, because it has an easy to understand function name.
 
This practice is also known as [Declarative Programming](1) ([german version](2)).

[1]: https://en.wikipedia.org/wiki/Declarative_programming
[2]: https://de.wikipedia.org/wiki/Deklarative_Programmierung