# Composer: Difference of `composer install` and `composer update`

In a project my team ran in a dependency fuck-up because not every known the difference between `composer install` 
and `composer update`.

## The composer files
When using composer, there are 2 files that are important:
- composer.json
- composer.lock

Then `composer.json` lists all requirements and if you run `composer install` the file `composer.lock` will be 
generated. The `composer.lock` file lists all required packages and the installed version.

## The composer workflow
1. Add `composer.json` with some dependencies
2. Run `composer install`
3. Add some more dependencies
4. Run `composer update` as you've updated your dependencies

## `Composer install` and `Composer update`
The first time in a project there should not exist a `composer.lock` file. This will be generated on the first run of
`composer.lock`. Whenever composer generates a new `composer.lock` it locks you to a specific set of dependencies 
and the latest versions of those dependencies it can resolve.

After changing a required version, you have to run `composer update` instead of `composer install`.

> What you really need to do is deploy your updated composer.lock, and then re-run composer install. You should never run composer update in production. If however you deploy a new composer.lock with new dependencies and/or versions (after having run composer update in dev) and then run composer install composer will update and install new your new dependencies.

##  Via
[Adamcod.es][1]

[1]: https://adamcod.es/2013/03/07/composer-install-vs-composer-update.html