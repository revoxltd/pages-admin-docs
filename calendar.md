# Calendar

Pages calendar plugin is exclusive only on pages and is not a third party plugin. The horizontal scrolling helps it to fit easily on to small screens and user experience is seemless across all platforms. It supports many features including multiple languages and timezones

#####jQuery users Dependencies
```
<script src="assets/plugins/interactjs/interact.min.js" type="text/javascript"></script>
<script src="assets/plugins/moment/moment-with-locales.min.js"></script>

```


#####Pages Calendar Li
```
<script src="pages/js/pages.calendar.min.js"></script>
```

#####HTML Source

Inlcude the following HTML source to your file, you can remove the compontents you do not need to have
```
<div id="myCalendar" class="full-height"></div>
```

#####Initialize Pages Calendar

To initialize pages calendar with default setting use the following code



#####AngularJS users Dependencies

You will find calendar route and dependency injections in demo/angular/assets/js/config.js. Controllers and Directives are found in assets/js/apps/calendar/calendar.js and these depend pages.calendar.min.js mentioned above


```
//Calendar app
.state('app.calendar', {
    url: '/calendar',
    templateUrl: 'tpl/apps/calendar/calendar.html',
    resolve: {
        deps: ['$ocLazyLoad', function($ocLazyLoad) {
            return $ocLazyLoad.load([
                    'switchery',
                    'jquery-ui',
                    'moment',
                    'hammer'
                ], {
                    insertBefore: '#lazyload_placeholder'
                })
                .then(function() {
                    return $ocLazyLoad.load([
                        'pages/js/pages.calendar.min.js',
                        'assets/js/apps/calendar/calendar.js'
                    ])
                });
        }]
    }
})
```