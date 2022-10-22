# Layout Options

C4-PlantUML comes with some layout options.

<!--TOC-->
<!--/TOC-->

## Layout Guidance and Practices

PlantUML uses [Graphviz](https://www.graphviz.org/) for its graph visualization. Thus the rendering itself is done automatically for you - that it one of the biggest advantages of using PlantUML.

...and also sometimes one of the biggest disadvantages, if the rendering is not what the user intended.

### Overall Guidance

1. Be minimal in the use of all directed relations - introduce the fewest possible directed `Rel_` and `Lay_` statements that achieve the desired layout. One way to do this is to immediately remove any of these you experiment with when they don't actually affect the layout at all. And of course you will remove the ones that affect it the layout in a negative way.
2. With dynamic rendering tools (e.g. VS Code plugin) do NOT trust the first rendering as it is shifty when adding code because you do not know exactly when it grabs the current unsaved code. Wait for a bit or close and reopen preview panel.

### Layout Practices

These are intended to correlate to the layout engine’s algorithm, but have (as of this writing) been determined by trial and error - not a code review.

Please read through all practices before starting.

1. Create all components, containers and boundaries first - in order top to bottom or left to right.
2. Use `Rel` (directionless) to create initial relationships.
3. If layout is not as desired, modify **some** Rel statements to contain direction `Rel_{direction}` to force shape layouts. 
4. If the layout is not as desired, sparingly add `Lay_{direction}` to force any layouts that `Rel_{direction}` does not correct.
5. For both `Lay_{direction}` and `Rel_{direction}` statements used above:
   1. Exhaust attempts to get a working layout with `Rel_{direction}` before adding `Lay_{direction}`
   2. Try to introduce the fewest possible directed statements (of either type) that result in the desired layout.
   3. Immediately back out any directed statements that do not change the layout at all.
   4. Order inner objects first when it creates the desired result (enclosing objects tend to follow suit when child objects are ordered).
   5. When ordering multiple objects, only specify one relationship and, if possible in the same direction. For example if you want entity1 => entity2 => entity3, then `Rel_R(entity1,entity2)` and `Rel_R(entity2, entity3)` is the minimum possible statements and they all specify the same direction.
   6. Try NOT to apply directed statements to both inner elements and enclosing elements to force relationships that aren't working out.
   7. Make all orderings at the same nesting level whenever possible.
   8. Do NOT create duplicated, opposite direction statements in an attempt to force or ensure relationships as it does not affect the results. For instance if you have `Lay_R(entity1,entity2)` which is not working as desired and then also add the opposing one as `Lay_L(entity2,entity1)` - it does not help with forcing layouts to be as you want them. It might help to use `Lay_L` **instead of** `Lay_R`, but not both together.
6. Do not create an "All enclosing" boundary - the code for processing relationships seems to struggle with relationships inside this. Additionally, `SHOW_FLOATING_LEGEND()` will not display inside the All enclosing boundary.
7. Legend statements must come after at least one usage of each of the elements you want the legend to contain.

## LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT() or LAYOUT_LANDSCAPE()

With the two macros `LAYOUT_TOP_DOWN()` and `LAYOUT_LEFT_RIGHT()` it is possible to easily change the flow visualization of the diagram. `LAYOUT_TOP_DOWN()` is the default.

```plantuml
@startuml LAYOUT_TOP_DOWN Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

/' Not needed because this is the default '/
LAYOUT_TOP_DOWN()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_TOP_DOWN Sample](https://www.plantuml.com/plantuml/png/NP1F3vD04CNl-od6Ue0c5LBZoPE8HW_zGuJQU28BJ6NZ_jdi3i76-DqTqjeQkRomxysRt-wxI3BGP3JiYc_7KzCsnwhzS3mVe9R6QnGlbEtrD22CH3w-pVCWv-oxed7gfeYXTvRGKjOxa_zGeHyZZNdvvbMbfQNJVfVZJ_O77FYmBJaibSMGUTueH9x0mH5OH0v0XxtaIg1HHL2H5M70YvmqGPAB__ZIjH0LXkXiAWUZx0PMnQ8gKf3amcejwciaDErxDzb1XclQRpUGtAwLhE6N0FuUIEcCNIkzvvupTb1uhrKlIJcxugFovGQAkieE7niU2GYliotilvQBLsZjvWYC7XZQ0J-5bnmn3Avu5pIp8i80f0ngtXMPxVUTBgMRoJtt69lY2-g_jtfYdI9Fidvkcghcr19wkC-QJqYHVt6HIt3cdv4_ "LAYOUT_TOP_DOWN Sample")

`LAYOUT_LEFT_RIGHT()` rotates the flow visualization to *from Left to Right* and directed relations like `Rel_Left()`, `Rel_Right()`, `Rel_Up()` and `Rel_Down()` are rotated too.

```plantuml
@startuml LAYOUT_LEFT_RIGHT Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

LAYOUT_LEFT_RIGHT()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_LEFT_RIGHT Sample](https://www.plantuml.com/plantuml/png/PL1DhzCm4BpxLopbq5GgYOeuSMg8IelKGjIa84wHcop4mX-MlL6e4F_zRTI-zadFbvLtPdTcTXr91XgCXdt-yzkfRlQRptLp_BBTrL19upMADygsUkWGUY8VFsPPa6FwMr4_d8U8eNMMq5BQEfFzKQ7j8_LPyU5TgQMbqs6VuL_6E-ousHHCbifYI3rh2l5AD5a8KMA8pYQoCyekOPPFLKKAaboOBKHrYOIc-UG6sybmIThL4kPNh_C5_1F0xwwJZ7XkfFUyvmUU8VTUgrQISdR6hUBj4lAgJBzkQXu92E_J5Ho-5nEMQ-t625F42EI0ytd953DeKgm5zQY8C00fWvgr8dlxVtENq1NaFJSQW-A8-ZdLmzOfyYJNNLsN5RCcqXrzhDaYHVxYL7u5PrwEhFc-VCud "LAYOUT_LEFT_RIGHT Sample")

`LAYOUT_LANDSCAPE()` rotates the default flow visualization to *from Left to Right* like `LAYOUT_LEFT_RIGHT()` additional **directed relations** like Rel_Left(), Rel_Right(), Rel_Up() and Rel_Down() **are not rotated** anymore.

```plantuml
@startuml LAYOUT_LANDSCAPE Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

LAYOUT_LANDSCAPE()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")

System(S,"S")
System(SU,"S Up")
System(SD,"S Down")
System(SL,"S Left")
System(SR,"S Right")

Rel_Up(S, SU, "Up")
Rel_Down(S, SD, "Down")
Rel_Left(S, SL, "Left")
Rel_Right(S, SR, "Right")

SHOW_LEGEND()

@enduml
```

![LAYOUT_LANDSCAPE Sample](https://www.plantuml.com/plantuml/png/NO_DRjim48JlUWhMFKG6N0afUkefgcGa1yKHBAb1Jm8jRIAY_2785TIWwBjtQIks4Lw8-MOvixppo1rEIh8o-_NKDbsPxOewpwejgxco4g9FGlTo6e2DYDP_JrF7v-HLu3WT9W-kDnf1Oz8RbVuMhXyzZcd-xKibkSRsiKpX3_a330Ixd8QvqE0IIvLHzB4pNaTH1SuR7VD12RrXgopSmgFZQDng7TLl7a5rFyoa1-xUulvsmsvEgzwisT-8qJdNn3CSEcujvJp3WMNMIj5p54Ql2EMVDoohgsItRUY90_OrkMMFF_FWPLAQsRFmGy_GCFgUvJIY9ec2kbWp2qHm38K2ILsUTlktR1VZoQISPOpCQ0_o_LUNjLfFB-b-Q9ggfgamT7OlCVU0dYI4wyKPTVtalRJUh4YULKkIjVQA584KPjPNh0oiX1UyOll0zk9rn6NjhhMKpkgMMaFYaOMW8os81h7m47Ra9V4W5Xu2JyQUZ7Dy_V3qt9NR--skY4dUWHuc9Vy3 "LAYOUT_LANDSCAPE Sample")

## LAYOUT_WITH_LEGEND() or SHOW_LEGEND(?hideStereotype)

Colors can help to add additional information or simply to make the diagram more aesthetically pleasing.
It can also help to save some space.

All of that is the reason, C4-PlantUML uses colors and prefer also to enable a layout without `<<stereotypes>>` and with a legend.
This can be enabled with `LAYOUT_WITH_LEGEND()`.

```plantuml
@startuml LAYOUT_WITH_LEGEND Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

LAYOUT_WITH_LEGEND()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_WITH_LEGEND Sample](https://www.plantuml.com/plantuml/png/PL1Fxz904BtlfnZnG4cm3SQJ9sebO0BOs2Bnr2pjQ3VkdytkD9KOlxlJW63osyjavxsPzzwi8yb0Wz6mpxzzFjND-LEzQ_QRxURu4Iffl4RnIjbM3nr2J-JZ-omBSan_AEg7on0njCuIMafRPxAVAhHzf3uhthqfjRHqEkmp_CLuXnqtcuB9KbaCgMTH8Lwg9WiXIWpHsKHsHjabpFAfgaX1aWkpXQYkaT0q7znWEnckIRjQmlncThw0tmBuFOII4I-Dz9xtdF42kVTQjPAKipDk5Q-Na5TbUjpKF18GtgOhE7mj9YpNseqHfemHo047z98fPj2aM0lgKH5X0586DMj5zlRdxYwX6yXxxZG6nHVK_r8zRPqYJtBTrNLPCMiYFT3dcYrIv2zEvNjmvl-HDH-Ox_aN "LAYOUT_WITH_LEGEND Sample")

Instead of a static legend (activated with `LAYOUT_WITH_LEGEND()`) a calculated legend can be activated with `SHOW_LEGEND(?hideStereotype)`.

The calculated legend has following differences:
* only relevant elements are listed
* custom tags/styles are supported
* stereotypes can remain visible (with `SHOW_LEGEND(false)`)
* **`SHOW_LEGEND()` has to be last call in the diagram**

```plantuml
@startuml SHOW_LEGEND Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")

SHOW_LEGEND()
@enduml
```

![SHOW_LEGEND Sample](https://www.plantuml.com/plantuml/png/JKzDR-8m4BtdLyoo1uB49cArfpsHfWWEGACcb6DaacbZrH-MFL6AglxtJbGAzUN9ypxqtZAGyDHh5VsIfb5zYz0HkV0_JRqOaXT9NN_g0_h66a93IMDr-YfzqmNgqlpVdq89GuVTDiKtvbji-LZdB1RIe4_S61qLw8CriMYrD7EOP2FAG5wGzPDPL9u3eQxlR6zQuSznivZ3j1JQAPpEu3q2VjV8UC1JBPpZd2EU87DEoKQGj6R2f_pt7BAoIFQhYYqUuM-oWDrJFdAPKdO8CAu9G1PuYXCiqRqYwHH2DKWYz41Iev860tVxkBIBwOlad8kCoUWHrVUgMwr3O2VZfggAabMZwChUOjP8WRyumhEt-gSbAZSFntgxMg_sz_4iMg9fUwq-0G00 "SHOW_LEGEND Sample")

## SHOW_FLOATING_LEGEND(?alias, ?hideStereotype) and LEGEND()

`LAYOUT_WITH_LEGEND()` and SHOW_LEGEND(?hideStereotype)` adds the legend at the bottom right of the picture like below and additional whitespace is created.

```plantuml
@startuml Layout With Whitespace Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(a, "Person A")
Container(b, "Container B", "techn")
System(c, "System C")
Container(d, "Container D", "techn")
Container_Ext(e, "Ext. Container E", "techn")

Rel_R(a, b, "calls")
Rel_D(b, c, "uses")
Rel_D(c, d, "uses")
Rel_R(d, e, "updates")

SHOW_LEGEND()
@enduml
```

![Layout With Whitespace Sample](https://www.plantuml.com/plantuml/png/LT2nJiCm40RWtKzXEhaI90iJKo69O0XGDK8PewjzmX6E4zbdqRuz5ogbpHJxk_zNJjv5Wa1fSBA6yvX8jZrPsTgUC4wWKJOmJ0x5NU-rImQb9PhYKvu7-Cs-EPkEAMBGeoVqbEbno7_we6qacnUF3ti7dhxUwnnFF3Te6Bk2mz1x3Dd4FnPYZo6ENi6zt5oEydcp5KjA7NcmtEJBXg-4sdeEDUT8E2ZDT3dAObKrgsfvMrsugqwaa2VypUGrNTscnG5TTvXtdBVHu5nadR5KB9enHRmQWraPbnbmjia0_RDetZxRhgvUguzIRSKElU47-GC0 "Layout With Whitespace Sample")

Therefore a floating legend can be added via SHOW_FLOATING_LEGEND(), positioned with Lay_Distance() and existing whitespace is reused like below.

- `SHOW_FLOATING_LEGEND(?alias, ?hideStereotype): shows the legend in the drawing area
- `LEGEND()`: is the default alias of the created floating legend and can be used in Lay_Distance() call

```plantuml
@startuml Compact Legend Layout Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(a, "Person A")
Container(b, "Container B", "techn")
System(c, "System C")
Container(d, "Container D", "techn")
Container_Ext(e, "Ext. Container E", "techn")

Rel_R(a, b, "calls")
Rel_D(b, c, "uses")
Rel_D(c, d, "uses")
Rel_R(d, e, "updates")

SHOW_FLOATING_LEGEND()
Lay_Distance(LEGEND(), e, 1)
@enduml
```

![Compact Legend Layout Sample](https://www.plantuml.com/plantuml/png/LT11JuCm50VmUpz5tQaa2Z7nv6aJS9hWjWoDnwQqBuDO2caVSVlsFhR8nedsz_x_qBnbGELnQ2rFkxPN6da11t265-hK3SXBrVOMs5tZj1qCy1gn3yz9ujLlV6Ym7geXWDUTGt0OwwvDVXglwu1raZuzxAno-FLH972akG53A5CAgyQ1ZtlwBsCxyA5pGjtpnUN8Luk8JIbHqM2wyPS5NH5qxIXKdW92ApJHvSZJMTNCgjbjTMAP7r40JUWRysiwlqspFLYv7zzOaMfbRI0TCHCacf3sS3K2CpCg4y1elL5uPbQ-RR_bQx5TVRvlrhB8r_ac4n6ZrSki2QYS1l6lv_9Zn9RW3Atj3m00 "Compact Legend Layout Sample")

## LAYOUT_AS_SKETCH() and SET_SKETCH_STYLE(?bgColor, ?fontColor, ?warningColor, ?fontName, ?footerWarning, ?footerText)

C4-PlantUML can be especially helpful during up-front design sessions.
One thing which is often ignored is the fact, that these software architecture sketches are just sketches.

Without any proof

* if they are technically possible
* if they can fulfill all requirements
* if they keep what they promise

More often these sketches are used by many people as facts and are manifested into their documentations.
With `LAYOUT_AS_SKETCH()` you can make a difference.

```plantuml
@startuml LAYOUT_AS_SKETCH Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

LAYOUT_AS_SKETCH()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_AS_SKETCH Sample](https://www.plantuml.com/plantuml/png/NL1DQzj04BtlhvYw1ylWIhZqr9DLOMgetOfARib9hAL9j6G_bjqHYWdvxnbXnmxPox3ptinxRzQHPA31QDZbTtyETPDNJVLhKnTRgAJn6iKdPLizT0WzaO_Viop8CNrGr0_78M9edIMqbBREP8ygj7saFYk-VIcrj7JOxp9yOhp3ZfjDmMIfB8RKiwGG7pMJXH0bXkXi8ZkZx19c-LHLf239XTb2LAT8Q9eVRh2T3AUaNIrXVhOwNy2p07vNcMJ4OoEzvpt_yGYvzrgrafIpCsuLdvUGLsNwUrFpI43ucgvW_w-Oi5nhDqQO4aOW1npFIwQOGPDYBQX7HOG1I1dKh1NPsyl5NK9daFTSQ0oAlwZVKjri7I9FSjtMTLanQo9TqTkQdqYHlpYL--3C-v4rdvUl-Ge0 "LAYOUT_AS_SKETCH Sample")

Additional styles and the footer text can be changed with SET_SKETCH_STYLE():

* `SET_SKETCH_STYLE(?bgColor, ?fontColor, ?warningColor, ?fontName, ?footerWarning, ?footerText)`:
  Enables the modification of differnt sketch styles and footer.

The possible font name(s) depend on the output format (e.g. PNG uses fonts which are installed on the server and SVG fonts have to be installed on the client).
Additional is it possible to define comma separated fall back fonts (if the diagrams are exported as SVG. Atm
PNG does not support fallback fonts based on a PlantUML [bug](https://forum.plantuml.net/14842/specify-fall-back-fonts-is-not-working), but this could be fixed in one of the following versions)

```plantuml
@startuml LAYOUT_AS_SKETCH Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

SET_SKETCH_STYLE($bgColor="lightblue", $fontColor="darkblue", $warningColor="darkred", $footerWarning="Sketch", $footerText="Created for discussion")

' PNG with font jlm_cmmi10 (typically another font is used)
' SET_SKETCH_STYLE($fontName="jlm_cmmi10")

' SVG with fallback fonts MS Gothic,Comic Sans MS, Comic Sans, Chalkboard SE, Comic Neue, cursive, sans-serif (typically without "MS Gothic")
SET_SKETCH_STYLE($fontName="MS Gothic,Comic Sans MS,Comic Sans,Chalkboard SE,Comic Neue,cursive,sans-serif")

LAYOUT_AS_SKETCH()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

PNG with font `jlm_cmmi10`

![LAYOUT_AS_SKETCH with custom style png Sample](https://www.plantuml.com/plantuml/png/VP9lQnf14CRV-occru06BjgKlYe8iOSaqCHAxvAGLyVUtkXjtJ_7xcojb7xtpg962srzixVpF3FFRrXl0WbFqUZ16sMbZYr2HzI7ZvE95zlnMb4NcnZGIsS9BOsbCvEDyh8Br4sA3rTBBImzFjnFy0VhBRPSh0is2sNHZ_iqUb3EgxhyFA-AkxgiNkxdeujcNJZj_3JJQjrHeoDcELoikEzGRuNV7CjRuQsowpF5OxltEqB_l9UdMRb1ajr9g9XfcXKU1M4BA-UXLK7649IpsULWC8JbuXQsl2EaPFYcJIsDKTVlO4IxNacXzGw4TTIXtrjKW1YmlVpBIabV28FJx3Hddr8-7LDuO2Fa1f8tm4C9jpnRoRnmHaaeXKt574vN_kw4tZHE-1RA-L5QOCGSPFH1VUUFmCwhW5wjpi5Jf8i4sMiEumpXV-J_8Ze3-fFd3ET8Su99sz_FNhuyLlMiF6IEkBP47vmTYTOecqCsIwSAv0KvpptbBX2Q-fEBjXL-DvBNEGnBONgDmqluEG3-lVx3HbjiQj7tFESP6vZrlURrARqmbugtESpAvNWnhxZ58xmVNyF3Kv6qcTPkcvwJQO0SI6TwmHOJDIdEWcghYD03AOEQimAp_JhGZMWlyfo3BItx5VLngnFMO-1EFk-gQbcoAvbUrTEOMwJ0Lqp7oZjptdA3jer6_mO0 "LAYOUT_AS_SKETCH with custom style png Sample")

SVG with fallback fonts MS Gothic,Comic Sans MS,Comic Sans,Chalkboard SE,Comic Neue,cursive,sans-serif

![LAYOUT_AS_SKETCH with custom style svg Sample](https://www.plantuml.com/plantuml/svg/VP9FQzj04CNl_XHJDH055BifFHKCSOL9e8bhAZaX9x5QZQsjzu_O7TKrfT-zizYEN4hhosfdthpt6zQtWOIdtkZH6sMbxXk4bgWB7oSJBtRZZQAsh_k0NZfBQ6aidPbibPTje7QIVxXUQc5fzVWmmH_SRx3XOfMpM2YBVjn5wr4nBwlYyxpCxwkYV7cOfnVr9dVQ-McYrQQbMlUOP72nvhbZlH5-UohlXBVARiuw7fk3tX7wvqDxcXHR9DaEZPAPfadkKH0si7OU6XLa7u9oDhaQZIvXkRY37Uy8CHc-QLD9OzJDEqXftoafjDw3i8vQz0U92j07RAvuzk-bec8X34wJmUcGKpoTSjYo5d8BKHlWiO0xTbSoovrH4WfXOp63uShVhT3RsWdVSEQfjS0UCv2z3-exVmHMNWVqQdsE7YDTJv2yvZ3E_xZ_nNE6yoVD6So9PK29kp_CNhwiocfM73DJhYtH1sTJqHXbCqXcyLI1l23d8-0-49hga-jj8_m-bJSPN1R2T1elh-3d2FZt-WzBTrXNeklOvnbhc7MTvkKflZ2NyhSPp8hbU34lUSGZl1_VmEDJ7diphTqkFYVJ03cGpdI29QRNf3WBofqYGW-a36hE2ipswqYNqg79FaTPNFOhwjDM0zOgy2IVzsMvB5Z5eW5wiBb32dp5UAozC-SZjsYRtkZV "LAYOUT_AS_SKETCH with custom style svg Sample")

All available (PNG) fonts can be displayed with

```plantuml
@startuml
listfonts
@enduml
```

## HIDE_STEREOTYPE()

To enable a layout without `<<stereotypes>>` and legend.
This can be enabled with `HIDE_STEREOTYPE()`.

```plantuml
@startuml HIDE_STEREOTYPE Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

HIDE_STEREOTYPE()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![HIDE_STEREOTYPE Sample](https://www.plantuml.com/plantuml/png/NL1DJ-j03Bplh_3hEpIL-XBrYHEdXX1H90fHau8uHTl4a1NxiTfr52h4VsUZbXPnikmPpuozzCGTzKh2wlOwhyigt-GFrNEHGycLbSZ-2Dt8laNeYAo_J1B7X_XLKDVlUe-kCPfGKzmObRm9rtIUkYIx-5T8hccxlalmFU0jjc5OPu7CXKONs-38s2_BQCPOWSuR7V5M2Js7IJfMuSbnCcuoO-NU4whwolIwvMuVDOivJ0z9fpFuO0009vTem5tDhGqwJxY3r5ef6ax2w4aOPN_da9P5V9zNOSKX_8yNi7xCHYoLqWmUnWCza876ACi3HVMIX9K8rI28q049XL9ez27Rvp5TH0Smw1nf0MGRbDzNdMDjFVhHRrLLHHbO8-c4dcLka7neSImlpgYVAylmtV6PNm00 "HIDE_STEREOTYPE Sample")


## HIDE_PERSON_SPRITE(), SHOW_PERSON_SPRITE(?sprite), SHOW_PERSON_PORTRAIT() and SHOW_PERSON_OUTLINE()

With the macros `HIDE_PERSON_SPRITE()`, `SHOW_PERSON_SPRITE()` and `SHOW_PERSON_PORTRAIT()` it is possible to change the person related default sprite or person layout itself. `SHOW_PERSON_SPRITE()` is the default.

- **HIDE_PERSON_SPRITE()**: deactivates the default sprite
- **SHOW_PERSON_SPRITE()**: activates the default sprite "person"
- **SHOW_PERSON_SPRITE($sprite)**: activates a specific sprite as default sprite
- **SHOW_PERSON_PORTRAIT()**: activates portrait instead of a rectangle
- **SHOW_PERSON_OUTLINE()**: activates person outline instead of a rectangle

"person" and "person2" are predefined sprites which can be used as default sprite too.

```plantuml
@startuml predefined sprites Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(userA, "User A", "with predefined sprite person", "person")
Person(userB, "User B", "with predefined sprite person2", "person2")
@enduml
```

![Predefined sprites Sample](https://www.plantuml.com/plantuml/png/XSvFYy8m40NmUpz5jgTTs6sWx6bF_NDTeI0zIqn64qpJC9bGFxvJKHGyUCeG7h_tcaGAAKzUH0G31nV0Y1JH4IInLLFqK7oue7qs82nHJ7zIebggeoERzpa1wZaG1AhqFCcJGsqJMTd__WnU1Het_nBE1C60uSzTps759LX5BYsA0J3DuNDrsczHZloAjkHhOVzrauZN_1guNL_FH7SdkhT4_J1gHXfUo8Ck "Predefined sprites Sample")


### Using HIDE_PERSON_SPRITE()

```plantuml
@startuml HIDE_PERSON_SPRITE Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

HIDE_PERSON_SPRITE()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![HIDE_PERSON_SPRITE Sample](https://www.plantuml.com/plantuml/png/PL1Fxz904BtlfnZnG4cm3SQJ9sfjX4ImeKMFpTAETkF-sUnEKudnkpiD22Q_NYQTz-RzsMqa6MWq6dRxZsLRbQVwox6jgzE-AQ6MnciKhvJjzDWZ34G-li-o8AVqXw9Xl8mHG-SieQMqSoRxgK8tH1goujsRIajBvyFd37yntcFFoxPWibGMG-hPL8YNhibAY0f3T3QHlL5s3OjydYfIaEJ2OYNgQoGqxGStsbw6Qz9jrh2yXLskuBS0_Xv6oOINLdhFEj_m0hdtMdMIbBCBNXMlrv3NLNei6pu926_J3Ho-5ZEMQ-sc27F72EI02th953DgKkm5pQI8C00fWvgz8cVxSq-Nq0radJkDGN52_Q_LCzOvyYNFNTDKDRDcqWDzodn2YloBy_WUdFd_P8ksv_Vy2m00 "HIDE_PERSON_SPRITE Sample")

### Using SHOW_PERSON_SPRITE()

```plantuml
@startuml SHOW_PERSON_SPRITE Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

/' Not needed because this is the default with sprite "person" '/
SHOW_PERSON_SPRITE()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_PERSON_SPRITE Sample](https://www.plantuml.com/plantuml/png/PL5DZvH04BtthoZn09ECa3MUF2sIYMlYpfA1TO-aQMgbOtzqkelWnlZVBPpHCP5BXNgltaVwDf6Cj5W3tTt3qz0UJjt3SUZQqwV-09sqmQ1ufPqoouGm4uNqlggYNCklckPbN196vHsXer9vMttJKSs9vgfvzwOrqj7Z_USAlpC-uSJBeM6or0vZ6TXKY2g7eoTmY4o04PLaIQ1P9z299yA4pt8n12iRGWfH4q8MC2RlCiWhyN_kOYT4-vjGoCbgjuUitgPE52NvcEr4zv88xV31BswIyQLGDtl8ptNp7VmGmD_VgCMAuo13O9qd7A4EmMWbINC0NZMlzr1tRNayz7mI4TwMDt3_fTcmsXY_9k1ACG5vKDu6oHJBXJHxGS-j22EGjcZOAt6sdvTq1Pr1rhdG61GdD7zQNMCz9hxaUTVtRSSi9br3NsK-8YN-nMqyHs__FRb5DsqlyWi0 "SHOW_PERSON_SPRITE Sample")

### Using SHOW_PERSON_SPRITE(sprite)

```plantuml
@startuml SHOW_PERSON_SPRITE(sprite) Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml

SHOW_PERSON_SPRITE("osa_user_green_architect")

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_PERSON_SPRITE(sprite) Sample](https://www.plantuml.com/plantuml/png/ZP1FQzj04CNl-XGRzn0PR8c4ddgAAqnJQ19XoSrHh5UJQEd-MNPcSKtfT-yiTknIUeWkOlQzcVURkKEIaP8rehj_UXxQzQPxUXowTlErNvSOeYQOYqxQOA2uqawPD8AOY09-gkiezzMhfYdj4a9KtX4ugfItzGyTrOGqrSt7PMkae-t3jnf-iZx2o8z3msQf7SGgS7XnDS8BLyAZRBb-Hq8J9KumMkt6-YrXwGCu19KO-o2PG1CeIX5kbvfxiROI2U9baLDStNXhlJkX_2jkERcMnXpbuZztch5ro833QmHmmpbwDY-A5Y9wLygCkX2pLVvhf2Z9HzQx0nBOuRDFRfJnKAgRXRW-7lnwBduLWh_piSezx0OP0izvXfrOXM2qagIzc_5Jys4XLbrRFQvxReaWRgiRyV2zoThA6Bz7aI5Ha1VAso3POfCXpLcYtsiYY8Aq1SDPo6o_JtGb7KMUSxBbnJPWthQwO6qHCEVTzttRiIkRpkfbp1SWv1BoxoLw-tVB7RWnMVC7 "SHOW_PERSON_SPRITE(sprite)")

### Using SHOW_PERSON_PORTRAIT()

```plantuml
@startuml SHOW_PERSON_PORTRAIT() Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

SHOW_PERSON_PORTRAIT()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

' if a person is combined with a sprite then the rectangle layout is used again
Person(person, "Person with sprite", $sprite="person2")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_PERSON_PORTRAIT() Sample](https://www.plantuml.com/plantuml/png/RL3DQjmm4BxxAQRRmdfXQvFGKw4GTmbDeScQjTCSZTQUh4Nr8wGHxbBwxXrLJT93VB2acM--dxaA93n5hQ2xsJyCxVMXszyDxVxG7vglVRc1JcYdi7WZpQZYX30JkV2nhhrOgfEaEHvZG3zQGsYe6gskVqW_pe7cUlVXVQk4eVlRRpN-93GJJbmSTjQGa0PzvLYuA5vNBeeMVR2c59EMPWkh9fqoa1Ta_MfJTET0g8VFDff9-7CvNcnXdUskD_2h0FwUfSe5ZuDmZdaUy0YDSqgEWgGrAoxjtcwXwThgxhhd4OzmMLt0xVTTwZLAsIL0IXc0B8nMEy4G7HL9fn3wHHAX1v8Q5Mi5zlRxdxkISfDvCYmPBzOW7q60-viFP4YSHvwSW34pTuBpaX1eHfD-u74aOKuifiJPHaepCJ1Ud3ZTqw8o7qlbToRBL1paNRvzMcNOPJ9oGFMqtfVzt0SCAVXDtxSTenBekVkIvmjIu2Ucuz5R_V_85PefQlK7 "SHOW_PERSON_PORTRAIT()")

### Using SHOW_PERSON_OUTLINE()

> This call requires PlantUML version >= v1.2021.4!

```plantuml
@startuml SHOW_PERSON_OUTLINE() Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

SHOW_PERSON_OUTLINE()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

' if a person is combined with a sprite then the rectangle layout is used again
Person(person, "Person with sprite", $sprite="person2")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_PERSON_OUTLINE() Sample](https://www.plantuml.com/plantuml/png/RL1DQzj04BthLqpTWcLm9H9wAXJY6jCK4bj4SdCKQsbYBTsFPNSMrvJ-zyvsaxY7wA3PtVVclNbp4qXuYbf1Uxjxx9lDGxlRzhjzT_TzkoaNq0hj51Rlf1bK714c8XS-rxKNf-eeQOg76D0FrX0QgWQhwv_I3rEWgLv_-jWeOMX_VrVZByP77FcnNpDPI8E-SknR56yQ5qM3FbXJYb5BiuJPAbKPo0koVhOesdCWrFrN6yqe_BaShfOmpzFE5_2x0FvUdSeJ7dhX7EiyuW5MpYav29BMpFXf_Nu9gxQfjfkEMpp2TNK5zp_M2LifPKy1KiW0P84JEi4K7HL9zeBk98dG0qcDYhq2p_RdURgICiWwppG6Ypd89n3W_kK36PBcWJj7OCx4I71U4W9DQD8FF0uap97Db3ZRIAad1kQB8wTxMLJMOwjyps9PYeDyoASliqoxJeCye7fPxsK_-y0HkDvsNTCoAv5UqKkURqY1hvZAaxVw_vORD6FKwYy0 "SHOW_PERSON_OUTLINE()")
