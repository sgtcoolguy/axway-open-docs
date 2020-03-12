{"title":"Axway Appcelerator Product Lifecycle","weight":"10"}

* [Overview](#Overview)

* [Release distribution phases (nominal timelines)](#Releasedistributionphases(nominaltimelines))

  * [Technology Preview](#TechnologyPreview)

  * [Restricted Availability](#RestrictedAvailability)

  * [Release Candidate](#ReleaseCandidate)

  * [General Availability (full support)](#GeneralAvailability(fullsupport))

  * [Supported (maintenance support)](#Supported(maintenancesupport))

  * [End of Support](#EndofSupport)

* [Versioning scheme](#Versioningscheme)

  * [Major (X)](#Major(X))

  * [Minor (Y)](#Minor(Y))

  * [Patch (Z)](#Patch(Z))

  * [Versioning summary](#Versioningsummary)

* [Nominal Lifetimes](#NominalLifetimes)

  * [Major release](#Majorrelease)

  * [Minor release](#Minorrelease)

  * [Patch release](#Patchrelease)

* [End of Support (EoS) examples](#EndofSupport(EoS)examples)

  * [Major EoS](#MajorEoS)

  * [Minor EoS](#MinorEoS)

  * [Patch EoS](#PatchEoS)

* [Cloud Services](#CloudServices)


## Overview

A product is a tightly integrated software entity that follows a discrete lifecycle. Each product has an independent lifecycle versus other products. A product is made concrete via the delivery of subsequent releases.

A release is a concrete product deliverable encompassing a coherent set of features, including product documentation. Release and documentation are identified by a unique version number.

## Release distribution phases (nominal timelines)

### Technology Preview

Technology Preview is an option for some new products or components where this status can be used to receive feedback from customers willing to test functionality and provide feedback during the development process. The functionality may not be functionally complete, and there is no commitment for a seamless upgrade to subsequent releases or that the functionality will move to [General Availability](#GeneralAvailability(fullsupport)). Technology Preview is not production-ready and does not receive full support.

### Restricted Availability

Restricted Availability marks the phase during which a release is distributed to a small and limited number of customers, selected by Axway Appcelerator prior to [General Availability](#GeneralAvailability(fullsupport)). The release is fully tested and can be deployed in production. Security, critical bug fixes, and small enhancements may be made available.

### Release Candidate

A release candidate (RC) is a beta version that includes features that will potentially be in the [General Availability](#GeneralAvailability(fullsupport)) release. Release Candidates are usually stable and available before [General Availability](#GeneralAvailability(fullsupport)). They may include bugs and is not intended for production use and does not receive full support. Release candidates users are highly encouraged to provide feedback when testing RCs.

### General Availability (full support)

General Availability marks the start of the phase during which the release is available without restrictions. Marks the start of the [full support](#Supported(maintenancesupport)) phase.

### Supported (maintenance support)

Supported is the phase during which a release is only eligible for general maintenance and support and no longer available for sale or enhancements. At the end of the Supported period, the release is changed to [End of Support](#EndofSupport) or End of Life (EOL) status. The supported period is only applicable to Major releases.

### End of Support

End of Support is for a release that is withdrawn from general support and represents the final status of any release. An End of Support release is also no longer available for sale.

## Versioning scheme

The version number of a release is split into three levels: [major](#Major(X)), [minor](#Minor(Y)), and [patch](#Patch(Z)).

### Major (X)

A major release indicates significant changes in architecture, functionality, features, and new operating environments. These changes can imply functional incompatibilities with previous releases.

### Minor (Y)

A minor release indicates significant new functionalities and major enhancements along with defect (bug) corrections. Compatibility between minor releases is provided.

### Patch (Z)

Patch releases may be made available to deliver bug fixes, corrections, minor enhancements. Each patch release is compatible with the previous minor and patch release. The new minor release supersedes the previous one; no more support on the previous one.

### Versioning summary

Here are a few examples of what versioning would like look with the Axway Appcelerator products:

* Axway Titanium SDK 6.1.1

* Axway Appcelerator CLI 6.2.2

* Axway Appcelerator Studio 4.9.0


## Nominal Lifetimes

Axway Appcelerator provides full support for the current minor release and the latest patch of the current major release.

### Major release

The nominal lifetime for a major release is 1 year of the Supported phase. A major release is moved from [General Availability](#GeneralAvailability(fullsupport)) (GA) full support to the Supported phase when the next major release is GA.

### Minor release

The nominal lifetime for a minor release is six months after the release of the next minor release.

### Patch release

The nominal lifetime for a patch release is only applicable to the latest GA release. The last GA patch release is fully supported, and there is not a Supported phase for previous patch releases.

## End of Support (EoS) examples

At the end of the Supported phase, the release is changed to [End of Support](#EndofSupport) or End of Life status.

### Major EoS

Axway Titanium SDK release 6.0.0 went GA on November 2016, then the previous major release 5.5.1 starts the Supported phase for 1 year until November 2017, then it reaches End of Support. On the first day of November 2017, Axway Titanium SDK 5.5.1 release no longer has maintenance support.

### Minor EoS

Axway Titanium SDK release 6.0.z gets six months of maintenance support after 6.1.z is released, version 6.1.z gets six months of maintenance support after 6.2.z is released, and so on.

### Patch EoS

Patch release 6.0.1 is no longer supported after 6.0.2 is GA. Note that the major and minor releases continue to be supported according to their nominal lifetime.

## Cloud Services

For Axway Appcelerator product available on-line such as [Axway Appcelerator Dashboard](/docs/appc/Appcelerator_Dashboard/), [Axway Mobile Analytics](/docs/appc/AMPLIFY_Appcelerator_Services/AMPLIFY_Appcelerator_Services_Guide/Appcelerator_Analytics/), and [Axway API Builder](/docs/appc/Axway_API_Builder/), since it is a Software-as-a-Service (SaaS) model, Axway deploys the latest version of every product online. All users get access only to the latest version of the product, and there are no exceptions for customers staying on previous releases. The previous [nominal timelines](#Releasedistributionphases(nominaltimelines)) section does not apply to Cloud Services.
