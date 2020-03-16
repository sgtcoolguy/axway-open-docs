{"title":"Reserved Words","weight":"70"}

* [Overview](#overview)

* [ECMAScript Specification](#ecmascript-specification)

* [iOS](#ios)

* [Alloy](#alloy)

## Overview

This article lists keywords that may not be used as variables, functions, methods, or object identifiers, because either Titanium or another source specifies its usage.

## ECMAScript Specification

The following keywords cannot be used as identifiers according to the ECMAScript Language Specification:

<table class="confluenceTable"><thead class=""></thead><tfoot class=""></tfoot><tbody><tr><td class="confluenceTd" rowspan="1" colspan="1"><ul class=""><li class=""><p><tt>abstract</tt></p></li><li class=""><p><tt>boolean</tt></p></li><li class=""><p><tt>break</tt></p></li><li class=""><p><tt>byte</tt></p></li><li class=""><p><tt>case</tt></p></li><li class=""><p><tt>catch</tt></p></li><li class=""><p><tt>char</tt></p></li><li class=""><p><tt>class</tt></p></li><li class=""><p><tt>const</tt></p></li><li class=""><p><tt>continue</tt></p></li><li class=""><p><tt>debugger</tt></p></li><li class=""><p><tt>default</tt></p></li><li class=""><p><tt>delete</tt></p></li><li class=""><p><tt>do</tt></p></li><li class=""><p><tt>double</tt></p></li><li class=""><p><tt>else</tt></p></li><li class=""><p><tt>enum</tt></p></li><li class=""><p><tt>export</tt></p></li><li class=""><p><tt>extends</tt></p></li><li class=""><p><tt>finally</tt></p></li></ul></td><td class="confluenceTd" rowspan="1" colspan="1"><ul class=""><li class=""><p><tt>for</tt></p></li><li class=""><p><tt>function</tt></p></li><li class=""><p><tt>goto</tt></p></li><li class=""><p><tt>if</tt></p></li><li class=""><p><tt>implements</tt></p></li><li class=""><p><tt>import</tt></p></li><li class=""><p><tt>in</tt></p></li><li class=""><p><tt>instanceof</tt></p></li><li class=""><p><tt>int</tt></p></li><li class=""><p><tt>interface</tt></p></li><li class=""><p><tt>let</tt></p></li><li class=""><p><tt>long</tt></p></li><li class=""><p><tt>native</tt></p></li><li class=""><p><tt>new</tt></p></li><li class=""><p><tt>package</tt></p></li><li class=""><p><tt>private</tt></p></li><li class=""><p><tt>protected</tt></p></li><li class=""><p><tt>public</tt></p></li><li class=""><p><tt>return</tt></p></li><li class=""><p><tt>short</tt></p></li></ul></td><td class="confluenceTd" rowspan="1" colspan="1"><ul class=""><li class=""><p><tt>static</tt></p></li><li class=""><p><tt>super</tt></p></li><li class=""><p><tt>switch</tt></p></li><li class=""><p><tt>synchronized</tt></p></li><li class=""><p><tt>this</tt></p></li><li class=""><p><tt>throw</tt></p></li><li class=""><p><tt>throws</tt></p></li><li class=""><p><tt>transient</tt></p></li><li class=""><p><tt>try</tt></p></li><li class=""><p><tt>typeof</tt></p></li><li class=""><p><tt>with</tt></p></li><li class=""><p><tt>while</tt></p></li><li class=""><p><tt>var</tt></p></li><li class=""><p><tt>void</tt></p></li><li class=""><p><tt>volatile</tt></p></li><li class=""><p><tt>yield</tt></p></li></ul></td></tr></tbody></table>

## iOS

The following keywords are exposed to JavaScript from Objective C and may not be used as identifiers:

* \_configure

* \_destroy

* \_initProperties

* autorelease

* deadlock

* dealloc

* description

* id

* init

* release

* startup

## Alloy

Do not use double underscore prefixes on variables, properties, or function names (e.g., \_\_foo). They are reserved for use in Alloy.
