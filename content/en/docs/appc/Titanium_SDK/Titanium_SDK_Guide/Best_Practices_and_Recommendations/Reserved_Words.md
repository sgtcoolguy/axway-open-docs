{"title":"Reserved Words","weight":"70"}

* [Overview](#overview)

* [ECMAScript Specification](#ecmascript-specification)

* [iOS](#ios)

* [Alloy](#alloy)

## Overview

This article lists keywords that may not be used as variables, functions, methods, or object identifiers, because either Titanium or another source specifies its usage.

## ECMAScript Specification

The following keywords cannot be used as identifiers according to the ECMAScript Language Specification:

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><ul class=" "><li class=" "><p><tt class=" ">abstract</tt></p></li><li class=" "><p><tt class=" ">boolean</tt></p></li><li class=" "><p><tt class=" ">break</tt></p></li><li class=" "><p><tt class=" ">byte</tt></p></li><li class=" "><p><tt class=" ">case</tt></p></li><li class=" "><p><tt class=" ">catch</tt></p></li><li class=" "><p><tt class=" ">char</tt></p></li><li class=" "><p><tt class=" ">class</tt></p></li><li class=" "><p><tt class=" ">const</tt></p></li><li class=" "><p><tt class=" ">continue</tt></p></li><li class=" "><p><tt class=" ">debugger</tt></p></li><li class=" "><p><tt class=" ">default</tt></p></li><li class=" "><p><tt class=" ">delete</tt></p></li><li class=" "><p><tt class=" ">do</tt></p></li><li class=" "><p><tt class=" ">double</tt></p></li><li class=" "><p><tt class=" ">else</tt></p></li><li class=" "><p><tt class=" ">enum</tt></p></li><li class=" "><p><tt class=" ">export</tt></p></li><li class=" "><p><tt class=" ">extends</tt></p></li><li class=" "><p><tt class=" ">finally</tt></p></li></ul></td><td class="confluenceTd" rowspan="1" colspan="1"><ul class=" "><li class=" "><p><tt class=" ">for</tt></p></li><li class=" "><p><tt class=" ">function</tt></p></li><li class=" "><p><tt class=" ">goto</tt></p></li><li class=" "><p><tt class=" ">if</tt></p></li><li class=" "><p><tt class=" ">implements</tt></p></li><li class=" "><p><tt class=" ">import</tt></p></li><li class=" "><p><tt class=" ">in</tt></p></li><li class=" "><p><tt class=" ">instanceof</tt></p></li><li class=" "><p><tt class=" ">int</tt></p></li><li class=" "><p><tt class=" ">interface</tt></p></li><li class=" "><p><tt class=" ">let</tt></p></li><li class=" "><p><tt class=" ">long</tt></p></li><li class=" "><p><tt class=" ">native</tt></p></li><li class=" "><p><tt class=" ">new</tt></p></li><li class=" "><p><tt class=" ">package</tt></p></li><li class=" "><p><tt class=" ">private</tt></p></li><li class=" "><p><tt class=" ">protected</tt></p></li><li class=" "><p><tt class=" ">public</tt></p></li><li class=" "><p><tt class=" ">return</tt></p></li><li class=" "><p><tt class=" ">short</tt></p></li></ul></td><td class="confluenceTd" rowspan="1" colspan="1"><ul class=" "><li class=" "><p><tt class=" ">static</tt></p></li><li class=" "><p><tt class=" ">super</tt></p></li><li class=" "><p><tt class=" ">switch</tt></p></li><li class=" "><p><tt class=" ">synchronized</tt></p></li><li class=" "><p><tt class=" ">this</tt></p></li><li class=" "><p><tt class=" ">throw</tt></p></li><li class=" "><p><tt class=" ">throws</tt></p></li><li class=" "><p><tt class=" ">transient</tt></p></li><li class=" "><p><tt class=" ">try</tt></p></li><li class=" "><p><tt class=" ">typeof</tt></p></li><li class=" "><p><tt class=" ">with</tt></p></li><li class=" "><p><tt class=" ">while</tt></p></li><li class=" "><p><tt class=" ">var</tt></p></li><li class=" "><p><tt class=" ">void</tt></p></li><li class=" "><p><tt class=" ">volatile</tt></p></li><li class=" "><p><tt class=" ">yield</tt></p></li></ul></td></tr></tbody></table>

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
