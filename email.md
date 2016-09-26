#Email
Pages Email app is a web-based email client designed and developed exclusively for Pages framework. It has a responsive design to work flawlessly across many devices. Please note that current version only includes the Inbox and Compose views. This is a work in progress and we're hoping to make this a complete jQuery plugin soon

##JQuery users
####Dependencies
Include the stylesheets of the libraries
```
<link href="assets/plugins/bootstrap3-wysihtml5/bootstrap3-wysihtml5.min.css" rel="stylesheet" type="text/css" />
<link href="assets/plugins/jquery-menuclipper/jquery.menuclipper.css" rel="stylesheet" type="text/css" />
<link href="assets/plugins/bootstrap-tag/bootstrap-tagsinput.css" rel="stylesheet" type="text/css" />
Include the scripts

<script src="assets/plugins/bootstrap3-wysihtml5/bootstrap3-wysihtml5.all.min.js"></script>
<script src="assets/plugins/jquery-menuclipper/jquery.menuclipper.js"></script>
<script src="assets/plugins/bootstrap-tag/bootstrap-tagsinput.min.js" type="text/javascript"></script>
```

####Pages Email Lib

In pages.email.js please replace the URL “http://revox.io/json/emails.json” (Line #54) with your own end point URL which can return a JSON having a structure mentioned below. Then include the updated file below pages.js.
```
<script src="pages/js/pages.email.js"></script>
```

- emails - (Array) List of all emails categorized by date
  - group - Date category
  - list - list of emails received for the day
    - id - unique ID to represent each email, should be an unique integer
    - subject - Subject line of the email
    - to - (Array) Recipients name list
    - body - Email body. HTML is allowed
    - time - Time email was sent
    - datetime - Date and time combined
    - from - Sender name
    - dp - Display picture of the sender
    - dpRetina - Retina version of the display picture of the sender

####Sample JSON output
```
{
    "emails": [
        {
            "group": "Today April 23",
            "list": [{
                "id": 1,
                "subject": "Pages - Multi-Purpose Admin Template Revolution Begins here!",
                "to": ["David Nester", "Jane Smith"],
                "body": "<p>First email body</p> ",
                "time": "5 Mins ago",
                "datetime": "Today at 1:33pm",
                "from": "David Nester",
                "dp": "assets/img/profiles/avatar.jpg",
                "dpRetina": "assets/img/profiles/avatar2x.jpg"
            }, {
                "id": 2,
                "subject": "Your site has some very imaginative animation /movement! ",
                "to": ["Anne Simons"],
                "body": "<p>Second email body</p> ",
                "time": "45 mins ago",
                "datetime": "Today at 1:33pm",
                "from": "Anne Simons",
                "dp": "assets/img/profiles/5.jpg",
                "dpRetina": "assets/img/profiles/5x.jpg"
            }]
        }, {
            "group": "Yesterday April 22",
            "list": [{
                "id": 3,
                "subject": "Good design is obvious. Great design is transparent",
                "to": ["John Doe", "Anne Simons"],
                "body": "<p>Third email body</p> ",
                "time": "1:33pm",
                "datetime": "Today at 1:33pm",
                "from": "David Nester",
                "dp": "assets/img/profiles/b.jpg",
                "dpRetina": "assets/img/profiles/b2x.jpg"
            }]
        }
    ]
}
```

####Markup
Inlcude the following HTML source in your file

#####Inbox view
```
<!-- START EMAIL -->
<div class="email-wrapper">
    <!-- START EMAIL SIDEBAR MENU-->
    <nav class="email-sidebar padding-30">
        <a href="email_compose.html" class="btn btn-complete btn-block btn-compose m-b-30">Compose</a>
        <p class="menu-title">BROWSE</p>
        <ul class="main-menu">
            <li class="active">
                <a href="#">
                    <span class="title"><i class="pg-inbox"></i> Inbox</span>
                    <span class="badge pull-right">5</span>
                </a>
            </li>
            <li class="">
                <a href="#">
                    <span class="title"><i class="pg-folder"></i> All mail</span>
                </a>
                <ul class="sub-menu no-padding">
                    <li>
                        <a href="#">
                            <span class="title">Important</span>
                        </a>
                    </li>
                    <li>
                        <a href="#">
                            <span class="title">Labeled</span>
                        </a>
                    </li>
                </ul>
            </li>
            <li>
                <a href="#">
                    <span class="title"><i class="pg-sent"></i> Sent</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <span class="title"><i class="pg-spam"></i> Spam</span>
                    <span class="badge pull-right">10</span>
                </a>
            </li>
        </ul>
        <p class="menu-title m-t-20 all-caps">Quick view</p>
        <ul class="sub-menu no-padding">
            <li>
                <a href="#">
                    <span class="title">Documents</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <span class="title">Flagged</span>
                    <span class="badge pull-right">5</span>
                </a>
            </li>
            <li>
                <a href="#">
                    <span class="title">Images</span>
                </a>
            </li>
        </ul>
    </nav>
    <!-- END EMAL SIDEBAR MENU -->
    <!-- START EMAILS LIST -->
    <div class="email-list b-r b-grey"> <a class="email-refresh" href="#"><i class="fa fa-refresh"></i></a>
        <div id="emailList">
            <!-- START EMAIL LIST SORTED BY DATE -->
            <!-- END EMAIL LIST SORTED BY DATE -->
        </div>
    </div>
    <!-- END EMAILS LIST -->
    <!-- START OPENED EMAIL -->
    <div class="email-opened">
        <div class="no-email">
            <h1>No email has been selected</h1>
        </div>
        <div class="email-content-wrapper">
            <div class="actions-wrapper menuclipper bg-master-lightest">
                <ul class="actions menuclipper-menu no-margin p-l-20 ">
                    <li class="visible-sm-inline-block visible-xs-inline-block">
                        <a href="#" class="email-list-toggle"><i class="fa fa-angle-left"></i> All Inboxes
                                </a>
                    </li>
                    <li class="no-padding "><a href="#" class="text-info">Reply</a>
                    </li>
                    <li class="no-padding "><a href="#">Reply all</a>
                    </li>
                    <li class="no-padding "><a href="#">Forward</a>
                    </li>
                    <li class="no-padding "><a href="#">Mark as read</a>
                    </li>
                    <li class="no-padding "><a href="#" class="text-danger">Delete</a>
                    </li>
                </ul>
                <div class="clearfix"></div>
            </div>
            <div class="email-content">
                <div class="email-content-header">
                    <div class="thumbnail-wrapper d48 circular bordered">
                        <img width="40" height="40" alt="" data-src-retina="assets/img/profiles/avatar2x.jpg" data-src="assets/img/profiles/avatar.jpg" src="assets/img/profiles/avatar2x.jpg">
                    </div>
                    <div class="sender inline m-l-10">
                        <p class="name no-margin bold">
                        </p>
                        <p class="datetime no-margin"></p>
                    </div>
                    <div class="clearfix"></div>
                    <div class="subject m-t-20 m-b-20 semi-bold">
                    </div>
                    <div class="fromto">
                        <div class="pull-left">
                            <div class="btn-group dropdown-default">
                                <a class="btn dropdown-toggle btn-small btn-rounded" data-toggle="dropdown" href="#">
                                        David Nester
                                        <span class="caret"></span>
                                        </a>
                                <ul class="dropdown-menu">
                                    <li><a href="#">Action</a>
                                    </li>
                                    <li><a href="#">Friend</a>
                                    </li>
                                    <li><a href="#">Report</a>
                                    </li>
                                </ul>
                            </div>
                            <label class="inline">
                                <span class="muted">&nbsp;&nbsp;to</span>
                                <span class=" small-text">johnsmith@skyace.com</span>
                            </label>
                        </div>
                    </div>
                </div>
                <div class="clearfix"></div>
                <div class="email-content-body m-t-20">
                </div>
                <div class="wysiwyg5-wrapper b-a b-grey m-t-30">
                    <textarea class="email-reply" placeholder="Reply"></textarea>
                </div>
            </div>
        </div>
    </div>
    <!-- END OPENED EMAIL -->
    <!-- START COMPOSE BUTTON FOR TABS -->
    <div class="compose-wrapper visible-xs">
        <a class="compose-email text-info pull-right m-r-10 m-t-10" href="email_compose.html"><i class="fa fa-pencil-square-o"></i></a>
    </div>
    <!-- END COMPOSE BUTTON -->
</div>
<!-- END EMAIL -->
```

#####Compose view

Replace ```<div class="email-opened">...</div>`` with the following for the compose view
```
<!-- START COMPOSE EMAIL -->
<div class="email-composer container-fluid">
    <div class="row">
        <div class="col-sm-12 no-padding">
            <div class="wysiwyg5-wrapper email-toolbar-wrapper">
            </div>
            <form id="form-project" role="form" autocomplete="off">
                <div class="form-group-attached">
                    <div class="row clearfix">
                        <div class="col-sm-6">
                            <div class="form-group form-group-default">
                                <label>TO:</label>
                                <input name="to" data-role="tagsinput" class="form-control tagsinput" type="text" value="John Smith" />
                            </div>
                        </div>
                        <div class="col-sm-6">
                            <div class="form-group form-group-default">
                                <label>CC:</label>
                                <input type="text" class="form-control" name="cc" placeholder="Add Carbon Copy">
                            </div>
                        </div>
                    </div>
                    <div class="form-group form-group-default">
                        <label>Subject</label>
                        <input type="text" class="form-control" name="subject">
                    </div>
                </div>
            </form>
            <div class="wysiwyg5-wrapper email-body-wrapper">
                <textarea class="wysiwyg email-body" style="height:350px"></textarea>
            </div>
        </div>
    </div>
    <div class="row p-b-20">
        <div class="col-sm-11">
            <button class="btn btn-white btn-cons">Cancel</button>
            <button class="btn btn-complete btn-cons m-l-10">Send</button>
            <div class="checkbox inline m-l-20">
                <input type="checkbox" value="1" id="sendCC">
                <label for="sendCC" class="hint-text hidden-xs">Send a <span class="text-complete">Carbon Copy</span> CC to my Primary email address.</label>
                <label for="sendCC" class="hint-text visible-xs-inline">Send me a CC</label>
            </div>
        </div>
        <div class="col-sm-1">
            <button class="btn btn-complete pull-right">
                <i class="pg-save"></i>
            </button>
        </div>
    </div>
</div>
<!-- END COMPOSE EMAIL -->
```

##AngularJS users
####Dependencies
You will find email app route and dependency injections in demo/angular/assets/js/config.js. Controllers and Directives are found in assets/js/apps/email/email.js and these depend email lib, pages.email.min.js mentioned above
```
// File: demo/angular/assets/js/config.js
...
// Email app
.state('app.email', {
        abstract: true,
        url: '/email',
        templateUrl: 'tpl/apps/email/email.html',
        resolve: {
            deps: ['$ocLazyLoad', function($ocLazyLoad) {
                return $ocLazyLoad.load([
                        'menuclipper',
                        'wysihtml5'
                    ], {
                        insertBefore: '#lazyload_placeholder'
                    })
                    .then(function() {
                        return $ocLazyLoad.load([
                            'assets/js/apps/email/service.js',
                            'assets/js/apps/email/email.js'
                        ])
                    });
            }]
        }
    })
    .state('app.email.inbox', {
        url: '/inbox/:emailId',
        templateUrl: 'tpl/apps/email/email_inbox.html'
    })
    .state('app.email.compose', {
        url: '/compose',
        templateUrl: 'tpl/apps/email/email_compose.html'
    })
...
```

###Template files
```<!-- File: tpl/apps/email/email.html -->
<!-- START EMAIL -->
<div class="email-wrapper">
    <div ng-include src="'tpl/apps/email/blocks/sidebar.html'" include-replace>
    </div>
    <div class="full-height" ui-view></div>
    <!-- START COMPOSE BUTTON FOR TABS -->
    <div class="compose-wrapper visible-xs">
        <a class="compose-email text-info pull-right m-r-10 m-t-10" href="email_compose.html"><i class="fa fa-pencil-square-o"></i></a>
    </div>
    <!-- END COMPOSE BUTTON -->
</div>
<!-- END EMAIL -->
```

```
<!-- File: tpl/apps/email/email_inbox.html -->
<!-- START EMAILS LIST -->
<div class="email-list b-r b-grey" ng-controller="EmailListCtrl"> <a class="email-refresh" href=""><i class="fa fa-refresh"></i></a>
    <div id="emailList" ui-jq="ioslist">
        <!-- START EMAIL LIST SORTED BY DATE -->
            <div class="list-view-group-container" ng-repeat="email in emails">
                <div class="list-view-group-header"><span>{{email.group}}</span></div>

                <ul class="no-padding">
                    <li ng-repeat="item in email.list" class="item padding-15" data-email-id="{{item.id}}" ng-click="view(emailId)" ng-init="emailId = item.id"> 
                                <div class="thumbnail-wrapper d32 circular bordered {{item.color}}"> 
                                    <img width="40" height="40" alt="" ng-src="{{item.dpRetina}}"> 
                                </div> 
                                <div class="checkbox  no-margin p-l-10"> 
                                    <input type="checkbox" value="1" id="emailcheckbox-{{$parent.$index}}-{{$index}}"> 
                                    <label for="emailcheckbox-{{$parent.$index}}-{{$index}}"></label> 
                                </div> 
                                <div class="inline m-l-15"> 
                                    <p class="recipients no-margin hint-text small">{{formatTo(item.to)}}</p> 
                                    <p class="subject no-margin">{{item.subject}}</p> 
                                    <p class="body no-margin"> 
                                     {{formatBody(item.body)}}
                                    </p> 
                                </div> 
                                <div class="datetime">{{item.time}}</div> 
                                <div class="clearfix"></div> 
                            </li>
                </ul>
        </div>
        <!-- END EMAIL LIST SORTED BY DATE -->
    </div>
</div>
<!-- END EMAILS LIST -->
<!-- START OPENED EMAIL -->
<div class="email-opened" ng-controller="EmailViewCtrl">
    <div class="no-email" ng-hide="email">
        <h1>No email has been selected</h1>
    </div>
     <div class="email-content-wrapper" ng-show="email">
        <div class="actions-wrapper menuclipper bg-master-lightest" ui-jq="menuclipper" ui-options="{bufferWidth: 20}">
            <ul class="actions menuclipper-menu no-margin p-l-20 ">
                <li class="visible-sm-inline-block visible-xs-inline-block">
                    <a ng-click="showInbox()" class="email-list-toggle"><i class="fa fa-angle-left"></i> All Inboxes
                                </a>
                </li>
                <li class="no-padding "><a href="" class="text-info">Reply</a>
                </li>
                <li class="no-padding "><a href="">Reply all</a>
                </li>
                <li class="no-padding "><a href="">Forward</a>
                </li>
                <li class="no-padding "><a href="">Mark as read</a>
                </li>
                <li class="no-padding "><a href="" class="text-danger">Delete</a>
                </li>
            </ul>
            <div class="clearfix"></div>
        </div>
        <div class="email-content">
            <div class="email-content-header">
                <div class="thumbnail-wrapper d48 circular bordered">
                    <img width="40" height="40" alt="" ui-jq="unveil" data-src-retina="assets/img/profiles/avatar2x.jpg" data-src="assets/img/profiles/avatar.jpg" src="assets/img/profiles/avatar2x.jpg">
                </div>
                <div class="sender inline m-l-10">
                    <p class="name no-margin bold">{{email.from}}
                    </p>
                    <p class="datetime no-margin">{{email.datetime}}</p>
                </div>
                <div class="clearfix"></div>
                <div class="subject m-t-20 m-b-20 semi-bold">{{email.subject}}
                </div>
                <div class="fromto">
                    <div class="pull-left">
                        <div class="btn-group dropdown-default">
                            <a class="btn dropdown-toggle btn-small btn-rounded" data-toggle="dropdown" href="">
                                        David Nester
                                        <span class="caret"></span>
                                        </a>
                            <ul class="dropdown-menu">
                                <li><a href="">Action</a>
                                </li>
                                <li><a href="">Friend</a>
                                </li>
                                <li><a href="">Report</a>
                                </li>
                            </ul>
                        </div>
                        <label class="inline">
                            <span class="muted">&nbsp;&nbsp;to</span>
                            <span class=" small-text">johnsmith@skyace.com</span>
                        </label>
                    </div>
                </div>
            </div>
            <div class="clearfix"></div>
            <div class="email-content-body m-t-20" ng-bind-html="emailHTML" >
            </div>
            <div class="wysiwyg5-wrapper b-a b-grey m-t-30">
                <textarea class="email-reply" placeholder="Reply" reply-editor></textarea>
            </div>
        </div>
    </div>

</div>
<!-- END OPENED EMAIL -->
```
```
<!-- File: tpl/apps/email/email_compose.html -->
<!-- START COMPOSE EMAIL -->
<div class="email-composer container-fluid" email-composer>
    <div class="row">
        <div class="col-sm-12 no-padding">
            <div class="wysiwyg5-wrapper email-toolbar-wrapper">
            </div>
            <form id="form-project" role="form" autocomplete="off">
                <div class="form-group-attached">
                    <div class="row clearfix">
                        <div class="col-sm-6">
                            <div pg-form-group class="form-group form-group-default">
                                <label>TO:</label>
                                <input name="to" data-role="tagsinput" class="form-control tagsinput" type="text" value="John Smith" />
                            </div>
                        </div>
                        <div class="col-sm-6">
                            <div pg-form-group class="form-group form-group-default">
                                <label>CC:</label>
                                <input type="text" class="form-control" name="cc" placeholder="Add Carbon Copy">
                            </div>
                        </div>
                    </div>
                    <div pg-form-group class="form-group form-group-default">
                        <label>Subject</label>
                        <input type="text" class="form-control" name="subject">
                    </div>
                </div>
            </form>
            <div class="wysiwyg5-wrapper email-body-wrapper">
                <textarea class="wysiwyg email-body" style="height:350px"></textarea>
            </div>
        </div>
    </div>
    <div class="row p-b-20">
        <div class="col-sm-11">
            <button class="btn btn-white btn-cons">Cancel</button>
            <button class="btn btn-complete btn-cons m-l-10">Send</button>
            <div class="checkbox inline m-l-20">
                <input type="checkbox" value="1" id="sendCC">
                <label for="sendCC" class="hint-text hidden-xs">Send a <span class="text-complete">Carbon Copy</span> CC to my Primary email address.</label>
                <label for="sendCC" class="hint-text visible-xs-inline">Send me a CC</label>
            </div>
        </div>
        <div class="col-sm-1">
            <button class="btn btn-complete pull-right">
                <i class="pg-save"></i>
            </button>
        </div>
    </div>
</div>
<!-- END COMPOSE EMAIL -->
```

```
<!-- File: tpl/apps/email/blocks/sidebar.html -->
<!-- START EMAIL SIDEBAR MENU-->
    <nav class="email-sidebar padding-30">
        <a ui-sref="app.email.compose" class="btn btn-complete btn-block btn-compose m-b-30">Compose</a>
        <p class="menu-title">BROWSE</p>
        <ul class="main-menu">
            <li class="active">
                <a ui-sref="app.email.inbox">
                    <span class="title"><i class="pg-inbox"></i> Inbox</span>
                    <span class="badge pull-right">5</span>
                </a>
            </li>
            <li class="">
                <a href="">
                    <span class="title"><i class="pg-folder"></i> All mail</span>
                </a>
                <ul class="sub-menu no-padding">
                    <li>
                        <a href="">
                            <span class="title">Important</span>
                        </a>
                    </li>
                    <li>
                        <a href="">
                            <span class="title">Labeled</span>
                        </a>
                    </li>
                </ul>
            </li>
            <li>
                <a href="">
                    <span class="title"><i class="pg-sent"></i> Sent</span>
                </a>
            </li>
            <li>
                <a href="">
                    <span class="title"><i class="pg-spam"></i> Spam</span>
                    <span class="badge pull-right">10</span>
                </a>
            </li>
        </ul>
        <p class="menu-title m-t-20 all-caps">Quick view</p>
        <ul class="sub-menu no-padding">
            <li>
                <a href="">
                    <span class="title">Documents</span>
                </a>
            </li>
            <li>
                <a href="">
                    <span class="title">Flagged</span>
                    <span class="badge pull-right">5</span>
                </a>
            </li>
            <li>
                <a href="">
                    <span class="title">Images</span>
                </a>
            </li>
        </ul>
    </nav>
    <!-- END EMAL SIDEBAR MENU -->
 ```
Controller and Directive
// File: assets/js/apps/email/email.js
'use strict';

/* Controllers */

angular.module('app')
    // Email controller 
    .controller('EmailListCtrl', ['$scope', 'emails', '$stateParams', '$state', '$timeout', '$window',
        function($scope, emails, $stateParams, $state, $timeout, $window) {

            var w = angular.element($window);


            emails.all().then(function(list) {
                $scope.emails = list;
            });

            $scope.EmailCtrl = function(arr) {
                return arr.join();
            }
            $scope.formatBody = function(body) {
                return body.replace(/<(?:.|\n)*?>/gm, '');
            }
            $scope.view = function(id) {
                $state.go('app.email.inbox', {
                    'emailId': id
                })
                $timeout(function() {
                    if ($.Pages.isVisibleSm() || $.Pages.isVisibleXs()) {
                        $('.email-list').toggleClass('slideLeft');
                    }
                });
            };
            $scope.showInbox = function() {
                $('.email-list').removeClass('slideLeft');
            }

            w.bind('resize', function() {
                if (w.width() <= 1024) {
                    $('.email-sidebar').hide();

                } else {
                    $('.email-list').length && $('.email-list').removeClass('slideLeft');
                    $('.email-sidebar').show();
                }
            });

        }
    ])

.controller('EmailViewCtrl', ['$scope', 'emails', '$stateParams', '$sce', function($scope, emails, $stateParams, $sce) {

    $stateParams.emailId && emails.find($stateParams.emailId).then(function(email) {
        $scope.email = email;
        $scope.emailHTML = $sce.trustAsHtml(email.body);
    });



}]);

/* Directives */

angular.module('app')
    .directive('emailComposer', function() {
        return {
            restrict: 'A',
            link: function(scope, element, attrs) {
                // Email composer
                var emailComposerToolbarTemplate = {
                    "font-styles": function(locale) {
                        return '<li class="dropdown">' + '<a data-toggle="dropdown" class="btn btn-default dropdown-toggle ">' + '<span class="editor-icon editor-icon-headline"></span>' + '<span class="current-font">Normal</span>' + '<b class="caret"></b>' + '</a>' + '<ul class="dropdown-menu">' + '<li><a tabindex="-1" data-wysihtml5-command-value="p" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Normal</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h1" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">1</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h2" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">2</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h3" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">3</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h4" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">4</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h5" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">5</a></li>' + '<li><a tabindex="-1" data-wysihtml5-command-value="h6" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">6</a></li>' + '</ul>' + '</li>';
                    },
                    emphasis: function(locale) {
                        return '<li>' + '<div class="btn-group">' + '<a tabindex="-1" title="CTRL+B" data-wysihtml5-command="bold" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-bold"></i></a>' + '<a tabindex="-1" title="CTRL+I" data-wysihtml5-command="italic" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-italic"></i></a>' + '<a tabindex="-1" title="CTRL+U" data-wysihtml5-command="underline" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-underline"></i></a>' + '</div>' + '</li>';
                    },
                    blockquote: function(locale) {
                        return '<li>' + '<a tabindex="-1" data-wysihtml5-display-format-name="false" data-wysihtml5-command-value="blockquote" data-wysihtml5-command="formatBlock" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-quote"></i>' + '</a>' + '</li>'
                    },
                    lists: function(locale) {
                        return '<li>' + '<div class="btn-group">' + '<a tabindex="-1" title="Unordered list" data-wysihtml5-command="insertUnorderedList" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-ul"></i></a>' + '<a tabindex="-1" title="Ordered list" data-wysihtml5-command="insertOrderedList" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-ol"></i></a>' + '<a tabindex="-1" title="Outdent" data-wysihtml5-command="Outdent" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-outdent"></i></a>' + '<a tabindex="-1" title="Indent" data-wysihtml5-command="Indent" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-indent"></i></a>' + '</div>' + '</li>'
                    },
                    image: function(locale) {
                        return '<li>' + '<div class="bootstrap-wysihtml5-insert-image-modal modal fade">' + '<div class="modal-dialog ">' + '<div class="modal-content">' + '<div class="modal-header">' + '<a data-dismiss="modal" class="close">×</a>' + '<h3>Insert image</h3>' + '</div>' + '<div class="modal-body">' + '<input class="bootstrap-wysihtml5-insert-image-url form-control" value="http://">' + '</div>' + '<div class="modal-footer">' + '<a data-dismiss="modal" class="btn btn-default">Cancel</a>' + '<a data-dismiss="modal" class="btn btn-primary">Insert image</a>' + '</div>' + '</div>' + '</div>' + '</div>' + '<a tabindex="-1" title="Insert image" data-wysihtml5-command="insertImage" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-image"></i>' + '</a>' + '</li>'
                    },
                    link: function(locale) {
                        return '<li>' + '<div class="bootstrap-wysihtml5-insert-link-modal modal fade">' + '<div class="modal-dialog ">' + '<div class="modal-content">' + '<div class="modal-header">' + '<a data-dismiss="modal" class="close">×</a>' + '<h3>Insert link</h3>' + '</div>' + '<div class="modal-body">' + '<input class="bootstrap-wysihtml5-insert-link-url form-control" value="http://">' + '<label class="checkbox"> <input type="checkbox" checked="" class="bootstrap-wysihtml5-insert-link-target">Open link in new window</label>' + '</div>' + '<div class="modal-footer">' + '<a data-dismiss="modal" class="btn btn-default">Cancel</a>' + '<a data-dismiss="modal" class="btn btn-primary" href="">Insert link</a>' + '</div>' + '</div>' + '</div>' + '</div>' + '<a tabindex="-1" title="Insert link" data-wysihtml5-command="createLink" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-link"></i>' + '</a>' + '</li>'
                    },
                    html: function(locale) {
                        return '<li>' + '<div class="btn-group">' + '<a tabindex="-1" title="Edit HTML" data-wysihtml5-action="change_view" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-html"></i>' + '</a>' + '</div>' + '</li>'
                    }
                }

                setTimeout(function() {
                    var emailBody = $(element).find('.email-body');
                    emailBody.length && emailBody.wysihtml5({
                        html: true,
                        stylesheets: ["pages/css/editor.css"],
                        customTemplates: emailComposerToolbarTemplate
                    });

                    $(element).find('.wysihtml5-toolbar').appendTo('.email-toolbar-wrapper');
                }, 500);
            }
        }
    })

.directive('replyEditor', function() {
    // Wysiwyg editor custom options

    var editorTemplate = {
        "font-styles": function(locale) {
            return '<li class="dropdown dropup">' + '<a data-toggle="dropdown" class="btn btn-default dropdown-toggle ">    <span class="glyphicon glyphicon-font"></span>    <span class="current-font">Normal text</span>    <b class="caret"></b>  </a>' + '<ul class="dropdown-menu">    <li><a tabindex="-1" data-wysihtml5-command-value="p" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Normal text</a></li>     <li><a tabindex="-1" data-wysihtml5-command-value="h1" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 1</a></li>    <li><a tabindex="-1" data-wysihtml5-command-value="h2" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 2</a></li>    <li><a tabindex="-1" data-wysihtml5-command-value="h3" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 3</a></li>    <li><a tabindex="-1" data-wysihtml5-command-value="h4" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 4</a></li>    <li><a tabindex="-1" data-wysihtml5-command-value="h5" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 5</a></li>    <li><a tabindex="-1" data-wysihtml5-command-value="h6" data-wysihtml5-command="formatBlock" href="javascript:;" unselectable="on">Heading 6</a></li>  </ul>' + '</li>';
        },
        emphasis: function(locale) {
            return '<li>' + '<div class="btn-group">' + '<a tabindex="-1" title="CTRL+B" data-wysihtml5-command="bold" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-bold"></i></a>' + '<a tabindex="-1" title="CTRL+I" data-wysihtml5-command="italic" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-italic"></i></a>' + '<a tabindex="-1" title="CTRL+U" data-wysihtml5-command="underline" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-underline"></i></a>' + '</div>' + '</li>';
        },
        blockquote: function(locale) {
            return '<li>' + '<a tabindex="-1" data-wysihtml5-display-format-name="false" data-wysihtml5-command-value="blockquote" data-wysihtml5-command="formatBlock" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-quote"></i>' + '</a>' + '</li>'
        },
        lists: function(locale) {
            return '<li>' + '<div class="btn-group">' + '<a tabindex="-1" title="Unordered list" data-wysihtml5-command="insertUnorderedList" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-ul"></i></a>' + '<a tabindex="-1" title="Ordered list" data-wysihtml5-command="insertOrderedList" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-ol"></i></a>' + '<a tabindex="-1" title="Outdent" data-wysihtml5-command="Outdent" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-outdent"></i></a>' + '<a tabindex="-1" title="Indent" data-wysihtml5-command="Indent" class="btn  btn-default" href="javascript:;" unselectable="on"><i class="editor-icon editor-icon-indent"></i></a>' + '</div>' + '</li>'
        },
        image: function(locale) {
            return '<li>' + '<div class="bootstrap-wysihtml5-insert-image-modal modal fade">' + '<div class="modal-dialog ">' + '<div class="modal-content">' + '<div class="modal-header">' + '<a data-dismiss="modal" class="close">×</a>' + '<h3>Insert image</h3>' + '</div>' + '<div class="modal-body">' + '<input class="bootstrap-wysihtml5-insert-image-url form-control" value="http://">' + '</div>' + '<div class="modal-footer">' + '<a data-dismiss="modal" class="btn btn-default">Cancel</a>' + '<a data-dismiss="modal" class="btn btn-primary">Insert image</a>' + '</div>' + '</div>' + '</div>' + '</div>' + '<a tabindex="-1" title="Insert image" data-wysihtml5-command="insertImage" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-image"></i>' + '</a>' + '</li>'
        },
        link: function(locale) {
            return '<li>' + '<div class="bootstrap-wysihtml5-insert-link-modal modal fade">' + '<div class="modal-dialog ">' + '<div class="modal-content">' + '<div class="modal-header">' + '<a data-dismiss="modal" class="close">×</a>' + '<h3>Insert link</h3>' + '</div>' + '<div class="modal-body">' + '<input class="bootstrap-wysihtml5-insert-link-url form-control" value="http://">' + '<div class="checkbox check-success"> <input type="checkbox" class="bootstrap-wysihtml5-insert-link-target" checked="checked" value="1" id="link-checkbox"> <label for="link-checkbox">Open link in new window</label></div>' + '</div>' + '<div class="modal-footer">' + '<a data-dismiss="modal" class="btn btn-default">Cancel</a>' + '<a data-dismiss="modal" class="btn btn-primary" href="">Insert link</a>' + '</div>' + '</div>' + '</div>' + '</div>' + '<a tabindex="-1" title="Insert link" data-wysihtml5-command="createLink" class="btn  btn-default" href="javascript:;" unselectable="on">' + '<i class="editor-icon editor-icon-link"></i>' + '</a>' + '</li>'
        }
    }

    var editorOptions = {
        "font-styles": true, //Font styling, e.g. h1, h2, etc. Default true
        "emphasis": true, //Italics, bold, etc. Default true
        "lists": false, //(Un)ordered lists, e.g. Bullets, Numbers. Default true
        "html": false, //Button which allows you to edit the generated HTML. Default false
        "link": true, //Button to insert a link. Default true
        "image": true, //Button to insert an image. Default true,
        "color": false, //Button to change color of font  
        "blockquote": true, //Blockquote  
        stylesheets: ["pages/css/editor.css"],
        customTemplates: editorTemplate
    };

    return {
        restrict: 'A',
        link: function(scope, element, attrs) {
            !$(element).data('wysihtml5') && $(element).wysihtml5(editorOptions);
        }
    }
});
Services
Service to retrieve email list from an API. For this demo we're loading a local JSON file (explained above in jQuery section)
// File: assets/js/apps/email/service.js
angular.module('app')
    .factory('emails', function($http) {

        var list = $http.get('assets/js/apps/email/emails.json').then(function(response) {
            return response.data.emails;
        });
        var emails = {
            all: function() {
                return list;
            },
            find: function(id) {
                return list.then(function(list) {
                    for (var i = 0; i < list.length; i++) {
                        for (var j = 0; j < list[i].list.length; j++) {
                            if (list[i].list[j].id == id)
                                return list[i].list[j];
                        }
                    }
                })
            }
        };
        return emails;
    });

For help and bug report please contact support@revox.io