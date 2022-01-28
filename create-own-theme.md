# How to create your own theme

## What is Oxwall?

Oxwall is a great community-software written in PHP. You can easily install it on your own server to build your own community site.

It is open source and you have full control over the data.

## How to create own theme in oxwall

Although Oxwall comes with some great themes that can even be easily customized in the backend a bit, one might want to build one’s own theme for Oxwall.

Here is how you do it:

1. Probably first build an HTML template of your design (one HTML page with CSS that looks like you plan how your Oxwall should look like). If you do that, make sure to use a list-based main menu and a div/link-based bottom-menu (see below) so you won’t get into trouble later.
2. Always a good idea to have a backup – although adding a new theme shouldn’t break anything. I’d recommend you to create a copy of your Oxwall installation where you create and test your new theme and when it’s finished, move it to your live installation of Oxwall.
3. Create a copy of an existing theme. You will find the themes in ow_themes. Choose one you’d like to use as a base for your own theme.
Copy it. E.g on a linux shell:

```
cp -rp own_themes/spring ow_themes/mytheme
```
4. Define the meta-data of your theme like name, author and so on. To do so, open `ow_themes/mytheme/theme.xml` in a text editor and adjust the data. Make sure the `<key>` is equal to the foldername (“mytheme” in the example).
5. If you want to, you can replace the theme_preview.jpg with a small thumbnail representing your theme (optional).
6. Now you can select this theme in the Oxwall backend. Try it. Note: To be able to adjust the theme, enable DEV_MODE. Otherwise you won’t see any changes. So open   `ow_includes/config.php` in a texteditor. Search for:

```
else
{
    /**
    * Make changes in this block if you want to enable DEV mode and DEBUG mode
    */
 
    define('OW_DEBUG_MODE', false);
    define('OW_DEV_MODE', false);
    define('OW_PROFILER_ENABLE', false);
}
```

change `OW_DEV_MODE` to true
```
else
{
    /**
    * Make changes in this block if you want to enable DEV mode and DEBUG mode
    */
 
    define('OW_DEBUG_MODE', false);
    define('OW_DEV_MODE', true); /* HERE! */
    define('OW_PROFILER_ENABLE', false);
}
```
8. Now you can start to adjust your theme. So what does a theme consists of?


### Meta-Data: theme.xml
`theme.xml` contains the meta data and `theme_preview.jpg` is a preview image.

### CSS: base.css
The main css of a stylesheet is called base.css. You can change/adjust the css there (there are also other places like the backend). I would recommend you to keep the css of your base theme and only adjust and add things to it. Otherwise you’ll have a hard time styling lots of things.

### Images: images/*
If you need to include images, this is the best place to put them. If you refer to them from the css, use a path like this:

```
background-image: url(images/myimage.jpg);
```

### HTML: master_pages/*
The HTML that builds your theme is stored in `master_pages.`

Note: Lots of themes do not contain all master_pages. If one is missing, the master_pages of the `graphite` theme are used. Therefore, I’d recommend you to first copy missing master_pages from the `graphite` theme to your theme so you get a full set of master_pages.

The following master_pages can be there:

- admin.html (only for the admin backend - no need to adjust this)
- blank.html (usually no need to change this as well)
- **dndindex.html** (body for pages without sidebar - you'll want to adjust this!)
- **general.html** (body for pages with sidebar - you'll want to adjust this!)
- **html_document.html** (html-head of alll pages, you might want to add css or javascript here)

### Markers

The following are the most important markers that you can put in your html mater_pages:

1. `{*$siteUrl*}`

2. `{*$siteName*}`

3. `{*$siteTagline*}`

4. `{ $Component class='BASE_CMP_Console }` : 
  This is the console containing 'Login', 'Register', and many more (usually at the top right corner).

5. `{$main-menu}` : A list-based menu

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Hint: **Listamatic** has lots of great list-based menu examples.

6. `{$heaing}`

7. `{componet}` : The sidebar.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Note: only in the **general.html**

8. `{add_content key=’base.add_page_top_content’}`

9. `{$content}`

10. `{add_content key=’base.add_page_bottom_content’}` : These 3 build up the main content.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Note: You'll only need `{$content}` in dndindex.html

11. `{$bottom_menu}` : The bottom menu

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Note: Not list-style, but a div with links.

12. `{text key=’base+copyright’}`

13. `{$bottomPoweredByLink}`

14. `{decorator name=’floatbox’}` : This should be at the end of your html file - oxwall puts JavaScript and stuff like that there (for chat etc.).

All the others should be self-explainatory.


### How you can do it:
- Upload your images to `images` folder and your `js` (of any) to the theme-folder
- Add your `css` at the end of `base.css`
- Add your references to additional css/js to `html_document.html` (no need to add a reference to `base.css`)
- Put the content of your body into `general.html` and `dndindex.html`
- Replace your static content in there with markers.

### Don't forget DEV_MODE
When you are done, don't forget to set `DEV_MODE` back to `false`. Otherwise your site will load slowly.



Reference: <https://blog.christosoft.de/2013/02/oxwall-theme-tutorial/>