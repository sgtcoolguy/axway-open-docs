{"title":"ACS 2013 11 April Release Note","weight":"100"}

This update included the following bug fixes:

* Fixed a regression causing user confirmation email requests to fail with an error ("400 Bad Request - Invalid app key").

* When querying ACS objects, regular expressions are limited to those expressions that can be processed efficiently. To be processed efficiently, the regex must be _anchored_ at the beginning of the string with "^" followed by a letter or digit. The initial character must be case sensitive. For example, "^\[aA\]" and "._Foo" are not allowed, but "^a._Foo" is allowed.

* Website: Fixed an issue with creating places. When creating an event from the website, the place ID was not added to the event, even though a place is selected.

* Website: Fixed an issue with photo collections. If an error was encountered when browsing a sub-collection on the photo collection page, it caused an infinite redirect loop.
