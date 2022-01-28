# OW_Theme_Dev 102

This part of the tutorial covers Oxwall basic HTML structure, things you need to start your theme development and how to integrate Bootstrap classes.

### Requirements
- Notepad++: Code editing software <https://notepad-plus-plus.org/download/v6.9.2.html>
- Oxwall Cache Cleaner: You will need to clear your theme & template cache to see live changes on your website <https://developers.oxwall.com/store/item/579>
- Oxwall Bootstrap Plugin: Integrate bootstrap framework to Oxwall <https://developers.oxwall.com/store/item/1289>
In this tutorial, we will deal mainly with the general.html template. You can modify other templates if you fully grab the concept behind Oxwall theme master pages.

### General Page Markup 
The general page templates controls up to 90% of the website. The HTML structure is as follows:

```
<div class="ow_page_wrap">
    <div class="ow_menu_fullpage">
        <div class="ow_menu_fullpage_wrap">
            <!-- Main menu goes here -->
            {$main_menu}
        </div>
    </div>

    <div class="ow_site_panel clearfix">
        <a class="ow_logo ow_left" href="{$siteUrl}"></a><!-- This is the logo area. -->
        <div class="ow_nav_btn"></div>
        <div class="ow_console_right">
            <!-- Console items goes here -->
            {component class='BASE_CMP_Console'}
        </div>

        <div class="ow_menu_wrap">
            <!-- Responsive main menu goes here -->
            {component class='BASE_CMP_MainMenu' responsive=true}
        </div>
    </div>

    <div class="ow_header">
        <div class="ow_header_pic"></div>
    </div>

    <!-- Theme header image -->
    {*if isset($imageControlValues.headerImage.src)}
    <div class="ow_header">
        <img class="ow_header_img" src="{$imageControlValues.headerImage.src}" />
        <div class="ow_header_pic">
            <img class="ow_header_img" src="{$themeImagesUrl}header.jpg" />
        </div>
    </div>
    {/if*}

    <div class="ow_page_padding">
        <div class="ow_page_container">
            <div class="ow_canvas">
                <div class="ow_page ow_bg_color clearfix">

                    {if !empty($heading)}
                    <!-- Page heading -->
                    <h1 class="ow_stdmargin {$heading_icon_class}">
                        {$heading}
                    </h1>
                    {/if}

                    <!-- Page content -->
                    <div class="ow_content">
                        {add_content key='base.add_page_top_content'}
                        {$content}
                        {add_content key='base.add_page_bottom_content'}
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- Page footer -->
<div class="ow_footer">
    <div class="ow_canvas">
        <div class="ow_page clearfix">
            {$bottom_menu} <!-- Bottom menu links -->
            <div class="ow_copyright">
                {text key='base+copyright'} <!-- Website copyright -->
            </div>
            <div style="float:right;padding-bottom: 30px;">
                {$bottomPoweredByLink} <!-- Oxwall Attribution -->
            </div>
        </div>
    </div>
</div>
```

The above is a simple html found in `ow_themes/themefolder/master_pages/general.html`. I have added comments to explain the key areas. You can always ask question if find anything complex.

Play around with the html a bit to see how easy it is to modify. You can pick any of the classes, find it in base.css and add your own style. Just remember to clear your cache whenever you make changes.

### Integrating Bootstrap

Adding bootstrap to the template is the easiest part. All you have to do is add the bootstrap classes to their respective areas or where you want to use theme.

#### Example 1:
```
<div class="ow_page_wrap">
    <div class="container-fluid">
        <!--ow_page_wrap contents-->
    </div>
</div>

<div class="ow_footer">
    <div class="container-fluid">
        <!--ow_footer contents-->
    </div>
</div>
```

In your base.css you can add:
```
.container-fluid {
    padding:0px;
}
```

To remove padding from container-fluid.


Reference: <https://developers.oxwall.com/forum/topic/49170?&page=2>