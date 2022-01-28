# OW_Theme_Dev 101

### Explaining Files and Folders
- foldername
- folder_name
- folder2name

You can not have whitespace in your folder name.

For a quick boost, you cam duplicate Oxwall simplicity theme, rename the folder and customize them accordingly... Or you can start from the very scratch. 

### theme.xml
Create a theme.xml file in your root folder.

This is the xml file that contains your theme information. It contains the theme two vital components: The theme key and developer key. The theme key is a unique name that is reserved for each Oxwall commercial theme to avoid conflits (like an id). To make sure that your key is unique run a check here <https://developers.oxwall.com/store/dev-tools>. Your developer key is also on the right panel of that page. Developer key and theme key is needed for plugin license check and updates.

Below is the content of `theme.xml`

```
<?xml version="1.0" encoding="utf-8"?>
<theme>
    <name>Theme Name</name>
    <key>foldername</key>
    <version>1.0</version>
    <compatibility>1.7 and higher</compatibility>
    <description>Your amazing theme description</description>
    <author>Oxwall Foundation</author>
    <authorEmail>email@example.com</authorEmail>
    <authorUrl>http://www.yourthemesite.com</authorUrl>;
    <developerKey>yourDeveloperKey</developerKey>
    <build>1</build>
    <copyright>(C) Fancy copyrights. All rights reserved.</copyright>
    <license>The BSD License</license>
    <licenseUrl>http://www.opensource.org/...hp</licenseUrl>;
</theme>
```

You don't always have to use The BSD License. OSCL is the legal license for commercial Oxwall items <https://developers.oxwall.com/store/oscl>.


### base.css
This is the CSS base file for Oxwall themes. We will come to this later.

### README.md
Add some special information users need to use your theme here.

### images folder
This folder contains all the statics files you intend using on your theme. You images, fonts, js, additional css, etc can go here.

### master_pages folder
This folder contains all the html templates used to structure Oxwall system. By default, each of the master tempplates are inherited from the Oxwall simplicity theme or the current default theme. Adding any of blank, general, dndindex or html_documents templates to your theme master pages will overide simplicy master page for that template.
 
This is also where we will be throwing all our bootstrap codes.

- **blank.html** templates structures the blank pages such as the sign-in page, forgot password page, email verification page, etc.
- **dndindex.html** templates structures the index page when it's on customization mode.
- **html_document** templates structures custom html pages such as privacy policy, terms, and your custom pages.
- **general.html** structures the rest of the site (apart from the admin area).

It is also worthy of note that most pages has there own document unique key which is the unique class for that document. For instance, the unique class for the join page is `.base_user_join`, that of the sign-in page is `.base_sign_in`, the user profile page is  `.base_profile_page`, etc.

You can add your custom classes with just a simple plugin tweaking.

### Mobile
This is for mobile version of your theme. Will be discussed much later.

### theme.jpg
A small thumbnail image of your theme. Usually 154px X 93px
 
### theme_preview.jpg
A larger preview of your theme. Usually 700px X 525px.



Reference: <https://developers.oxwall.com/forum/topic/49170?&page=2>