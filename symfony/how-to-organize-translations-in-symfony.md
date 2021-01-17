# How to organize translations in Syfony

Symfony is a great tool to build enterprise software. But i also comes with a lot of ways to solve the same problem.
When introducing translations into a project, i really had a problem with organizing the translations.

This is really not **the only one** solution - but i really like it.

Instead of using the real translations in the **.twig** file i use key identifiers, which clearly tell what 
they are used for. This makes it easy to identify the use of them and translate them.

> This is [Symfony Best Practice][0]

My `messages.en.yml` looks like this:

      app:                                  # Bundle
        project:                            # Identifier for context/scope
          sprint:
            current: Sprint 6
        
        page:                               # Scope: whole page
          title:                            # title of parent scope "page" 
            suffix: 'eBIRD'                 # suffix for title
        
        apidocument:                        # Scope: Handling entities "apidocument"
          list:                             # Sub-Scope "list"
            title: 'Dokumente verwalten'    # title for sub-scope
        
        documentsource:
          list:
            title: 'Anbieter verwalten'

In the **twig** templates the text-snippets look like this:

    {{ 'page.title.suffix'|trans }}

That way it is easy to read and to translate. I need to look at the scope `page` for the `title` item and change the 
`suffix` if i want to change the text-snippet.

## Via
* [obtao.com][1]
* [Symfony Translations][2]
* [Symfony Internationalization Best Practices][3]

[0]: http://symfony.com/doc/current/best_practices/i18n.html#translation-keys
[1]: http://obtao.com/blog/2013/06/how-to-organize-your-translations-in-symfony/
[2]: http://symfony.com/doc/current/translation.html
[3]: http://symfony.com/doc/current/best_practices/i18n.html