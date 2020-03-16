{"title":"Using Custom Conditional Statements in Titanium Alloy Views","weight":"20"}

One of the many great features of Alloy is how it separates the business logic of an app and the user interface. You use XML views and TSS files to define the elements and styling of your views, and controllers contain the JavaScript to make everything work.

One challenge that comes up from time to time is how to hide and show content in a view based on a condition within the app. For example, showing or hiding content when a view opens based on wether the user has logged in or not.

Here’s a simple example that shows a View that has two visual states — one where it shows the user is logged in and one when they’re not.

In this example, there’s some additional TSS that’s used allowing views and windows to use a vertical layout and the View tag has been set to have a default height and width of Ti.UI.SIZE.

`<``Alloy``>`

`<``Window``>`

`<``View`  `class``=``"container indent"``>`

`<``View`  `id``=``"notLoggedIn"`  `class``=``"vertical"``>`

`<``Label`  `text``=``"Not logged in"` `/>`

`</``View``>`

`<``View`  `id``=``"loggedIn"`  `class``=``"vertical"``>`

`<``Label`  `text``=``"Logged in"` `/>`

`</``View``>`

`</``View``>`

`</``Window``>`

`</``Alloy``>`

In this example, one usually handles hiding and showing content using some JavaScript code in the controller based on calling a method in the alloy.js file called Alloy.Globals.isLoggedIn:

`if` `(Alloy.Globals.isLoggedIn()) {`

`$.loggedIn.show();`

`$.notLoggedIn.hide();`

`}` `else` `{`

`$.loggedIn.show();`

`$.notLoggedIn.hide();`

`}`

This kind of works in terms of the showing and hiding of elements, but the problem is that both views were rendered to the view when it opened, and _then_ the visibility changed. This means that if the user isn’t logged in, there’s a big white space above the non-logged-in view.

The “classic” way of dealing with this was to not use show/hide at all but to change the heights:

`if` `(Alloy.Globals.isLoggedIn()) {`

`$.loggedIn.setHeight(Ti.UI.SIZE);`

`$.notLoggedIn.setHeight(0);`

`}` `else` `{`

`$.loggedIn.setHeight(0);`

`$.notLoggedIn.setHeight(Ti.UI.SIZE);`

`}`

This works, but it’s messy. We’re also assuming that the default setting of each view should be Ti.UI.SIZE which isn’t ideal.

Thankfully, there’s a simple to do this with Alloy using IF attributes _within_ the XML View.

Let’s update our View XML:

`<``Alloy``>`

`<``Window``>`

`<``View`  `class``=``"container indent"``>`

`<``View`  `if``=``"Alloy.Globals.isLoggedIn()"`  `id``=``"notLoggedIn"`  `class``=``"vertical"``>`

`<``Label`  `text``=``"Not logged in"` `/>`

`</``View``>`

`<``View`  `if``=``"!Alloy.Globals.isLoggedIn()"`  `id``=``"loggedIn"`  `class``=``"vertical"``>`

`<``Label`  `text``=``"Logged in"` `/>`

`</``View``>`

`</``View``>`

`</``Window``>`

`</``Alloy``>`

You’ll notice a couple of things — we’ve added an IF attribute to the View element that calls a method called Alloy.Globals.isLoggedIn in alloy.js. You’ll also notice the second View if attribute prefixes the method with ! because we want that to show if the method returns false.

When creating the View, Alloy is checking the method and if it returns true, the first view is rendered, and if false, the second view. What’s nice about this is that it only renders one or the other — so there’s no white space anymore.

Similarly, you can use IF attributes in TSS definitions to change the way elements display based on custom properties or methods, for example:

`"#info[if=Alloy.Globals.isIos7Plus]"``: {`

`font``: {`

`textStyle : Ti.UI.TEXT_STYLE_FOOTNOTE`

`}`

`},`

`"#title[if=Alloy.Globals.isIos7Plus]"``: {`

`top``:` `"25dp"``,`

`font``: {`

`textStyle : Ti.UI.TEXT_STYLE_HEADLINE`

`}`

`},`

`"#content[if=Alloy.Globals.isIos7Plus]"``: {`

`font``: {`

`textStyle : Ti.UI.TEXT_STYLE_CAPTION``1`

`}`

`},`

`"ScrollView[if=Alloy.Globals.iPhoneTall]"``: {`

`height``:` `"500dp"`

`}`

You can even use conditional queries by defining custom methods in your models in Alloy, and then render elements based on those methods when data-binding. In this example, a comment row is only displayed if a model has a method called shouldShowCommentRow which returns true:

`<``Alloy``>`

`<``TableViewRow`  `id``=``"commentRow"`  `hasChild``=``"false"`  `if``=``"$model.shouldShowCommentRow()"`  `onClick``=``"onSelectComment"``>`

`<``Label`  `id``=``"commentPlaceholderLabel"`  `class``=``"commentRowPreviewLabel placeholderLabel"`  `text``=``"Ti.App.L('AddComment')"` `/>`

`<``Label`  `id``=``"commentRowLabel"`  `class``=``"commentRowPreviewLabel"`  `text``=``"{Comment}"` `/>`

`</``TableViewRow``>;`

`</``Alloy``>`

As you can see, there’s lots of ways to use custom queries within Alloy, to reduce the amount of JavaScript you need to write and take advantage of these conditions running before any rendering is carried out, providing a smoother app experience.

You can find out more about buy checking out our guide on [Custom query styles](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_Styles_and_Themes/#custom-query-styles).
