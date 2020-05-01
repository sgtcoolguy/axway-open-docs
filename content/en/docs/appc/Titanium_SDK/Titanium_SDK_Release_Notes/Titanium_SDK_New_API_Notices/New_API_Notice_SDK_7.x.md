{"title":"New API Notice SDK 7.x","weight":"20"}

List of all new API notices for SDK 7.x.

* [SDK 7.x](#SDK7.x)

  * [7.5.0](#7.5.0)

  * [7.4.0](#7.4.0)

  * [7.3.1](#7.3.1)

  * [7.3.0](#7.3.0)

  * [7.2.1](#7.2.1)

  * [7.1.1](#7.1.1)

  * [7.1.0](#7.1.0)

  * [7.0.1](#7.0.1)

  * [7.0.0](#7.0.0)


## SDK 7.x

### 7.5.0

API

Type

Notes

Global.console.timeLog

method

Log duration taken so far for an operation. (New API, supported on Android, iPhone and iPad.)

Titanium.Android.Activity.userinteraction

event

Called whenever a key, touch, or trackball event is dispatched to the activity. (New API, supported on Android.)

Titanium.Android.NotificationChannel.getSound

method

Gets the value of the Titanium.Android.NotificationChannel.sound property. (New API, supported on Android.)

Titanium.Android.NotificationChannel.setSound

method

Sets the value of the Titanium.Android.NotificationChannel.sound property. (New API, supported on Android.)

Titanium.Android.NotificationChannel.sound

property

A URL to the sound to play. (New API, supported on Android.)

Titanium.App.Android.shortcutitemclick

event

Fired when a Titanium.UI.ShortcutItem is clicked. (New API, supported on Android.)

Titanium.App.shortcutitemclick

event

Fired when a Titanium.UI.ShortcutItem is clicked. (New API, supported on Android, iPhone and iPad.)

Titanium.App.trackUserInteraction

property

Indicates whether or not the user interaction shoud be tracked. (New API, supported on iPhone and iPad.)

Titanium.App.userinteraction

event

Called whenever an interaction with the window occurred. To be used together with the Titanium.App.trackUserInteraction property. (New API, supported on Android, iPhone and iPad.)

Titanium.Locale.change

event

Fired when the device locale changes. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_BUFFERING

property

Audio data is being buffered from the network. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_INITIALIZED

property

Audio playback is being initialized. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_PAUSED

property

Playback is paused. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_PLAYING

property

Audio playback is active. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_STARTING

property

Audio playback is starting. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_STOPPED

property

Audio playback is stopped. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_STOPPING

property

Audio playback is stopping. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_WAITING\_FOR\_DATA

property

Player is waiting for audio data from the network. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AUDIO\_STATE\_WAITING\_FOR\_QUEUE

property

Player is waiting for audio data to fill the queue. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AudioPlayer.allowsExternalPlayback

property

Indicates whether the player allows switching to "external playback" mode. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.complete

event

Fired when the audio has finished playing. (Added support for iPhone and iPad.)

Titanium.Media.AudioPlayer.externalPlaybackActive

property

Indicates whether the player is currently playing video in "external playback" mode. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.getAllowsExternalPlayback

method

Gets the value of the Titanium.Media.AudioPlayer.allowsExternalPlayback property. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.getExternalPlaybackActive

method

Gets the value of the Titanium.Media.AudioPlayer.externalPlaybackActive property. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.getMuted

method

Gets the value of the Titanium.Media.AudioPlayer.muted property. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AudioPlayer.getRate

method

Gets the value of the Titanium.Media.AudioPlayer.rate property. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.metadata

event

Fired when the timed metadata was encountered most recently within the media as it plays. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.muted

property

Indicates whether or not audio output of the player is muted. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AudioPlayer.rate

property

Indicates the desired rate of playback; 0.0 means "paused", 1.0 indicates a desire to play at the natural rate of the current item. In addition, 2.0would mean that the audio plays twice as fast. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.release

method

Stops buffering audio data and releases audio resources. (Added support for iPhone and iPad.)

Titanium.Media.AudioPlayer.restart

method

Restarts (stops and stars) audio playback. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AudioPlayer.seekToTime

method

Moves the playback cursor and invokes the specified block when the seek operation has either been completed or been interrupted. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.setAllowsExternalPlayback

method

Sets the value of the Titanium.Media.AudioPlayer.allowsExternalPlayback property. (New API, supported on iPhone and iPad.)

Titanium.Media.AudioPlayer.setMuted

method

Sets the value of the Titanium.Media.AudioPlayer.muted property. (New API, supported on Android, iPhone and iPad.)

Titanium.Media.AudioPlayer.setRate

method

Sets the value of the Titanium.Media.AudioPlayer.rate property. (New API, supported on iPhone and iPad.)

Titanium.Media.QUALITY\_640x480

property

Media type constant for medium-quality video recording. (Added support for Android.)

Titanium.Media.QUALITY\_HIGH

property

Media type constant for high-quality video recording. (Added support for Android.)

Titanium.Media.QUALITY\_IFRAME\_1280x720

property

Media type constant for medium-quality video recording. (Added support for Android.)

Titanium.Media.QUALITY\_LOW

property

Media type constant for low-quality video recording. (Added support for Android.)

Titanium.Media.getQUALITY\_640x480

method

Gets the value of the Titanium.Media.QUALITY\_640x480 property. (Added support for Android.)

Titanium.Media.getQUALITY\_IFRAME\_1280x720

method

Gets the value of the Titanium.Media.QUALITY\_IFRAME\_1280x720 property. (Added support for Android.)

Titanium.UI.ATTRIBUTE\_PARAGRAPH\_STYLE

property

Use with Attribute.type to manages the behaviour of string set. (New API, supported on iPhone and iPad.)

Titanium.UI.ActivityIndicator.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.ActivityIndicator.getAnchorPoint

method

Gets the value of the Titanium.UI.ActivityIndicator.anchorPoint property. (Added support for Android.)

Titanium.UI.ActivityIndicator.setAnchorPoint

method

Sets the value of the Titanium.UI.ActivityIndicator.anchorPoint property. (Added support for Android.)

Titanium.UI.AlertDialog.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.AlertDialog.buttonClickRequired

property

Setting this to true requires the end-user to click a dialog button to close the dialog. (New API, supported on Android.)

Titanium.UI.AlertDialog.getAnchorPoint

method

Gets the value of the Titanium.UI.AlertDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.AlertDialog.getButtonClickRequired

method

Gets the value of the Titanium.UI.AlertDialog.buttonClickRequired property. (New API, supported on Android.)

Titanium.UI.AlertDialog.setAnchorPoint

method

Sets the value of the Titanium.UI.AlertDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.AlertDialog.setButtonClickRequired

method

Sets the value of the Titanium.UI.AlertDialog.buttonClickRequired property. (New API, supported on Android.)

Titanium.UI.Android.FLAG\_TRANSLUCENT\_NAVIGATION

property

Window flag which makes the Android system's navigation bar semi-transparent. (New API, supported on Android.)

Titanium.UI.Android.FLAG\_TRANSLUCENT\_STATUS

property

Window flag which makes the Android system's top status bar semi-transparent. (New API, supported on Android.)

Titanium.UI.Android.ProgressIndicator.anchorPoint

property

Coordinate of the view about which to pivot an animation. (New API, supported on Android.)

Titanium.UI.Android.ProgressIndicator.getAnchorPoint

method

Gets the value of the Titanium.UI.Android.ProgressIndicator.anchorPoint property. (New API, supported on Android.)

Titanium.UI.Android.ProgressIndicator.setAnchorPoint

method

Sets the value of the Titanium.UI.Android.ProgressIndicator.anchorPoint property. (New API, supported on Android.)

Titanium.UI.Button.attributedString

property

Specify an attributed string for the label. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Button.getAttributedString

method

Gets the value of the Titanium.UI.Button.attributedString property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Button.setAttributedString

method

Sets the value of the Titanium.UI.Button.attributedString property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.EmailDialog.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.EmailDialog.getAnchorPoint

method

Gets the value of the Titanium.UI.EmailDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.EmailDialog.setAnchorPoint

method

Sets the value of the Titanium.UI.EmailDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.OptionDialog.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.OptionDialog.getAnchorPoint

method

Gets the value of the Titanium.UI.OptionDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.OptionDialog.setAnchorPoint

method

Sets the value of the Titanium.UI.OptionDialog.anchorPoint property. (Added support for Android.)

Titanium.UI.Picker.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.Picker.getAnchorPoint

method

Gets the value of the Titanium.UI.Picker.anchorPoint property. (Added support for Android.)

Titanium.UI.Picker.setAnchorPoint

method

Sets the value of the Titanium.UI.Picker.anchorPoint property. (Added support for Android.)

Titanium.UI.ScrollableView.clipViews

property

Determines whether the previous and next pages are clipped, so that they are not visibleadjacent to the current page. (Added support for Android.)

Titanium.UI.ScrollableView.getClipViews

method

Gets the value of the Titanium.UI.ScrollableView.clipViews property. (Added support for Android.)

Titanium.UI.ScrollableView.getPadding

method

Gets the value of the Titanium.UI.ScrollableView.padding property. (New API, supported on Android.)

Titanium.UI.ScrollableView.padding

property

The padding applied to the scrollable view. (New API, supported on Android.)

Titanium.UI.ScrollableView.setClipViews

method

Sets the value of the Titanium.UI.ScrollableView.clipViews property. (Added support for Android.)

Titanium.UI.ScrollableView.setPadding

method

Sets the value of the Titanium.UI.ScrollableView.padding property. (New API, supported on Android.)

Titanium.UI.SearchBar.fieldBackgroundDisabledImage

property

Background image of the text field in disabled state, specified as a local file path or URL. (New API, supported on iPhone and iPad.)

Titanium.UI.SearchBar.fieldBackgroundImage

property

Background image of the text field, specified as a local file path or URL. (New API, supported on iPhone and iPad.)

Titanium.UI.SearchBar.getFieldBackgroundDisabledImage

method

Gets the value of the Titanium.UI.SearchBar.fieldBackgroundDisabledImage property. (New API, supported on iPhone and iPad.)

Titanium.UI.SearchBar.getFieldBackgroundImage

method

Gets the value of the Titanium.UI.SearchBar.fieldBackgroundImage property. (New API, supported on iPhone and iPad.)

Titanium.UI.SearchBar.setFieldBackgroundDisabledImage

method

Sets the value of the Titanium.UI.SearchBar.fieldBackgroundDisabledImage property. (New API, supported on iPhone and iPad.)

Titanium.UI.SearchBar.setFieldBackgroundImage

method

Sets the value of the Titanium.UI.SearchBar.fieldBackgroundImage property. (New API, supported on iPhone and iPad.)

Titanium.UI.ShortcutItem

object

An application shortcut. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Tab.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.Tab.getAnchorPoint

method

Gets the value of the Titanium.UI.Tab.anchorPoint property. (Added support for Android.)

Titanium.UI.Tab.setAnchorPoint

method

Sets the value of the Titanium.UI.Tab.anchorPoint property. (Added support for Android.)

Titanium.UI.TabGroup.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.TabGroup.getAnchorPoint

method

Gets the value of the Titanium.UI.TabGroup.anchorPoint property. (Added support for Android.)

Titanium.UI.TabGroup.setAnchorPoint

method

Sets the value of the Titanium.UI.TabGroup.anchorPoint property. (Added support for Android.)

Titanium.UI.TextArea.getLines

method

Gets the value of the Titanium.UI.TextArea.lines property. (New API, supported on Android.)

Titanium.UI.TextArea.getMaxLines

method

Gets the value of the Titanium.UI.TextArea.maxLines property. (New API, supported on Android.)

Titanium.UI.TextArea.lines

property

Number of lines tall the text area height will be, if set. (New API, supported on Android.)

Titanium.UI.TextArea.maxLines

property

Maximum line count of text field input. (New API, supported on Android.)

Titanium.UI.TextArea.setLines

method

Sets the value of the Titanium.UI.TextArea.lines property. (New API, supported on Android.)

Titanium.UI.TextArea.setMaxLines

method

Sets the value of the Titanium.UI.TextArea.maxLines property. (New API, supported on Android.)

Titanium.UI.TextField.getPasswordRules

method

Gets the value of the Titanium.UI.TextField.passwordRules property. (New API, supported on iPhone and iPad.)

Titanium.UI.TextField.passwordRules

property

Set password rules that should be used for this text field. (New API, supported on iPhone and iPad.)

Titanium.UI.TextField.setPasswordRules

method

Sets the value of the Titanium.UI.TextField.passwordRules property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.anchorPoint

property

Coordinate of the view about which to pivot an animation. (Added support for Android.)

Titanium.UI.View.getAnchorPoint

method

Gets the value of the Titanium.UI.View.anchorPoint property. (Added support for Android.)

Titanium.UI.View.setAnchorPoint

method

Sets the value of the Titanium.UI.View.anchorPoint property. (Added support for Android.)

Titanium.UI.WebView.getMixedContentMode

method

Gets the value of the Titanium.UI.WebView.mixedContentMode property. (New API, supported on Android.)

Titanium.UI.WebView.getOnlink

method

Gets the value of the Titanium.UI.WebView.onlink property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.mixedContentMode

property

If true, allows the loading of insecure resources from a secure origin. (New API, supported on Android.)

Titanium.UI.WebView.onlink

property

Fired before navigating to a link. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.setMixedContentMode

method

Sets the value of the Titanium.UI.WebView.mixedContentMode property. (New API, supported on Android.)

Titanium.UI.WebView.setOnlink

method

Sets the value of the Titanium.UI.WebView.onlink property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Window.extendSafeArea

property

Specifies whether the screen insets/notches are allowed to overlap the window's content or not. (Added support for Android.)

Titanium.UI.Window.getExtendSafeArea

method

Gets the value of the Titanium.UI.Window.extendSafeArea property. (Added support for Android.)

Titanium.UI.Window.getHidesBackButton

method

Gets the value of the Titanium.UI.Window.hidesBackButton property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getSafeAreaPadding

method

Gets the value of the Titanium.UI.Window.safeAreaPadding property. (New API, supported on Android.)

Titanium.UI.Window.hidesBackButton

property

Set this to true to hide the back button of navigation bar. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.safeAreaPadding

property

The padding needed to safely display content without it being overlapped by the screen insets and notches. (New API, supported on Android.)

Titanium.UI.Window.setExtendSafeArea

method

Sets the value of the Titanium.UI.Window.extendSafeArea property. (Added support for Android.)

Titanium.UI.Window.setHidesBackButton

method

Sets the value of the Titanium.UI.Window.hidesBackButton property. (New API, supported on iPhone and iPad.)

Titanium.UI.createShortcutItem

method

Creates and returns an instance of Titanium.UI.ShortcutItem. (New API, supported on Android, iPhone and iPad.)

### 7.4.0

The following APIs are new or have expanded platform support in Release 7.4.0 as of September 17th, 2018.

API

Type

Notes

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_PROVISIONAL

property

The application is provisionally authorized to post non-interruptive user notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_TYPE\_CRITICAL\_ALERT

property

The ability to play sounds for critical alerts.Use with the types property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_TYPE\_PROVIDES\_APP\_NOTIFICATION\_SETTINGS

property

An option indicating the system should display a button for in-app notification settings.Use with the types property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_TYPE\_PROVISIONAL

property

The ability to post non-interrupting notifications provisionally to the Notification Center.Use with the types property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.deleteAllSavedUserActivities

method

Deletes all user activities created by your app. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.deleteSavedUserActivitiesForPersistentIdentifiers

method

Deletes user activities created by your app that have the specified persistent identifiers. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.eligibleForPrediction

property

A Boolean value that determines whether Siri can suggest the user activity as a shortcut to the user. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.getEligibleForPrediction

method

Gets the value of the Titanium.App.iOS.UserActivity.eligibleForPrediction property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.getPersistentIdentifier

method

Gets the value of the Titanium.App.iOS.UserActivity.persistentIdentifier property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.persistentIdentifier

property

A value used to identify the user activity. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.setEligibleForPrediction

method

Sets the value of the Titanium.App.iOS.UserActivity.eligibleForPrediction property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.setPersistentIdentifier

method

Sets the value of the Titanium.App.iOS.UserActivity.persistentIdentifier property. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserActivity.useractivitydeleted

event

Fired when the user activity get deleted using the Titanium.App.iOS.UserActivity.deleteAllSavedUserActivities or Titanium.App.iOS.UserActivity.deleteSavedUserActivitiesForPersistentIdentifiers methods. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserNotificationCategory.categorySummaryFormat

property

A format string for the summary description used when the system groups the category's notifications. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_NEW\_PASSWORD

property

Specifies the expectation of a new password. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ONE\_TIME\_CODE

property

Specifies the expectation of a single-factor SMS login code. (New API, supported on iPhone and iPad.)

### 7.3.1

The following APIs are new or have expanded platform support in Release 7.3.1 as of August 30th, 2018.

API

Type

Notes

Global.console.time

method

Start a timer to track duration of an operation. (New API, supported on Android, iPhone and iPad.)

Global.console.timeEnd

method

Stop a timer that was previously started. (New API, supported on Android, iPhone and iPad.)

Titanium.Android.R.animator

property

Animator resources. See R.animator in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.bool

property

Boolean resources. See R.bool in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.fraction

property

Fraction resources. See R.fraction in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.interpolator

property

Interpolator resources. See R.fraction in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.menu

property

Menu resources. See R.menu in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.mipmap

property

Mipmap resources. See R.mipmap in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.plurals

property

Plurals resources. See R.plurals in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.raw

property

Raw resources. See R.raw in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.transition

property

Transition resources. See R.transition in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.xml

property

XML resources. See R.xml in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.Service.foregroundCancel

method

Puts the service into the "background" state and removes its foreground notification. (New API, supported on Android.)

Titanium.Android.Service.foregroundNotify

method

Puts the service into the "foreground" state and displays a notification. (New API, supported on Android.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_ALERT

property

A alert dialog is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_BANNER

property

A banner is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_NONE

property

No banner or alert dialog is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_AUTHORIZED

property

The application is authorized to post user notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_DENIED

property

The application is not authorized to post user notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_NOT\_DETERMINED

property

The user has not yet made a choice regarding whether the application may postuser notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_ALLOW\_IN\_CARPLAY

property

Allow CarPlay to display notifications of this type. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_CUSTOM\_DISMISS\_ACTION

property

Send dismiss actions to the UNUserNotificationCenter object's delegate for handling. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_HIDDEN\_PREVIEWS\_SHOW\_SUBTITLE

property

Show the notification's subtitle, even if the user has disabled notification previews for the app. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_HIDDEN\_PREVIEWS\_SHOW\_TITLE

property

Show the notification's title, even if the user has disabled notification previews for the app. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_NONE

property

No options. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_DISABLED

property

The notification setting is turned off. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_ENABLED

property

The notification setting is turned on. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_NOT\_SUPPORTED

property

The application does not support this notification type. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserNotificationCenter

object

The top-level App iOS Notification Center module. It is used to control scheduled notificationsand receive details about the system-wide notification settings. (New API, supported on iPhone and iPad.)

Titanium.Filesystem.File.append

method

Appends data to the file identified by this file object. (Added support for Android.)

Titanium.Filesystem.File.copy

method

Copies the file identified by this file object to a new path. (Added support for iPhone and iPad.)

Titanium.Filesystem.File.createdAt

method

Returns the creation Date for the file identified by this file object. (Added support for Android, iPhone and iPad.)

Titanium.Filesystem.File.modifiedAt

method

Returns the last modification Date for the file identified by this file object. (Added support for Android, iPhone and iPad.)

Titanium.Geolocation.getShowBackgroundLocationIndicator

method

Gets the value of the Titanium.Geolocation.showBackgroundLocationIndicator property. (New API, supported on iPhone and iPad.)

Titanium.Geolocation.setShowBackgroundLocationIndicator

method

Sets the value of the Titanium.Geolocation.showBackgroundLocationIndicator property. (New API, supported on iPhone and iPad.)

Titanium.Geolocation.showBackgroundLocationIndicator

property

Specifies that an indicator be shown when the app makes use of continuous background location updates. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_CLEAR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR\_BURN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR\_DODGE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COPY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DARKEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_ATOP

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_IN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_OUT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_OVER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DIFFERENCE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_EXCLUSION

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_HARD\_LIGHT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_HUE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_LIGHTEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_LUMINOSITY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_MULTIPLY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_NORMAL

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_OVERLAY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_PLUS\_DARKER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_PLUS\_LIGHTER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SATURATION

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SCREEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOFT\_LIGHT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_ATOP

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_IN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_OUT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_XOR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.MaskedImage

object

A control that displays an image composited with a background image or color. (Added support for Android.)

Titanium.UI.TableView.getResultsBackgroundColor

method

Gets the value of the Titanium.UI.TableView.resultsBackgroundColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorColor

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorInsets

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorInsets property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorStyle

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorStyle property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getScrollable

method

Gets the value of the Titanium.UI.TableView.scrollable property. (Added support for Android.)

Titanium.UI.TableView.resultsBackgroundColor

property

The background color of the search results (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorColor

property

Separator line color between rows inside search results, as a color name or hex triplet (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorInsets

property

The insets for search results separators (applies to all cells & iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorStyle

property

The separator style of the search results (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.scrollable

property

If true, the tableview can be scrolled. (Added support for Android.)

Titanium.UI.TableView.setResultsBackgroundColor

method

Sets the value of the Titanium.UI.TableView.resultsBackgroundColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorColor

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorInsets

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorInsets property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorStyle

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorStyle property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setScrollable

method

Sets the value of the Titanium.UI.TableView.scrollable property. (Added support for Android.)

Titanium.UI.View.getHorizontalMotionEffect

method

Gets the value of the Titanium.UI.View.horizontalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.getVerticalMotionEffect

method

Gets the value of the Titanium.UI.View.verticalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.horizontalMotionEffect

property

Adds a horizontal parallax effect to the view (New API, supported on iPhone and iPad.)

Titanium.UI.View.setHorizontalMotionEffect

method

Sets the value of the Titanium.UI.View.horizontalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.setVerticalMotionEffect

method

Sets the value of the Titanium.UI.View.verticalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.verticalMotionEffect

property

Adds a vertical parallax effect to the view (New API, supported on iPhone and iPad.)

Titanium.UI.WebView.getZoomLevel

method

Gets the value of the Titanium.UI.WebView.zoomLevel property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.setZoomLevel

method

Sets the value of the Titanium.UI.WebView.zoomLevel property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.zoomLevel

property

Manage the zoom-level of the current page. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Window.getHomeIndicatorAutoHidden

method

Gets the value of the Titanium.UI.Window.homeIndicatorAutoHidden property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getNavigationWindow

method

Gets the value of the Titanium.UI.Window.navigationWindow property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.homeIndicatorAutoHidden

property

Boolean value indicating whether the system is allowed to hide the visual indicator for returning to the Home screen. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.navigationWindow

property

The Titanium.UI.iOS.NavigationWindow instance hosting this window. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setHomeIndicatorAutoHidden

method

Sets the value of the Titanium.UI.Window.homeIndicatorAutoHidden property. (New API, supported on iPhone and iPad.)

Titanium.UI.createMaskedImage

method

Creates and returns an instance of Titanium.UI.MaskedImage. (Added support for Android.)

Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT

property

View presented over its parent window. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN

property

Presented view covers the screen. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.setMODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT

method

Sets the value of the Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT property. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.setMODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN

method

Sets the value of the Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN property. (New API, supported on iPhone and iPad.)

### 7.3.0

The following APIs are new or have expanded platform support in Release 7.3.0 as of August 17th, 2018.

API

Type

Notes

Global.console.time

method

Start a timer to track duration of an operation. (New API, supported on Android, iPhone and iPad.)

Global.console.timeEnd

method

Stop a timer that was previously started. (New API, supported on Android, iPhone and iPad.)

Titanium.Android.R.animator

property

Animator resources. See R.animator in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.bool

property

Boolean resources. See R.bool in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.fraction

property

Fraction resources. See R.fraction in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.interpolator

property

Interpolator resources. See R.fraction in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.menu

property

Menu resources. See R.menu in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.mipmap

property

Mipmap resources. See R.mipmap in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.plurals

property

Plurals resources. See R.plurals in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.raw

property

Raw resources. See R.raw in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.transition

property

Transition resources. See R.transition in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.R.xml

property

XML resources. See R.xml in the Android Developer Reference. (New API, supported on Android.)

Titanium.Android.Service.foregroundCancel

method

Puts the service into the "background" state and removes its foreground notification. (New API, supported on Android.)

Titanium.Android.Service.foregroundNotify

method

Puts the service into the "foreground" state and displays a notification. (New API, supported on Android.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_ALERT

property

A alert dialog is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_BANNER

property

A banner is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_ALERT\_STYLE\_NONE

property

No banner or alert dialog is presented when the notification is received. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_AUTHORIZED

property

The application is authorized to post user notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_DENIED

property

The application is not authorized to post user notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_AUTHORIZATION\_STATUS\_NOT\_DETERMINED

property

The user has not yet made a choice regarding whether the application may postuser notifications. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_ALLOW\_IN\_CARPLAY

property

Allow CarPlay to display notifications of this type. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_CUSTOM\_DISMISS\_ACTION

property

Send dismiss actions to the UNUserNotificationCenter object's delegate for handling. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_HIDDEN\_PREVIEWS\_SHOW\_SUBTITLE

property

Show the notification's subtitle, even if the user has disabled notification previews for the app. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_HIDDEN\_PREVIEWS\_SHOW\_TITLE

property

Show the notification's title, even if the user has disabled notification previews for the app. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_CATEGORY\_OPTION\_NONE

property

No options. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_DISABLED

property

The notification setting is turned off. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_ENABLED

property

The notification setting is turned on. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.USER\_NOTIFICATION\_SETTING\_NOT\_SUPPORTED

property

The application does not support this notification type. (New API, supported on iPhone and iPad.)

Titanium.App.iOS.UserNotificationCenter

object

The top-level App iOS Notification Center module. It is used to control scheduled notificationsand receive details about the system-wide notification settings. (New API, supported on iPhone and iPad.)

Titanium.Filesystem.File.append

method

Appends data to the file identified by this file object. (Added support for Android.)

Titanium.Filesystem.File.copy

method

Copies the file identified by this file object to a new path. (Added support for iPhone and iPad.)

Titanium.Filesystem.File.createdAt

method

Returns the creation Date for the file identified by this file object. (Added support for Android, iPhone and iPad.)

Titanium.Filesystem.File.modifiedAt

method

Returns the last modification Date for the file identified by this file object. (Added support for Android, iPhone and iPad.)

Titanium.Geolocation.getShowBackgroundLocationIndicator

method

Gets the value of the Titanium.Geolocation.showBackgroundLocationIndicator property. (New API, supported on iPhone and iPad.)

Titanium.Geolocation.setShowBackgroundLocationIndicator

method

Sets the value of the Titanium.Geolocation.showBackgroundLocationIndicator property. (New API, supported on iPhone and iPad.)

Titanium.Geolocation.showBackgroundLocationIndicator

property

Specifies that an indicator be shown when the app makes use of continuous background location updates. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_CLEAR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR\_BURN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COLOR\_DODGE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_COPY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DARKEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_ATOP

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_IN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_OUT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DESTINATION\_OVER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_DIFFERENCE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_EXCLUSION

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_HARD\_LIGHT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_HUE

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_LIGHTEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_LUMINOSITY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_MULTIPLY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_NORMAL

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_OVERLAY

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_PLUS\_DARKER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_PLUS\_LIGHTER

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SATURATION

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SCREEN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOFT\_LIGHT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_ATOP

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_IN

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_SOURCE\_OUT

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.BLEND\_MODE\_XOR

property

Use with MaskedImage.mode to specify a blend mode. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.MaskedImage

object

A control that displays an image composited with a background image or color. (Added support for Android.)

Titanium.UI.TableView.getResultsBackgroundColor

method

Gets the value of the Titanium.UI.TableView.resultsBackgroundColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorColor

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorInsets

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorInsets property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getResultsSeparatorStyle

method

Gets the value of the Titanium.UI.TableView.resultsSeparatorStyle property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.getScrollable

method

Gets the value of the Titanium.UI.TableView.scrollable property. (Added support for Android.)

Titanium.UI.TableView.resultsBackgroundColor

property

The background color of the search results (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorColor

property

Separator line color between rows inside search results, as a color name or hex triplet (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorInsets

property

The insets for search results separators (applies to all cells & iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.resultsSeparatorStyle

property

The separator style of the search results (iOS-only). (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.scrollable

property

If true, the tableview can be scrolled. (Added support for Android.)

Titanium.UI.TableView.setResultsBackgroundColor

method

Sets the value of the Titanium.UI.TableView.resultsBackgroundColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorColor

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorColor property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorInsets

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorInsets property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setResultsSeparatorStyle

method

Sets the value of the Titanium.UI.TableView.resultsSeparatorStyle property. (New API, supported on iPhone and iPad.)

Titanium.UI.TableView.setScrollable

method

Sets the value of the Titanium.UI.TableView.scrollable property. (Added support for Android.)

Titanium.UI.View.getHorizontalMotionEffect

method

Gets the value of the Titanium.UI.View.horizontalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.getVerticalMotionEffect

method

Gets the value of the Titanium.UI.View.verticalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.horizontalMotionEffect

property

Adds a horizontal parallax effect to the view (New API, supported on iPhone and iPad.)

Titanium.UI.View.setHorizontalMotionEffect

method

Sets the value of the Titanium.UI.View.horizontalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.setVerticalMotionEffect

method

Sets the value of the Titanium.UI.View.verticalMotionEffect property. (New API, supported on iPhone and iPad.)

Titanium.UI.View.verticalMotionEffect

property

Adds a vertical parallax effect to the view (New API, supported on iPhone and iPad.)

Titanium.UI.WebView.getZoomLevel

method

Gets the value of the Titanium.UI.WebView.zoomLevel property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.setZoomLevel

method

Sets the value of the Titanium.UI.WebView.zoomLevel property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.WebView.zoomLevel

property

Manage the zoom-level of the current page. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.Window.getHomeIndicatorAutoHidden

method

Gets the value of the Titanium.UI.Window.homeIndicatorAutoHidden property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getNavigationWindow

method

Gets the value of the Titanium.UI.Window.navigationWindow property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.homeIndicatorAutoHidden

property

Boolean value indicating whether the system is allowed to hide the visual indicator for returning to the Home screen. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.navigationWindow

property

The Titanium.UI.iOS.NavigationWindow instance hosting this window. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setHomeIndicatorAutoHidden

method

Sets the value of the Titanium.UI.Window.homeIndicatorAutoHidden property. (New API, supported on iPhone and iPad.)

Titanium.UI.createMaskedImage

method

Creates and returns an instance of Titanium.UI.MaskedImage. (Added support for Android.)

Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT

property

View presented over its parent window. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN

property

Presented view covers the screen. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.setMODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT

method

Sets the value of the Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_CONTEXT property. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.setMODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN

method

Sets the value of the Titanium.UI.iOS.MODAL\_PRESENTATION\_OVER\_CURRENT\_FULL\_SCREEN property. (New API, supported on iPhone and iPad.)

### 7.2.1

The following APIs are new or have expanded platform support in Release 7.2.1 as of August 17th, 2018.

API

Type

Notes

Titanium.Analytics.getOptedOut

method

Gets the value of the Titanium.Analytics.optedOut property. (New API, supported on Android, iPhone, iPad and Windows Phone.)

Titanium.Analytics.optedOut

property

Allows the user to opt out from Analytics during runtime to comply to GPDR. (New API, supported on Android, iPhone, iPad and Windows Phone.)

Titanium.Analytics.setOptedOut

method

Sets the value of the Titanium.Analytics.optedOut property. (New API, supported on Android, iPhone, iPad and Windows Phone.)

### 7.1.1

The following APIs are new or have expanded platform support in Release 7.1.1 as of May 2nd, 2018.

API

Type

Notes

Titanium.Android.ActionBar.customView

property

Sets a view to be used for a custom navigation mode. (New API, supported on Android.)

Titanium.Android.ActionBar.getCustomView

method

Gets the value of the Titanium.Android.ActionBar.customView property. (New API, supported on Android.)

Titanium.Android.ActionBar.setCustomView

method

Sets the value of the Titanium.Android.ActionBar.customView property. (New API, supported on Android.)

Titanium.Android.NotificationManager.areNotificationsEnabled

method

Returns whether showing notifications is enabled for the application. (New API, supported on Android.)

Titanium.Calendar.Event.createRecurrenceRule

method

Creates an recurrence pattern for a recurring event.All of the properties for the recurrence rule must be set during creation. The recurrence rule properties cannot be modified. (Added support for Android.)

Titanium.Calendar.Event.getRecurrenceRules

method

Gets the value of the Titanium.Calendar.Event.recurrenceRules property. (Added support for Android.)

Titanium.Calendar.Event.recurrenceRules

property

The recurrence rules for the calendar item. (Added support for Android.)

Titanium.Calendar.Event.save

method

Saves changes to an event permanently. (Added support for Android.)

Titanium.Calendar.Event.setRecurrenceRules

method

Sets the value of the Titanium.Calendar.Event.recurrenceRules property. (Added support for Android.)

Titanium.Calendar.RecurrenceRule

object

An object that is used to describe the recurrence pattern for a recurring event. (Added support for Android.)

Titanium.Media.VideoPlayer.getShowsControls

method

Gets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for Android.)

Titanium.Media.VideoPlayer.setShowsControls

method

Sets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for Android.)

Titanium.Media.VideoPlayer.showsControls

property

Whether or not the receiver shows playback controls. Default is true. (Added support for Android.)

Titanium.UI.Android.DrawerLayout.getToolbar

method

Gets the value of the Titanium.UI.Android.DrawerLayout.toolbar property. (New API, supported on Android.)

Titanium.UI.Android.DrawerLayout.setToolbar

method

Sets the value of the Titanium.UI.Android.DrawerLayout.toolbar property. (New API, supported on Android.)

Titanium.UI.Android.DrawerLayout.toolbar

property

A Toolbar instance to use as a toolbar. (New API, supported on Android.)

Titanium.UI.Android.SearchView.getHintTextColor

method

Gets the value of the Titanium.UI.Android.SearchView.hintTextColor property. (New API, supported on Android.)

Titanium.UI.Android.SearchView.hintTextColor

property

Color of hint text that displays when field is empty. (New API, supported on Android.)

Titanium.UI.Android.SearchView.setHintTextColor

method

Sets the value of the Titanium.UI.Android.SearchView.hintTextColor property. (New API, supported on Android.)

Titanium.UI.SearchBar.color

property

Color of the text in this text field, as a color name or hex triplet. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.getColor

method

Gets the value of the Titanium.UI.SearchBar.color property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.getHintTextColor

method

Gets the value of the Titanium.UI.SearchBar.hintTextColor property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.hintTextColor

property

Hint text color to display when the field is empty. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.setColor

method

Sets the value of the Titanium.UI.SearchBar.color property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.setHintTextColor

method

Sets the value of the Titanium.UI.SearchBar.hintTextColor property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TabGroup.close

event

Fired when the tab group is closed. (Added support for Android.)

### 7.1.0

The following APIs are new or have expanded platform support in Release 7.1.0 as of March 14th, 2018.

API

Type

Notes

Titanium.Android.ActionBar.customView

property

Sets a view to be used for a custom navigation mode. (New API, supported on Android.)

Titanium.Android.ActionBar.getCustomView

method

Gets the value of the Titanium.Android.ActionBar.customView property. (New API, supported on Android.)

Titanium.Android.ActionBar.setCustomView

method

Sets the value of the Titanium.Android.ActionBar.customView property. (New API, supported on Android.)

Titanium.Android.NotificationManager.areNotificationsEnabled

method

Returns whether showing notifications is enabled for the application. (New API, supported on Android.)

Titanium.Calendar.Event.createRecurrenceRule

method

Creates an recurrence pattern for a recurring event.All of the properties for the recurrence rule must be set during creation. The recurrence rule properties cannot be modified. (Added support for Android.)

Titanium.Calendar.Event.getRecurrenceRules

method

Gets the value of the Titanium.Calendar.Event.recurrenceRules property. (Added support for Android.)

Titanium.Calendar.Event.recurrenceRules

property

The recurrence rules for the calendar item. (Added support for Android.)

Titanium.Calendar.Event.save

method

Saves changes to an event permanently. (Added support for Android.)

Titanium.Calendar.Event.setRecurrenceRules

method

Sets the value of the Titanium.Calendar.Event.recurrenceRules property. (Added support for Android.)

Titanium.Calendar.RecurrenceRule

object

An object that is used to describe the recurrence pattern for a recurring event. (Added support for Android.)

Titanium.Media.VideoPlayer.getShowsControls

method

Gets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for Android.)

Titanium.Media.VideoPlayer.setShowsControls

method

Sets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for Android.)

Titanium.Media.VideoPlayer.showsControls

property

Whether or not the receiver shows playback controls. Default is true. (Added support for Android.)

Titanium.UI.Android.DrawerLayout.getToolbar

method

Gets the value of the Titanium.UI.Android.DrawerLayout.toolbar property. (New API, supported on Android.)

Titanium.UI.Android.DrawerLayout.setToolbar

method

Sets the value of the Titanium.UI.Android.DrawerLayout.toolbar property. (New API, supported on Android.)

Titanium.UI.Android.DrawerLayout.toolbar

property

A Toolbar instance to use as a toolbar. (New API, supported on Android.)

Titanium.UI.Android.SearchView.getHintTextColor

method

Gets the value of the Titanium.UI.Android.SearchView.hintTextColor property. (New API, supported on Android.)

Titanium.UI.Android.SearchView.hintTextColor

property

Color of hint text that displays when field is empty. (New API, supported on Android.)

Titanium.UI.Android.SearchView.setHintTextColor

method

Sets the value of the Titanium.UI.Android.SearchView.hintTextColor property. (New API, supported on Android.)

Titanium.UI.SearchBar.color

property

Color of the text in this text field, as a color name or hex triplet. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.getColor

method

Gets the value of the Titanium.UI.SearchBar.color property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.getHintTextColor

method

Gets the value of the Titanium.UI.SearchBar.hintTextColor property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.hintTextColor

property

Hint text color to display when the field is empty. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.setColor

method

Sets the value of the Titanium.UI.SearchBar.color property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.SearchBar.setHintTextColor

method

Sets the value of the Titanium.UI.SearchBar.hintTextColor property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TabGroup.close

event

Fired when the tab group is closed. (Added support for Android.)

### 7.0.1

The following APIs are new or have expanded platform support in Release 7.0.1 as of December 21st, 2017.

API

Type

Notes

Titanium.Android.IMPORTANCE\_DEFAULT

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_HIGH

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_LOW

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_MAX

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_MIN

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_NONE

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_UNSPECIFIED

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.Notification.color

property

Accent color used behind icon. (New API, supported on Android.)

Titanium.Android.Notification.getColor

method

Gets the value of the Titanium.Android.Notification.color property. (New API, supported on Android.)

Titanium.Android.Notification.setColor

method

Sets the value of the Titanium.Android.Notification.color property. (New API, supported on Android.)

Titanium.Android.NotificationChannel

object

Module for notification channels. (New API, supported on Android.)

Titanium.Android.QuickSettingsService

object

Android service for creating custom quick settings tiles and handling user's interaction with them. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_ACTIVE

property

QuickSettings tile is active. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_INACTIVE

property

QuickSettings tile is inactive. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_UNAVAILABLE

property

QuickSettings tile is unavailble. (New API, supported on Android.)

Titanium.Media.VIDEO\_SCALING\_RESIZE

property

Specifies that the video should be stretched to fill the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VIDEO\_SCALING\_RESIZE\_ASPECT

property

Specifies that the player should preserve the aspect ratio of video and fit the video within the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VIDEO\_SCALING\_RESIZE\_ASPECT\_FILL

property

Specifies that the player should preserve the aspect ratio of video and fill the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VideoPlayer.getShowsControls

method

Gets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for iPhone and iPad.)

Titanium.Media.VideoPlayer.setShowsControls

method

Sets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for iPhone and iPad.)

Titanium.Media.VideoPlayer.showsControls

property

Whether or not the receiver shows playback controls. Default is true. (Added support for iPhone and iPad.)

Titanium.Platform.getIdentifierForAdvertising

method

Gets the value of the Titanium.Platform.identifierForAdvertising property. (New API, supported on iPhone and iPad.)

Titanium.Platform.getIdentifierForVendor

method

Gets the value of the Titanium.Platform.identifierForVendor property. (New API, supported on iPhone and iPad.)

Titanium.Platform.getIsAdvertisingTrackingEnabled

method

Gets the value of the Titanium.Platform.isAdvertisingTrackingEnabled property. (New API, supported on iPhone and iPad.)

Titanium.Platform.identifierForAdvertising

property

An alphanumeric string unique to each device, used only for serving advertisements. (New API, supported on iPhone and iPad.)

Titanium.Platform.identifierForVendor

property

An alphanumeric string that uniquely identifies a device to the app's vendor. (New API, supported on iPhone and iPad.)

Titanium.Platform.isAdvertisingTrackingEnabled

property

A Boolean value that indicates whether the user has limited ad tracking. (New API, supported on iPhone and iPad.)

Titanium.Platform.setIdentifierForAdvertising

method

Sets the value of the Titanium.Platform.identifierForAdvertising property. (New API, supported on iPhone and iPad.)

Titanium.UI.ATTRIBUTE\_BASELINE\_OFFSET

property

Use with Attribute.type to apply a different baseline to the text. (Added support for Android.)

Titanium.UI.ListView.allowsMultipleSelectionDuringEditing

property

Determines whether multiple items of this list view can be selected at the same time while editing the table. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.getAllowsMultipleSelectionDuringEditing

method

Gets the value of the Titanium.UI.ListView.allowsMultipleSelectionDuringEditing property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.getSelectedItems

method

Gets the value of the Titanium.UI.ListView.selectedItems property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.selectedItems

property

Returns the selected list view items. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.setAllowsMultipleSelectionDuringEditing

method

Sets the value of the Titanium.UI.ListView.allowsMultipleSelectionDuringEditing property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.setSelectedItems

method

Sets the value of the Titanium.UI.ListView.selectedItems property. (New API, supported on iPhone and iPad.)

Titanium.UI.ScrollView.scrollToTop

method

Moves the top of the scrollable region into the viewable area. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextArea.getHintType

method

Gets the value of the Titanium.UI.TextArea.hintType property. (New API, supported on Android.)

Titanium.UI.TextArea.hintType

property

Hint type to display on the text field. (New API, supported on Android.)

Titanium.UI.TextArea.setHintType

method

Sets the value of the Titanium.UI.TextArea.hintType property. (New API, supported on Android.)

Titanium.UI.TextField.getHintType

method

Gets the value of the Titanium.UI.TextField.hintType property. (New API, supported on Android.)

Titanium.UI.TextField.hintType

property

Hint type to display on the text field. (New API, supported on Android.)

Titanium.UI.TextField.setHintType

method

Sets the value of the Titanium.UI.TextField.hintType property. (New API, supported on Android.)

Titanium.UI.Window.getSustainedPerformanceMode

method

Gets the value of the Titanium.UI.Window.sustainedPerformanceMode property. (New API, supported on Android.)

Titanium.UI.Window.setSustainedPerformanceMode

method

Sets the value of the Titanium.UI.Window.sustainedPerformanceMode property. (New API, supported on Android.)

Titanium.UI.Window.sustainedPerformanceMode

property

Maintain a sustainable level of performance. (New API, supported on Android.)

### 7.0.0

The following APIs are new or have expanded platform support in Release 7.0.0 as of December 8th, 2017.

API

Type

Notes

Titanium.Android.IMPORTANCE\_DEFAULT

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_HIGH

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_LOW

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_MAX

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_MIN

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_NONE

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.IMPORTANCE\_UNSPECIFIED

property

Used with NotificationChannel to specify an importance level. (New API, supported on Android.)

Titanium.Android.Notification.color

property

Accent color used behind icon. (New API, supported on Android.)

Titanium.Android.Notification.getColor

method

Gets the value of the Titanium.Android.Notification.color property. (New API, supported on Android.)

Titanium.Android.Notification.setColor

method

Sets the value of the Titanium.Android.Notification.color property. (New API, supported on Android.)

Titanium.Android.NotificationChannel

object

Module for notification channels. (New API, supported on Android.)

Titanium.Android.QuickSettingsService

object

Android service for creating custom quick settings tiles and handling user's interaction with them. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_ACTIVE

property

QuickSettings tile is active. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_INACTIVE

property

QuickSettings tile is inactive. (New API, supported on Android.)

Titanium.Android.TILE\_STATE\_UNAVAILABLE

property

QuickSettings tile is unavailble. (New API, supported on Android.)

Titanium.Media.VIDEO\_SCALING\_RESIZE

property

Specifies that the video should be stretched to fill the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VIDEO\_SCALING\_RESIZE\_ASPECT

property

Specifies that the player should preserve the aspect ratio of video and fit the video within the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VIDEO\_SCALING\_RESIZE\_ASPECT\_FILL

property

Specifies that the player should preserve the aspect ratio of video and fill the bounds of layer. (New API, supported on iPhone and iPad.)

Titanium.Media.VideoPlayer.getShowsControls

method

Gets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for iPhone and iPad.)

Titanium.Media.VideoPlayer.setShowsControls

method

Sets the value of the Titanium.Media.VideoPlayer.showsControls property. (Added support for iPhone and iPad.)

Titanium.Media.VideoPlayer.showsControls

property

Whether or not the receiver shows playback controls. Default is true. (Added support for iPhone and iPad.)

Titanium.Platform.getIdentifierForAdvertising

method

Gets the value of the Titanium.Platform.identifierForAdvertising property. (New API, supported on iPhone and iPad.)

Titanium.Platform.getIdentifierForVendor

method

Gets the value of the Titanium.Platform.identifierForVendor property. (New API, supported on iPhone and iPad.)

Titanium.Platform.getIsAdvertisingTrackingEnabled

method

Gets the value of the Titanium.Platform.isAdvertisingTrackingEnabled property. (New API, supported on iPhone and iPad.)

Titanium.Platform.identifierForAdvertising

property

An alphanumeric string unique to each device, used only for serving advertisements. (New API, supported on iPhone and iPad.)

Titanium.Platform.identifierForVendor

property

An alphanumeric string that uniquely identifies a device to the app's vendor. (New API, supported on iPhone and iPad.)

Titanium.Platform.isAdvertisingTrackingEnabled

property

A Boolean value that indicates whether the user has limited ad tracking. (New API, supported on iPhone and iPad.)

Titanium.Platform.setIdentifierForAdvertising

method

Sets the value of the Titanium.Platform.identifierForAdvertising property. (New API, supported on iPhone and iPad.)

Titanium.UI.ATTRIBUTE\_BASELINE\_OFFSET

property

Use with Attribute.type to apply a different baseline to the text. (Added support for Android.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS

property

Specifies the expectation of an address. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS\_CITY

property

Specifies the expectation of a city name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS\_CITY\_STATE

property

Specifies the expectation of a city name combined with a state name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS\_LINE1

property

Specifies the expectation of the first line of a street address. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS\_LINE2

property

Specifies the expectation of the second line of a street address. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ADDRESS\_STATE

property

Specifies the expectation of a state name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_EXPIRATION\_DATE

property

Specifies the expectation of a card expiration date. (New API, supported on Android.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_EXPIRATION\_DAY

property

Specifies the expectation of a card expiration day. (New API, supported on Android.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_EXPIRATION\_MONTH

property

Specifies the expectation of a card expiration month. (New API, supported on Android.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_EXPIRATION\_YEAR

property

Specifies the expectation of a card expiration year. (New API, supported on Android.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_NUMBER

property

Specifies the expectation of a card number. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_CARD\_SECURITY\_CODE

property

Specifies the expectation of a card security code. (New API, supported on Android.)

Titanium.UI.AUTOFILL\_TYPE\_COUNTRY\_NAME

property

Specifies the expectation of a country name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_EMAIL

property

Specifies the expectation of an email address. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_FAMILY\_NAME

property

Specifies the expectation of a family name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_GIVEN\_NAME

property

Specifies the expectation of a given name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_JOB\_TITLE

property

Specifies the expectation of a job title. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_LOCATION

property

Specifies the expectation of a location, such as a point of interest, an address, or another way to identify a location. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_MIDDLE\_NAME

property

Specifies the expectation of a middle name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_NAME

property

Specifies the expectation of a name. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_NAME\_PREFIX

property

Specifies the expectation of a prefix or title, such as 'Dr.' (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_NAME\_SUFFIX

property

Specifies the expectation of a suffix, such as 'Jr.' (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_NICKNAME

property

Specifies the expectation of a nickname. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_ORGANIZATION\_NAME

property

Specifies the expectation of an organization name. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_PASSWORD

property

Specifies the expectation of a password. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_PHONE

property

Specifies the expectation of a telephone number. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_POSTAL\_CODE

property

Specifies the expectation of a postal code. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_SUBLOCALITY

property

Specifies the expectation of a sublocality. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_URL

property

Specifies the expectation of a URL. (New API, supported on iPhone and iPad.)

Titanium.UI.AUTOFILL\_TYPE\_USERNAME

property

Specifies the expectation of an account or login name. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.ListView.allowsMultipleSelectionDuringEditing

property

Determines whether multiple items of this list view can be selected at the same time while editing the table. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.getAllowsMultipleSelectionDuringEditing

method

Gets the value of the Titanium.UI.ListView.allowsMultipleSelectionDuringEditing property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.getSelectedItems

method

Gets the value of the Titanium.UI.ListView.selectedItems property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.selectedItems

property

Returns the selected list view items. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.setAllowsMultipleSelectionDuringEditing

method

Sets the value of the Titanium.UI.ListView.allowsMultipleSelectionDuringEditing property. (New API, supported on iPhone and iPad.)

Titanium.UI.ListView.setSelectedItems

method

Sets the value of the Titanium.UI.ListView.selectedItems property. (New API, supported on iPhone and iPad.)

Titanium.UI.ScrollView.getRefreshControl

method

Gets the value of the Titanium.UI.ScrollView.refreshControl property. (Added support for Android.)

Titanium.UI.ScrollView.refreshControl

property

View positioned above the first row that is only revealed when the user drags the scroll view contents down. (Added support for Android.)

Titanium.UI.ScrollView.scrollToTop

method

Moves the top of the scrollable region into the viewable area. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.ScrollView.setRefreshControl

method

Sets the value of the Titanium.UI.ScrollView.refreshControl property. (Added support for Android.)

Titanium.UI.TextArea.autofillType

property

Sets the autofill type for the text area. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextArea.getAutofillType

method

Gets the value of the Titanium.UI.TextArea.autofillType property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextArea.getHintType

method

Gets the value of the Titanium.UI.TextArea.hintType property. (New API, supported on Android.)

Titanium.UI.TextArea.hintType

property

Hint type to display on the text field. (New API, supported on Android.)

Titanium.UI.TextArea.setAutofillType

method

Sets the value of the Titanium.UI.TextArea.autofillType property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextArea.setHintType

method

Sets the value of the Titanium.UI.TextArea.hintType property. (New API, supported on Android.)

Titanium.UI.TextField.autofillType

property

Sets the autofill type for the text field. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextField.getAutofillType

method

Gets the value of the Titanium.UI.TextField.autofillType property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextField.getHintType

method

Gets the value of the Titanium.UI.TextField.hintType property. (New API, supported on Android.)

Titanium.UI.TextField.hintType

property

Hint type to display on the text field. (New API, supported on Android.)

Titanium.UI.TextField.setAutofillType

method

Sets the value of the Titanium.UI.TextField.autofillType property. (New API, supported on Android, iPhone and iPad.)

Titanium.UI.TextField.setHintType

method

Sets the value of the Titanium.UI.TextField.hintType property. (New API, supported on Android.)

Titanium.UI.Window.extendSafeArea

property

Specifies whether the content (subviews) of the window will render inside the safe-area or not.Only used in iOS 11.0 and later. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getExtendSafeArea

method

Gets the value of the Titanium.UI.Window.extendSafeArea property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getLargeTitleDisplayMode

method

Gets the value of the Titanium.UI.Window.largeTitleDisplayMode property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getLargeTitleEnabled

method

Gets the value of the Titanium.UI.Window.largeTitleEnabled property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.getSustainedPerformanceMode

method

Gets the value of the Titanium.UI.Window.sustainedPerformanceMode property. (New API, supported on Android.)

Titanium.UI.Window.largeTitleDisplayMode

property

The mode to use when displaying the title of the navigation bar. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.largeTitleEnabled

property

A Boolean value indicating whether the title should be displayed in a large format. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setExtendSafeArea

method

Sets the value of the Titanium.UI.Window.extendSafeArea property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setLargeTitleDisplayMode

method

Sets the value of the Titanium.UI.Window.largeTitleDisplayMode property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setLargeTitleEnabled

method

Sets the value of the Titanium.UI.Window.largeTitleEnabled property. (New API, supported on iPhone and iPad.)

Titanium.UI.Window.setSustainedPerformanceMode

method

Sets the value of the Titanium.UI.Window.sustainedPerformanceMode property. (New API, supported on Android.)

Titanium.UI.Window.sustainedPerformanceMode

property

Maintain a sustainable level of performance. (New API, supported on Android.)

Titanium.UI.iOS.LARGE\_TITLE\_DISPLAY\_MODE\_ALWAYS

property

Always use a larger title when this item is top most. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.LARGE\_TITLE\_DISPLAY\_MODE\_AUTOMATIC

property

Automatically use the large out-of-line title based on the state of the previous item in the navigation bar. (New API, supported on iPhone and iPad.)

Titanium.UI.iOS.LARGE\_TITLE\_DISPLAY\_MODE\_NEVER

property

Never use a larger title when this item is top most. (New API, supported on iPhone and iPad.)
