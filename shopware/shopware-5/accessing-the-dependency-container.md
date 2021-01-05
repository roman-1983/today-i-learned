# Accessing the dependency container in Shopware

To retrieve the container in side a controller, you use this snippet:

    $this->Container();

Inside the plugin bootstrap you can use this snippet to get the container:
    
    // Zugriff im Plugin Bootstrap
    $this->container;
    
From anywhere else you can get the container via the `Shopware` object.

    Shopware()->Container();