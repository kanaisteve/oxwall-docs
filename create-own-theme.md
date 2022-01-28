# How to create your own theme

## What is Oxwall?

Oxwall is a great community-software written in PHP. You can easily install it on your own server to build your own community site.

It is open source and you have full control over the data.

Although Oxwall comes with some great themes that can even be easily customized in the backend a bit, one might want to build one’s own theme for Oxwall.

## How to create own theme

1. Probably first build an HTML template of your design (one HTML page with CSS that looks like you plan how your Oxwall should look like). If you do that, make sure to use a list-based main menu and a div/link-based bottom-menu (see below) so you won’t get into trouble later.
2. Always a good idea to have a backup – although adding a new theme shouldn’t break anything. I’d recommend you to create a copy of your Oxwall installation where you create and test your new theme and when it’s finished, move it to your live installation of Oxwall.
3. Create a copy of an existing theme. You will find the themes in ow_themes. Choose one you’d like to use as a base for your own theme.
Copy it. E.g on a linux shell:

`cp -rp own_themes/spring ow_themes/mytheme`

