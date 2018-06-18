---
title: Guidelines to Create a Widget
tags: 
homepage: 
toc: true
sidebar: product1_sidebar
permalink: create_widget.html
---

To create a new widget in Hygieia:

1. Model your widget after one of the existing widgets, such as the deploy or build widget available at `/UI/src/components/widgets/`. Customize your module, config, style, view, html,  and ".js" files as needed.

2. In the `UI/src/components/templates/` directory, add the following section in the `capone.html` template to match the widget you are building:


```html
<div class="container-fluid" widget-container dashboard="ctrl.dashboard" ng-if="template.widgetView == 'your-widget-name'">
        <div class="row">
            <div class="col-xs-12">
                <widget name="your-widget-name" widget-title="Your-widget-title"></widget>
            </div>
        </div>
    </div>
```