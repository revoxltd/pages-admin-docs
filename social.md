##Social
Pages Social presents a Pinterest-like card layout that you can use for any social feed/timeline. It is also responsive and works flawlessly in mobile devices.

###jQuery users
Include the dependencies
Pages Social depends on the following jQuery plugins. Make sure you include them before calling the library functions. 
- Isotope
- Classie
- StepsForm

```
<!-- Waits for the images to be loaded before applying the Isotope plugin -->
<script src="assets/plugins/imagesloaded/imagesloaded.pkgd.min.js"></script>
<!-- Isotope plugin arranges the card layout -->
<script src="assets/plugins/jquery-isotope/isotope.pkgd.min.js" type="text/javascript"></script>
<!-- Required for stepsForm plugin -->
<script src="assets/plugins/classie/classie.js" type="text/javascript"></script>
<!-- Creates the multi-step status update form -->
<script src="assets/plugins/codrops-stepsform/js/stepsForm.js" type="text/javascript"></script>
```

- Include Pages Social Lib
- Include pages.social.min.js below pages.js
```
<script src="pages/js/pages.social.min.js"></script>
```

###Include Stylesheet
We recommend that you use the 'simple' theme instead of pages default theme (pages.css) together with Social for better experience.
```
<link href="pages/css/themes/simple.css" rel="stylesheet" type="text/css" />
```

####HTML Source
The following shows the basic markup structure you have to follow when setting up the Social page. Components mentioned inside *** are further explained below. You may change the content inside each component without changing the main structure below.

```
<!-- START SOCIAL WRAPPER -->
<div class="social-wrapper">
    <!-- START SOCIAL -->
    <div class="social " data-pages="social">
        <!--
            *** SOCIAL COVER GOES HERE ***
        -->
        <div class="container-fluid container-fixed-lg sm-p-l-20 sm-p-r-20">
            <div class="feed">
                <!-- START DAY -->
                <div class="day" data-social="day">
                    <!--
                        *** POSTS GO HERE ***
                    -->
                </div>
                <!-- END DAY -->
            </div>
            <!-- END FEED -->
        </div>
        <!-- END CONTAINER FLUID -->
    </div>
    <!-- END SOCIAL -->
</div>
<!-- END SOCIAL WRAPPER -->

Markup for cover

<!-- START SOCIAL COVER -->
<div class="jumbotron" data-pages="parallax" data-social="cover">
    <!-- START COVER PHOTO -->
    <div class="cover-photo">
        <img alt="Cover photo" src="assets/img/social/cover.png" />
    </div>
    <!-- END COVER PHOTO -->
    <!-- START COVER PHOTO INNER -->
    <div class="container-fluid container-fixed-lg sm-p-l-20 sm-p-r-20">
        <div class="inner">
            <div class="pull-bottom bottom-left m-b-40">
                <h5 class="text-white no-margin">welcome to pages social</h5>
                <h1 class="text-white no-margin"><span class="semi-bold">social</span> cover</h1>
            </div>
        </div>
    </div>
    <!-- END COVER PHOTO INNER -->
</div>
<!-- END SOCIAL COVER -->

Markup for posts

<!-- START PROFILE OVERVIEW -->
<div class="card no-border bg-transparent full-width" data-social="item">
    <!--
        SHOW ANY PROFILE OWNER DATA IN THE FIRST FULL-WIDTH ISOTOPE ITEM
        EX: NAME, CURRENT STATUS, LOCATION, ABOUT SECTION AND FRIENDS
    -->
    <!-- START CONTAINER FLUID -->
    <div class="container-fluid p-t-30 p-b-30 ">
        <div class="row">
            <div class="col-md-4">
                <div class="container-xs-height">
                    <div class="row-xs-height">
                        <!-- START USER PROFILE PICTURE -->
                        <div class="social-user-profile col-xs-height text-center col-top">
                            <div class="thumbnail-wrapper d48 circular bordered b-white">
                                <img alt="Avatar" width="55" height="55" data-src-retina="assets/img/profiles/avatar_small2x.jpg" data-src="assets/img/profiles/avatar.jpg" src="assets/img/profiles/avatar.jpg">
                            </div>
                            <br>
                            <i class="fa fa-check-circle text-success fs-16 m-t-10"></i>
                        </div>
                        <!-- END USER PROFILE PICTURE -->
                        <!-- START USER NAME -->
                        <div class="col-xs-height p-l-20">
                            <h3 class="no-margin">David Nester</h3>
                            <p class="no-margin fs-16">is excited about the new pages design framework</p>
                            <p class="hint-text m-t-5 small">San Fransisco Bay | CEO at Pages.inc</p>
                        </div>
                        <!-- END USER NAME -->
                    </div>
                </div>
            </div>
            <!-- START USER BIO -->
            <div class="col-md-4">
                <p class="no-margin fs-16">Hi My Name is David Nester, &amp; heres my new pages user profile page</p>
                <p class="hint-text m-t-5 small">I love reading people's about page especially those who are in the same industry as me.</p>
            </div>
            <!-- END USER BIO -->
            <!-- START USER'S FRIENDS -->
            <div class="col-md-4">
                <p class="m-b-5 small">1,435 Mutual Friends</p>
                <ul class="list-unstyled ">
                    <li class="m-r-10">
                        <div class="thumbnail-wrapper d32 circular b-white m-r-5 b-a b-white">
                            <img width="35" height="35" data-src-retina="assets/img/profiles/1x.jpg" data-src="assets/img/profiles/1.jpg" alt="Profile Image" src="assets/img/profiles/1.jpg">
                        </div>
                    </li>
                    <li>
                        <div class="thumbnail-wrapper d32 circular b-white m-r-5 b-a b-white">
                            <img width="35" height="35" data-src-retina="assets/img/profiles/2x.jpg" data-src="assets/img/profiles/2.jpg" alt="Profile Image" src="assets/img/profiles/2.jpg">
                        </div>
                    </li>
                    ...
                    <li>
                        <div class="thumbnail-wrapper d32 circular b-white">
                            <div class="bg-master text-center text-white"><span>+34</span>
                            </div>
                        </div>
                    </li>
                </ul>
                <br>
                <p class="m-t-5 small">More friends</p>
            </div>
            <!-- END USER'S FRIENDS -->
        </div>
    </div>
    <!-- END CONTAINER FLUID -->
</div>
<!-- END PROFILE OVERVIEW -->

<!-- START STATUS UPDATE FORM -->
<!-- 
    USE 'col1, col2, col3' TO SPECIFY CARD WIDTH 
    data-social="item" AUTO INIT THE CARD
-->
<div class="card col2 padding-20" data-social="item">
    <!-- 
        MULTI-STEP STATUS UPDATE FORM IS MADE POSSIBLE USING 'stepsForm' PLUGIN 
    -->
    <form class="simform no-margin" autocomplete="off" data-social="status">
        <div class="status-form-inner">
            <!-- START QUESTIONS -->
            <ol class="questions">
                <li>
                    <span>
                       <label for="status-q1">What's on your mind?</label>
                    </span>
                    <input id="status-q1" name="q1" type="text" />
                </li>
                <li>
                    <span>
                        <label for="status-q2">What are you feeling?</label>
                    </span>
                    <input id="status-q2" name="q2" type="text" />
                </li>
                <li>
                    <span>
                        <label for="status-q3">What's your location?</label>
                    </span>
                    <input id="status-q3" name="q3" type="text" />
                </li>
                <li>
                    <span>
                        <label for="status-q4">Who are you with?</label>
                    </span>
                    <input id="status-q4" name="q4" type="text" />
                </li>
            </ol>
            <!--END QUESTIONS -->
            <button class="submit" type="submit">Send answers</button>
            <!-- FORM CONTROLS. DO NOT REMOVE -->
            <div class="controls">
                <button class="next"></button>
                <div class="progress"></div>
                <span class="number">
                    <span class="number-current"></span>
                    <span class="number-total"></span>
                </span>
                <span class="error-message"></span>
            </div>
        </div>
        <!-- MESSAGE TO BE DISPLAYED AT THE END -->
        <span class="final-message"></span>
    </form>
</div>
<!-- END STATUS UPDATE FORM -->
<!-- START POST TYPE-1 -->
<div class="card status col2" data-social="item">
    <div class="circle" data-toggle="tooltip" title="Label">
    </div>
    <h5>David Nester updated his status
                            <span class="hint-text">few seconds ago</span></h5>
    <h2>Earned my first salary bonus for the best design of the year award.</h2>
    <ul class="reactions">
        <li><a href="#">5,345 <i class="fa fa-comment-o"></i></a>
        </li>
        <li><a href="#">23K <i class="fa fa-heart-o"></i></a>
        </li>
    </ul>
</div>
<!-- END POST TYPE-1 -->
<!-- START POST TYPE-2 -->
<div class="card share share-self col1" data-social="item">
    <div class="circle" data-toggle="tooltip" title="Label">
    </div>
    <div class="card-header clearfix">
        <div class="user-pic">
            <img alt="Profile Image" width="33" height="33" data-src-retina="assets/img/profiles/5x.jpg" data-src="assets/img/profiles/5.jpg" src="assets/img/profiles/5x.jpg">
        </div>
        <h5>Shannon Williams</h5>
        <h6>Shared a photo
           <span class="location semi-bold"><i class="fa fa-map-marker"></i> NYC, New York</span>
        </h6>
    </div>
    <div class="card-description">
        <p>Inspired by : good design is obvious, great design is transparent</p>
        <div class="via">via themeforest</div>
    </div>
    <div class="card-content">
        <ul class="buttons ">
            <li>
                <a href="#"><i class="fa fa-expand"></i>
                                    </a>
            </li>
            <li>
                <a href="#"><i class="fa fa-heart-o"></i>
                                    </a>
            </li>
        </ul>
        <img alt="Social post" src="assets/img/social-post-image.png">
    </div>
    <div class="card-footer clearfix">
        <div class="time">few seconds ago</div>
        <ul class="reactions">
            <li><a href="#">5,345 <i class="fa fa-comment-o"></i></a>
            </li>
            <li><a href="#">23K <i class="fa fa-heart-o"></i></a>
            </li>
        </ul>
    </div>
</div>
<!-- END POST TYPE-2 -->
<!-- START POST TYPE-3 -->
<div class="card share share-self col1" data-social="item">
    <div class="circle" data-toggle="tooltip" title="Label">
    </div>
    <div class="card-header clearfix">
        <div class="user-pic">
            <img alt="Profile Image" width="33" height="33" data-src-retina="assets/img/profiles/8x.jpg" data-src="assets/img/profiles/8.jpg" src="assets/img/profiles/8x.jpg">
        </div>
        <h5>Jeff Curtis</h5>
        <h6>Shared a Tweet
                                <span class="location semi-bold"><i class="fa fa-map-marker"></i> SF, California</span>
                            </h6>
    </div>
    <div class="card-description">
        <p>What you think, you become. What you feel, you attract. What you imagine, you create - Buddha. <a href="#">#quote</a> </p>
        <div class="via">via Twitter</div>
    </div>
</div>
<!-- END POST TYPE-3 -->
<!-- START POST TYPE-4 -->
<div class="card share share-other col1" data-social="item">
    <div class="circle" data-toggle="tooltip" title="Label">
    </div>
    <div class="card-content">
        <ul class="buttons ">
            <li>
                <a href="#"><i class="fa fa-expand"></i>
                                    </a>
            </li>
            <li>
                <a href="#"><i class="fa fa-heart-o"></i>
                                    </a>
            </li>
        </ul>
        <img alt="Quote" src="assets/img/social/quote.jpg">
    </div>
    <div class="card-description">
        <p>Like if you agree</p>
    </div>
    <div class="card-footer clearfix">
        <div class="time">few seconds ago</div>
        <ul class="reactions">
            <li><a href="#">5,345 <i class="fa fa-comment-o"></i></a>
            </li>
            <li><a href="#">23K <i class="fa fa-heart-o"></i></a>
            </li>
        </ul>
    </div>
    <div class="card-header clearfix">
        <div class="user-pic">
            <img alt="Profile Image" width="33" height="33" data-src-retina="assets/img/profiles/7x.jpg" data-src="assets/img/profiles/7.jpg" src="assets/img/profiles/7x.jpg">
        </div>
        <h5>Tracy Brooks</h5>
        <h6>Shared a photo on your wall</h6>
    </div>
</div>
<!-- END POST TYPE-4 -->
<!-- START POST TYPE-5 -->
<div class="card share share-self col1" data-social="item">
    <div class="card-header ">
        <h5 class="text-complete pull-left fs-12">News <i class="fa fa-circle text-complete fs-11"></i></h5>
        <div class="pull-right small hint-text">
            5,345 <i class="fa fa-comment-o"></i>
        </div>
        <div class="clearfix"></div>
    </div>
    <div class="card-description">
        <h3>Ebola outbreak: Clinical drug trials to start next month as death toll mounts</h3>
    </div>
    <div class="card-footer clearfix">
        <div class="pull-left">via <span class="text-complete">CNN</span>
        </div>
        <div class="pull-right hint-text">
            Apr 23
        </div>
        <div class="clearfix"></div>
    </div>
</div>
<!-- END POST TYPE-5 -->
```

##Initializing Pages Social

Pages will auto-initialize Social if elements with following data-properties are found in the DOM. The following shows the default settings object for Social

```
$.fn.social.defaults = {
        cover: '[data-social="cover"]',
        day: '[data-social="day"]',
        status: '[data-social="status"]',
        item: '[data-social="item"]',
        colWidth: 300
    }
```

If you wish to make the initialization programatically, refrain from using the above data properties in the DOM. Set the classes/ids you defined in the DOM in $.fn.social.defaults object and then call the initialization script.

The minimum column width for Social is 300 pixels. If you wish to change it, you may have edit the .col1,.col2 and .col3 in the CSS accordingly. ex: If colWidth is 400, .col1,.col2 and .col3 will get 400px, 820px and 1220px (Note the extra 20px reserved for gutter width)

```
$(document).ready(function() {
    $.fn.social.defaults = {
        cover: '.cover', // Cover element
        day: '.day', // Day element
        status: '.status', // Status update box element
        item: '.item', // Post item
        colWidth: 300 // minimum column width for cards
    }
    $('#social').social();
});
```

##AngularJS users
####Dependencies
You will find social app route and dependency injections in demo/angular/assets/js/config.js. Controllers and Directives are found in assets/js/apps/social/social.js and these depend social lib, pages.social.min.js mentioned above
```
// File: demo/angular/assets/js/config.js
...
// Social app
.state('app.social', {
    url: '/social',
    templateUrl: 'tpl/apps/social/social.html',
    resolve: {
        deps: ['$ocLazyLoad', function($ocLazyLoad) {
            return $ocLazyLoad.load([
                    'isotope',
                    'stepsForm'
                ], {
                    insertBefore: '#lazyload_placeholder'
                })
                .then(function() {
                    return $ocLazyLoad.load([
                        'pages/js/pages.social.min.js',
                        'assets/js/apps/social/social.js'
                    ])
                });
        }]
    }
})
...
```
####Template
Please refer to jQuery section above for Markup for posts and cover.


####Controller and Directive
```
// File: assets/js/apps/social/social.js
'use strict';

/* Controllers */

angular.module('app')
    // Social controller 
    .controller('SocialCtrl', ['$scope', '$stateParams', '$rootScope', function($scope, $stateParams, $rootScope) {
        // Apply recommended theme for Calendar
        $scope.app.layout.theme = 'pages/css/themes/simple.css';

        // For demo purposes only. Changes the theme back to pages default when switching the state. 
        $rootScope.$on('$stateChangeSuccess',
            function(event, toState, toParams, fromState, fromParams) {
                $scope.app.layout.theme = 'pages/css/pages.css';
            })

    }]);

/* Directives */

angular.module('app')
    .directive('pgSocial', function() {
        return {
            restrict: 'A',
            link: function(scope, element, attrs) {
                var $social = $(element);
                $social.social($social.data());
            }
        }
    });
```