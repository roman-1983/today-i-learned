# Get user-id and check login status

You can check via the `sUserId` if a user is logged in. The variable can be retrieved via the `Session` object.

**In global context**
    
    $userId = Shopware()->Session()->sUserId

** In event subscriber**

    /** @var \Enlight_Controller_Action $controller */
    $controller = $args->get('subject');
    $userId = $controller->get('session')->offsetGet('sUserId');