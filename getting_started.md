# Getting Started

This part of the doc will help you to quick start your project and will you a basic idea about how pages work. For you to get start visit the "Get Started" folder in your download package


##What's Included
Pages comes in two forms, within which you'll find the following directories and files, logically grouping common resources and providing both compiled and minified variations

Once you have download the package you will see the following folder structure


##Whats Inside getting_started
This folder is a boilerplate template to help you start your project from. You will find both AngularJS and jQuery versions inside this.


In the getting_started folder you will find both jQuery and AngularJS implementations of Pages. Pages was originally written in jQuery. To make it work on AngularJS environments, several directives and controllers wrote in v2.0.

Folder structure inside these two folders are almost the same except for the assets folder. In AngularJS this will contain directives and controllers which are mandatory for Pages to work, whereas in jQuery version you can have your own files.

###Folder : assets

If you are using jQuery, this folder is entirely dedicated for you and you can add your own images, custom css and js files, its grouped into resource folders for best practice

If you are an AngularJS user you will find Pages core directive and controllers.


###Folder : pages

This where the magic happens and contains pre-complied version of Pages, we do recommend updating any contents of the folder as all future updates are affected directly to this

AngularJS direcitves found in angular/assets/js/directives folder will be calling Pages modules found in this folder to make them work on AngularJS environments


###Folder : tpl (Only available for AngularJS)

Contains template HTML files that are lazy loaded and rendered for each state


###Whats Inside demo
This folder contains all the demo files that we have shown in the live version for your reference. You may wish to import code to your project from that. This is only used for reference and we do no recommend to start your project from demo files. Contains files for both AngularJS and jQuery users


###Whats Inside grunt and gulp
Pages support two popular build systems called Grunt and Gulp.
