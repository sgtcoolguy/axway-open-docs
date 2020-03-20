{"title":"Alloy 1.9.3 - 8 October 2016","weight":"30"}

Alloy 1.9.3 is a patch release that includes new features, improvements, and bug fixes.

As of this release, the previous Alloy patch release is no longer supported. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#nominal-lifetimes) documents for details.

## New features

* [ALOY-1493](https://jira.appcelerator.org/browse/ALOY-1493) - \[Alloy\] Alloy sql adapter db\_file to be function

    * The db\_file not accepts function

    * Example:

        <table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class="js plain ">exports.definition = {</tt><tt class="js spaces "> </tt><tt class="js plain ">config: {</tt><tt class="js spaces "> </tt><tt class="js plain ">columns: {},</tt><tt class="js spaces "> </tt><tt class="js plain ">adapter: {</tt><tt class="js spaces "> </tt><tt class="js plain ">type: </tt><tt class="js string ">"sql"</tt><tt class="js plain ">,</tt><tt class="js spaces "> </tt><tt class="js plain ">collection_name: </tt><tt class="js string ">"mytable"</tt><tt class="js plain ">,</tt><tt class="js spaces "> </tt><tt class="js plain ">db_file: </tt><tt class="js keyword ">function</tt><tt class="js plain ">() {</tt><tt class="js spaces "> </tt><tt class="js keyword ">var</tt> <tt class="js plain ">myFile = Titanium.Filesystem.getFile(Titanium.Filesystem.applicationDataDirectory, </tt><tt class="js string ">'file1.sql'</tt><tt class="js plain ">);</tt><tt class="js spaces "> </tt><tt class="js keyword ">return</tt> <tt class="js plain ">myFile.exists() ? myFile.nativePath : Titanium.Filesystem.applicationDataDirectory + </tt><tt class="js string ">'file2.sql'</tt><tt class="js plain ">;</tt><tt class="js spaces "> </tt><tt class="js plain ">},</tt><tt class="js spaces "> </tt><tt class="js plain ">db_name: </tt><tt class="js string ">"projectsDB"</tt><tt class="js plain ">,</tt><tt class="js spaces "> </tt><tt class="js plain ">idAttribute: </tt><tt class="js string ">"UserID"</tt><tt class="js plain ">,</tt><tt class="js spaces "> </tt><tt class="js plain ">remoteBackup: </tt><tt class="js keyword ">false</tt><tt class="js spaces "> </tt><tt class="js plain ">}</tt><tt class="js spaces "> </tt><tt class="js plain ">}</tt><tt class="js plain ">};</tt></p></td></tr></tbody></table>

## Improvements

* [ALOY-1519](https://jira.appcelerator.org/browse/ALOY-1519) - Alloy: Support iOS 10 <RefreshControl> tag in Ti.UI.ScrollView

    * Added support for iOS 10's <RefreshControl> element in Ti.UI.ScrollView

## Fixed issues

* [ALOY-1520](https://jira.appcelerator.org/browse/ALOY-1520) - Replace Ti.Ui.iPhone with Ti.Ui.iOS in Alloy
