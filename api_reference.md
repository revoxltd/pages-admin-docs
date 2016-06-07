# API Reference

As mentioned in the Getting Started guide, Pages core framework files can be found in the pages folder. Inside this you'll be able to find pages.js and pages.min.js files which contain the core logic and utility functions of the framework. Simply including either of these files will set environment variables, auto initialize all the core modules for you and present you with the Pages global object $.Pages which you can use to call utility functions.


##Environment variables
Pages will detect the user OS and add it as a class name (ex: 'windows', 'mac', 'unix', 'linux') into body.

It will also detect if it's mobile device or desktop and add either 'mobile' and 'desktop' into the same tag.

##Auto-initialized jQuery Plugins
The following table shows which plugins are auto-initialized and their default configuration.

AngularJS users can apply corresponding directives or ui-jq attribute (provided by UI.Utils) to load plugins.

