## Changelog
### Jan. 14th, 2020 (v1.3.4):
* Added support for Group Views with subgroup projects
  * Authors and approvals will now properly be fetched for group views. Previously, subgroup projects were not propogating correctly and resulted in undefined project IDs.

### Jan. 21st, 2019 (v1.3.3):
* Fix for very large group views
  * There was an issue with the selector on merge request `li` items in the group view which caused massive mix ups of where to inject approvals and move author views around.

### Jan. 20th, 2019 (v1.3.2):
* Added Group support
  * The plugin now works for all composite group views.
  * Uses a single API call to get project ids (only if it hasn't seen one before!), and then similar functionality as a project view.
* Added option to clear all cache and settings

### Jan. 19th, 2019 (v1.3.1):
* Fixes a caching bug which involved getting the wrong time stamp off the page
* Fixes the generalized permissions issue
  * Allows me to publish faster
  * Potentially reduces the number of whitelisted websites that will work with the extension. Going to keep investigating.

### Jan. 18th, 2019 (v1.3.0):
* Hosted on the chrome web store now!
* Now works with ANY gitlab host!
* Fixed an issue with settings not working
* Reduced potential calls to 0 on subsequent page refresh (got rid of the initial API request that did MR status checks)
* Fixed a bunch of issues with sorting/searching/ordering/page views due to new method of getting time stamps for MRs
* Added new setting
    * Now you can automatically have it mark the checkbox to auto remove a branch once an MR has been merged. This is disabled by default.
* Cleaned up some code -- internal stuff that ended up looking better due to new cache checks. Page loads are faster!

### Jan. 18th, 2019 (v1.2.1):
* Fixed an issue with the first request for the opened MRs not loading

### Jan. 17th, 2019 (v1.2.0):
* Added a caching mechanism
  * Issue: casual usage from teams has been a positive experience. However, rate limiting has been enabled for our team. We're now consistently hitting rate limits due to how many upfront API requests this plugin makes (10 MRs = 10 API requests. This adds up during a quick session.)
  * Benefits: This will reduce the number of subsequent calls from page refreshes or general navigation.
  * How it works: Instead of immediately calling each MR approval list every time we load the page, we will do a check against `/projects/{projectId}/merge_requests` and view the last update time for each MR. If the cache entry is older than the last update time, refresh that cache entry. If the cache matches the last update time, then don't update.
* Refreshed the styling of the options page
  * Updated the default settings to use compact approval settings by default.
  * Added an indicator that displays "Setting Saved!" whenever a user changes their settings.
* Fix alignment of missing approval circles to match other approval margins

### Jan. 1st, 2019 (v1.1.1):
* Fix compact approvals
  * Using a different element to key off of where to place (originally pipeline status -- wasn't always there).

### Dec. 27th, 2018 (v1.1.0):
* Added Icon for the Extension
* Added simple settings page (Note: You need to _*reload*_ the merge request page after changing the settings)
  * Compact View -- Enable this to bring the approvals to the right hand side of the page.
  * Author View -- Helps display the author more prominantly on the left hand side.
* Updated to version 1.1.0 instead of 1.1, changing the versioning scheme.

### Oct. 11th, 2018 (v1.0.0):
* Initial Release
* Only Works under one domain currently
* Loads approvals into view when viewing the list of Merge Requests
