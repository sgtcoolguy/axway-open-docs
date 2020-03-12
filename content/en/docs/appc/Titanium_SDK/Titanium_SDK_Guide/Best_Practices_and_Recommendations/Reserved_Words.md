{"title":"Reserved Words","weight":"70"}

* [Overview](#Overview)

* [ECMAScript Specification](#ECMAScriptSpecification)

* [iOS](#iOS)

* [Alloy](#Alloy)


## Overview

This article lists keywords that may not be used as variables, functions, methods, or object identifiers, because either Titanium or another source specifies its usage.

## ECMAScript Specification

The following keywords cannot be used as identifiers according to the ECMAScript Language Specification:

* abstract

* boolean

* break

* byte

* case

* catch

* char

* class

* const

* continue

* debugger

* default

* delete

* do

* double

* else

* enum

* export

* extends

* finally


* for

* function

* goto

* if

* implements

* import

* in

* instanceof

* int

* interface

* let

* long

* native

* new

* package

* private

* protected

* public

* return

* short


* static

* super

* switch

* synchronized

* this

* throw

* throws

* transient

* try

* typeof

* with

* while

* var

* void

* volatile

* yield


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
