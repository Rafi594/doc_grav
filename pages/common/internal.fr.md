---
cache_enable: false
visible: false
---

[g-navbar id="navbar1" name=navbar1 fixed=top centering=none image="yunohost.jpg" render=false]
    [g-navbar-menu name=menu0 alignment="center" submenu="autre" attributes="class:highdensity-menu"][/g-navbar-menu]    
    [g-navbar-menu name=menu1 icon_type="fontawesome" alignment="right" ]
    [g-link url="https://rafi59.codelib.re/grav/login" icon="login"][/g-link]
        [g-link url="https://framasphere.org/u/yunohost" icon_type="fontawesome" icon="asterisk"][/g-link]
        [g-link url="https://mastodon.social/@yunohost" icon="retweet"][/g-link]
        [g-link url="https://github.com/YunoHost" icon="github"][/g-link]
    [/g-navbar-menu]
[/g-navbar]

[g-footer-one name="footer" render=false]
[g-section name="credits"]

Ce site est motorisé par [Grav CMS](http://getgrav.org/) avec le theme [Gravstrap](http://diblas.net/themes/gravstrap-theme-to-start-grav-cms-site-with-bootstrap-support/)

[/g-section]
[/g-footer-one]
