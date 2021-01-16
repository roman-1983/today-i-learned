# Localize date in Twig using Symfony 2/3

It is possible to format a date according to the active `locale` which is set via the `config.yml` or direct to the user-locale.

To use the `localizeddate` filter, the [`intl` extension for PHP][1] is required.

Also the Twif intl-extension must be activated in the Symfony project.

    services:
        twig.extension.intl:
            class: Twig_Extensions_Extension_Intl
            tags:
                - { name: twig.extension }            

After that, the filter can be used in all `.twig` templates as seen in this snippet:

    {{ post.published_at|localizeddate('medium', 'none', locale) }}

[1]: http://php.net/manual/en/book.intl.php
