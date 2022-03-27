# Deprecation Notice
UpdateKit as a standalone shortcut has been deprecated and will be removed from availability with the launch of iOS 17 (estimated late 2023). It has been replaced by a far more powerful cloud version called the UpdateKit API, which is available for use in all shortcuts, including third-party standalone updaters. You can learn more about the UpdateKit API at [mikebeas.com/updatekit-api](https://www.mikebeas.com/updatekit-api).

# UpdateKit Translations
This repo contains the files for the languages built into UpdateKit 4.0. Starting with version 4.0, you can create and distribute your own language files to translate UpdateKit into any language you want. You can share these files online, and other users can download and install them directly from UpdateKit.

### Creating A Language File
UpdateKit language files are JSON files that contain the translated strings for each line of text that appears in the Shortcut. There are currently eleven strings, plus two pieces of metadata (plus an optional piece of metadata).

The two pieces of metadata that **must** be included with these strings are the English-translated name of the language and the localized version of the same name. These should use the keys `English Name` and `Localized Name`. You can see examples of this in the files on this repo.

A third piece of metadata may optionally be included: `Credit`. This will contain the name of the language file creator. This is not currently used in UpdateKit, but could be used in future updates to display a language file's creator. However, this will **never** be mandatory in any future version of UpdateKit. Language files for the bulit-in languages do not contain this credit because they have translator credits inside the UpdateKit Shortcut, where they are more visible.

### Strings to Localize
The table below contains the JSON key, English string, and case of the original string, such as "Sentence case" or "Title Case." Matching the case is advisable if your language uses capitalization similarly to English. Note that the keys are case-sensitive and must be entered exact as shown below.

You will see {{variableNames}} in the strings below. Do not translate those. Insert them unchanged wherever the variable should go in the translated string. They are not case-sensitive, but they should always be enclosed in double curly brackets so that UpdateKit can find them and replace them with the appropriate variable.

![](https://raw.githubusercontent.com/MikeBeas/updatekit-translation/master/table.png)

### Testing Your Language File
To test your language file, first delete the Configuration.json file from iCloud Drive » Shortcuts » UpdateKit to reset your language. In UpdateKit 5.0 or later, you can also run UpdateKit with no input to bring up the menu, which will allow you to reset your language. Next, change the `Version` in UpdateKit's Dictionary to 2.3. This will allow you to run UpdateKit and see a new update with your translations once the file is installed. This specific version number will also allow you to test the `Broadcast Notice` string that appears in the emergency message popup. Note that the `Broadcast Notice` feature is no longer included in the latest versions of UpdateKit. You only need to add this if you want your language file to be backwards compatible. The latest version of UpdateKit does not exclude any devices so this is not necessary to support any devices.

**Don't forget to change your version number back when you're done testing so that you don't keep seeing false update warnings!**

Once that's done, you need to install your file. Add it to your iCloud Drive or another Files app-compatible file storage service, then run UpdateKit. It will prompt you to select a language. Select the ••• option and then choose "File" from the menu and select your file from the location where you saved it.

You should see the `Localized Name` on the confirmation dialog (with the thumbs-up and thumbs-down emoji options). If you do not see your language's name here, cancel or press the thumbs-down emoji to exit and check your file. You can use jsonlint.com to make sure that your JSON is formatted correctly.

If you see your language name in the confirmation dialog, select the thumbs-up emoji to confirm your selection and continue through the process. You should see text in all of the usual places in UpdateKit. If you need to make changes to your file, just delete the Language.json or Configuration.json file from the UpdateKit folder in iCloud Drive as before to reset your language. If either of these files are missing, you will be prompted to re-select your language (note that English works without a Language.json file because its strings are built into the Shortcut).

### Distributing Your Language File
**Please do not make pull requests to this repo. New language submissions are currently closed. Pull requests will be ignored or declined. If you find an error in one of the translations hosted on this repo, please contact [@UpdateKit](https://twitter.com/updatekit) with details.**

Once your language file is ready to ship, you can post it anywhere on the web. Other users will be able to download it and install it using the Install from File method, or by pasting the URL to the raw JSON into the Download from URL option. Be aware that when downloading a language file from a URL, you must link directly to the file, not to a page hosting the file. For example, if the file is stored on GitHub, you will need to use the click the "Raw" button on that file and use the link to the raw file.

A .txt file will install correctly (without the .json extension) if the file contains correctly formatted JSON. This may also be true of files with no extension, or with other file extensions that the Shortcuts app can parse for data. However, the recommended method of distribution is as a .json file or a .txt file containing properly formatted JSON.
