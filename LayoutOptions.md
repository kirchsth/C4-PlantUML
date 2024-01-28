# Layout Options

C4-PlantUML comes with some layout options.

- [📄 C4-PlantUML](README.md#c4-plantuml)
- [📄 Layout Options](#layout-options)
  - [Layout Guidance and Practices](#layout-guidance-and-practices)
    - [Overall Guidance](#overall-guidance)
    - [Layout Practices](#layout-practices)
  - [LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT() or LAYOUT_LANDSCAPE()](#layout_top_down-or-layout_left_right-or-layout_landscape)
  - [LAYOUT_WITH_LEGEND() or SHOW_LEGEND(?hideStereotype, ?details)](#layout_with_legend-or-show_legendhidestereotype-details)
  - [SHOW_FLOATING_LEGEND(?alias, ?hideStereotype, ?details) and LEGEND()](#show_floating_legendalias-hidestereotype-details-and-legend)
  - [LAYOUT_AS_SKETCH() and SET_SKETCH_STYLE(?bgColor, ?fontColor, ?warningColor, ?fontName, ?footerWarning, ?footerText)](#layout_as_sketch-and-set_sketch_stylebgcolor-fontcolor-warningcolor-fontname-footerwarning-footertext)
  - [HIDE_STEREOTYPE()](#hide_stereotype)
  - [HIDE_PERSON_SPRITE(), SHOW_PERSON_SPRITE(?sprite), SHOW_PERSON_PORTRAIT() and SHOW_PERSON_OUTLINE()](#hide_person_sprite-show_person_spritesprite-show_person_portrait-and-show_person_outline)
    - [Using HIDE_PERSON_SPRITE()](#using-hide_person_sprite)
    - [Using SHOW_PERSON_SPRITE()](#using-show_person_sprite)
    - [Using SHOW_PERSON_SPRITE(sprite)](#using-show_person_spritesprite)
    - [Using SHOW_PERSON_PORTRAIT()](#using-show_person_portrait)
    - [Using SHOW_PERSON_OUTLINE()](#using-show_person_outline)
  - [(C4 styled) Sequence diagram specific layout options](#c4-styled-sequence-diagram-specific-layout-options)
    - [SHOW_ELEMENT_DESCRIPTIONS(?show)](#show_element_descriptionsshow)
    - [SHOW_FOOT_BOXES(?show)](#show_foot_boxesshow)
    - [SHOW_INDEX(?show)](#show_indexshow)
  - [Optional support of additional PlantUML elements](#optional-support-of-additional-plantuml-elements)
    - [List of supported PlantUML elements](#list-of-supported-plantuml-elements)
- [📄 Themes](Themes.md#themes)
- samples
  - [📄 C4 Model Diagrams](samples/C4CoreDiagrams.md#c4-model-diagrams)

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

![LAYOUT_TOP_DOWN Sample](https://www.plantuml.com/plantuml/png/JL1FxvD04BtlfnZh0PfKI8qdJqKqUkWV8jJ64rbWAXltpsPt23R6x-uGQ_lZyiAyDs_Ulbqa6MWoMhnIjjVJW30I-VW-puESin-AngcR8eRUMK9BMUzC_bE5VemqvkMxDvMMbiw7VOw_c1zmu65RibWgYo7pYxN84pWw0el80kYmbsm9DAe8AZ8Y37YLaoP8Sh4llf_EJTkSglRZwN9Crq9K6AApgHoCiXjO5GkgI46I2wkrg6-HqBGVt6G76Mvflzr0KalZDIPh-2s0lqUaTCQkbTwppmKxABpNgfUad5tng7ozWQAkikEdXbS2mjji2uTlvS8LMhivmj86XtR0LNZ94iF15T-2PbP4682KGSst8cVxSq-NqZ-IVUuo9iLNrFzVzOnrZhp9-ALfgffLY-Z1Fcq-8qN-nGMkmPcNApkq0pV_5m00 "LAYOUT_TOP_DOWN Sample")

`LAYOUT_LEFT_RIGHT()` rotates the flow visualization to _from Left to Right_ and directed relations like `Rel_Left()`, `Rel_Right()`, `Rel_Up()` and `Rel_Down()` are rotated too.

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

![LAYOUT_LEFT_RIGHT Sample](https://www.plantuml.com/plantuml/png/JKzDJy904BttLwnue2JO1kF94xL1C05jQD5uQfPsj1ltOxCxcqgC_zrfH70lavttvdtCFNA7GSdeGkX6XXPOXsZzRPewtYVl0hkm3nvSOpI2ngGnAlqGhkayTcb-SrL8hd6tMQVmINWBBIthdCXSQ7297QIZTVRwjAlgzUA-ghSForKLJwAe0EUDZdchX9woKJPCuT5nD6uqYSg3Hr3rdGcwvUuGDxCf6vTSMGdZ2VkA6BsJJzp3lkRMaiuBx5bchHGDHs7qY5RvvPHbPP4yBYewSS2kandRFES3babfUi-6YfwXOTJFSgAe856G5wjwWGYEeL0WoSjJjkzZkXX_GT8vqWYCjY3_MfrZxJnTqbnLLL4IQo2TqBFC4j3J5uRnvepwVp87tGObVm00 "LAYOUT_LEFT_RIGHT Sample")

`LAYOUT_LANDSCAPE()` rotates the default flow visualization to _from Left to Right_ like `LAYOUT_LEFT_RIGHT()` additional **directed relations** like Rel_Left(), Rel_Right(), Rel_Up() and Rel_Down() **are not rotated** anymore.

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

## LAYOUT_WITH_LEGEND() or SHOW_LEGEND(?hideStereotype, ?details)

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

Instead of a static legend (activated with `LAYOUT_WITH_LEGEND()`) a calculated legend can be activated with `SHOW_LEGEND(?hideStereotype, ?details)`.

The calculated legend has following differences:

- only relevant elements are listed
- custom tags/styles are supported
- stereotypes can remain visible (with `SHOW_LEGEND(false)`)
- details can be displayed in different sizes via the `$details` argument
  - `$details = Small()` .. default; details are displayed with a smaller size compared to the legend labels
  - `$details = Normal()` .. details and labels are displayed with same size
  - `$details = None()` .. only the labels are displayed
  - if `$legendText` contains `\n` then the text before is the label and the text behind the details
- **`SHOW_LEGEND()` has to be last call in the diagram**

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

Legend labels and details can be defined via `\n` in `$legendTest` arguments too.

```plantuml
@startuml
' convert it with additional command line argument -DRELATIVE_INCLUDE="./.." to use locally
!if %variable_exists("RELATIVE_INCLUDE")
  !include %get_variable_value("RELATIVE_INCLUDE")/C4_Container.puml
!else
  !include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
!endif
' $legendText with \n defines the label and details of the legend entry ("backend container" is label, "eight sided shape" is details)
AddElementTag("backendContainer", $fontColor=$ELEMENT_FONT_COLOR, $bgColor="#335DA5", $shape=EightSidedShape(), $legendText="backend container\neight sided shape")
' $legendText without \n defines only a label
AddRelTag("async", $textColor=$ARROW_FONT_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DashedLine(), $legendText="async call")
' if no $legendText defined, $tag is automatically the label and all additional displayed properties are the details
AddRelTag("sync/async", $textColor=$ARROW_FONT_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DottedLine())

System_Boundary(c1, "Internet Banking") {
    Container(mobile_app, "Mobile App", "C#, Xamarin", "Provides a limited subset of the Internet banking functionality to customers via their mobile device")
    Container(backend_api, "API Application", "Java, Docker Container", "Provides Internet banking functionality via API", $tags="backendContainer")
}
System_Ext(banking_system, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(mobile_app, backend_api, "Uses", "async, JSON/HTTPS", $tags="async")
Rel_Neighbor(backend_api, banking_system, "Uses", "sync/async, XML/HTTPS", $tags="sync/async")

SHOW_LEGEND()
@enduml
```

![SHOW_LEGEND Sample, $legendText defines legend details](https://www.plantuml.com/plantuml/png/hPFHRzis4CRV_LTSr1Ip0TV6qFLbW86wjhQcSEB0ThOz531EqbacGf42UN9Z3FlVTvGYJNKox6Lv24mTx_ZxFdxyw1aTLuKU_02fDITo38hXc-8ZO9OfLjQWbb9HeCb0AqE0BgyACWplbfjuDT_T_1RlR-uMguTbF8icqyaa0hPGUG9jKzJwFBXI1tXxGgSmqRId9-NP3wFBvcWq0BXI9jLLHl0s9zvtFIVK5RtMCbtyj5zOmoXaRb869LUaFVL77PbB__Dqwl3R91TbLI9mBfKkKJ4HRTD7vTAZvwDCUtUlqV33xMfAJrBFA7lr29EfWtXshIcNtplPsvZsrK161zdfWOy46XFI4ApBI0Pe3_RG5Ee-401tXc6KOFeOrcbxJWJADzrZY4ZbHmQl10Ry4KiArNRY20RpB8irXJlPOTuDwvYZCLmVPB6mshhPTRoAR-ExtVwNjVnRh5VhZTIJlAb6Rzw__x2SVmWzzL6pE1o-3MTlmteu6lTLprwYVpKlUKUlU6KhxjjbZJu3DffhIHlIjHpqPvC67gQdLiDyird_ti67MFvhOSjdJRCb-YDbAsLU26ZcGqXgZIbPDRQ_uvam2mIO1-UnObiWgphT5_Sid_el9rE-r7WM8qfdItAiIFeTXQxs1ljY0ylq_r5icLl5ey5WU_PCnVwJhKo6xZnCVvHWtHWcPuZX4vf7PV9e17yEGFwwx0mBcoXDUonBsNzRBs1Ubf6i5c_6y0SMw9G9otjdJoeBya2hGd6u_2hnn6tckzEIvZGuL2PjV58iFbf8Ao_EalDmKXXwb8C6GBmwgLI2T87td3xXKu8mlxy9S5gb6EO6gYzumZ4ihMnp__JrUV-BAw38uAYvVpzxyRu4wg_Mt_Y9XyzZzhx-56oJRGU71RK-GxCxK6pPkk2PrgrDgNpeKAJHkg9M0vY49zDvD0PCKxbEbb_iq7YieML5d4u4QY2X-kx-lZVhmPCNWYR_O_YoNTzDF-zszzjEQLEIIJ9eVnTUTM8lBB_Gsatj1Lb2ShkwcDmh1z3jPudmAlurlbiEHuEFChqgzDy0 "SHOW_LEGEND Sample, $legendText defines legend details")

Legend details can be deactivated via `SHOW_LEGEND($details=None())`

```plantuml
@startuml
' convert it with additional command line argument -DRELATIVE_INCLUDE="./.." to use locally
!if %variable_exists("RELATIVE_INCLUDE")
  !include %get_variable_value("RELATIVE_INCLUDE")/C4_Container.puml
!else
  !include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
!endif
' $legendText with \n defines the label and details of the legend entry ("backend container" is label, "eight sided shape" is details)
AddElementTag("backendContainer", $fontColor=$ELEMENT_FONT_COLOR, $bgColor="#335DA5", $shape=EightSidedShape(), $legendText="backend container\neight sided shape")
' $legendText without \n defines only a label
AddRelTag("async", $textColor=$ARROW_FONT_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DashedLine(), $legendText="async call")
' if no $legendText defined, $tag is automatically the label and all additional displayed properties are the details
AddRelTag("sync/async", $textColor=$ARROW_FONT_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DottedLine())

System_Boundary(c1, "Internet Banking") {
    Container(mobile_app, "Mobile App", "C#, Xamarin", "Provides a limited subset of the Internet banking functionality to customers via their mobile device")
    Container(backend_api, "API Application", "Java, Docker Container", "Provides Internet banking functionality via API", $tags="backendContainer")
}
System_Ext(banking_system, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(mobile_app, backend_api, "Uses", "async, JSON/HTTPS", $tags="async")
Rel_Neighbor(backend_api, banking_system, "Uses", "sync/async, XML/HTTPS", $tags="sync/async")

SHOW_LEGEND($details=None())
@enduml
```

![SHOW_LEGEND Sample, hide details with $details=None()](https://www.plantuml.com/plantuml/png/hLDHZzf647xdLymv5nKa0ghIl5H22W6tkOY34t1j7oAXiJsOrQrthTqnEQlgV-yi1jVXhkfBx-74UFQR-Rvll_te6HrNXUxz0AarHt8CYk6RuWDWbYbMrg2MLb6WoK0hGu0khmeo3E_cwtWntTxz5k_kbhF5upoUHAFnQ1G1MwWyWROfQbttRjGUtXxHAKmqxUXPUVRzw1eS3Ne0Dygakie8tkR4knPpH5tHQv3nxAVTp1f6OUP6PL1oGzfJTzI1kVG_ZySEluroKLObGiwbWX8L8z4sVb8kFNW-oBHt3neDFzulnlGi_OooLrUOJEt5irjDkVpUojd6jAy6CjhBIGzy8D2Oa8PWNKOoG7km-wPnme4GS3NqemJJfr2dbpqHAD-WXn2HoWyCNWaPy0SiANGl4mVGcsPPh2dSoHRpTbZBEHh2xLwAcTNMJMxZHNmVBxUxNrRoRxPQhDRIJ_Ac6xrv__x3VFeXO4wh9d5OlWcxDw7k3uPTrPENrB-Qbtm7htXbA-xQPOsk0S-E1KbhqYSvw6kJ1ZuioBE6wNgz-hqb7sBvhuqDrvecS_G7oXPINmjevaD8weccPDNOxeapmommm3muZnNR0ba5J7rrp_Af-t8ovKkDjHXHEbkIOqM2TnHGbnliYWrSnl-FOijyKJpezJQrPofsdsnbCdHrF_rHWdLdc9mXXazedfJ9em7ysGFvQxFJBsoYDEsmBENy_Qc0QLb6KitU3E4FBD0f4ye7Puyg2_90gq9nkFmgySINpBVRacORx2kJDZuf5Xyjf9KNPybvE2eC6EMW8I1U7LKgGRgYTqwVy5D2OVfm5yXfbMAO6rXzmICEOMxbcFi7r-NxNxm25HaSDVVl9o_Vrw3tryNV-9dxvp4xV_eKR9DZUuS5NNo6vdHWiM7hWcTQNsnAvKDBHO3M5ISrW4buCgr7Gy0qbUja-SKEZSSJQQc8qv6Gwacelhk_xyrwzEI5GPF_8NpPh9RZpzljmwPLshHaaWpQBSEhJkoLvLTQswcT84j8xXTNaxiv3-7yB15UnB_6otd_zlmg9alRHFUZBAiA_JS0 "SHOW_LEGEND Sample, hide details with $details=None()")

## SHOW_FLOATING_LEGEND(?alias, ?hideStereotype, ?details) and LEGEND()

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

- if they are technically possible
- if they can fulfill all requirements
- if they keep what they promise

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

- `SET_SKETCH_STYLE(?bgColor, ?fontColor, ?warningColor, ?fontName, ?footerWarning, ?footerText)`:
  Enables the modification of different sketch styles and footer.

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

![SHOW_PERSON_OUTLINE() Sample](https://www.plantuml.com/plantuml/png/RL5BQzj04BxhLqpTWcLm919wAXJY6jCK4bj4SdCK8sbYB-nZsHqXJEb_xopAeuVeeDNEV8_vHhUHCV1eDDHtXwUssZtMXtrxE3Rtl_QxV0Kr6gyf-wHihyU1uCpiuxUo33WL9yNdiHiZXTvP9ij5xqpfDTeaU1LvqAehjr-lgbGwFjoN1YDJa5Ax5GOgIw7mWiso3zsphA8GdSrnCCgkOR59fueSa5rOhBBw8dgc_U56Es2uvFtr6fRpoCiL_Cb0dZUdVAAkHUz5vuaws7YlLO-id5r8QVjv3PkwAlQxHYY1uAQuXeVVszJRQEsc22bf17OWCJqAn8oQbNX1CocMOC3Aa1QlABFzVPakvxafEYymQMPBKC-0u2db0nMJPYVC0GHpbaxqGJ41dycc5mJg6Ur9p3HUtCY9CqR1uqdIlIvgrXEh-JwBpL8IvClyzNqnmsxI88-aNzVxlfzZb0XotZLDLGigWTwwxtb-4aUvKZgUWpF_Ksx93kdF_WC0 "SHOW_PERSON_OUTLINE()")

## (C4 styled) Sequence diagram specific layout options

- **SHOW_ELEMENT_DESCRIPTIONS(?show)**: show or hide (hidden is default) all element/participant related descriptions
- **SHOW_FOOT_BOXES(?show)**: show or hide (hidden is default) all element/participant related foot boxes
- **SHOW_INDEX(?show)**: show or hide (hidden is default) the relationship (call) related index (sequence number)

show is defined with `$show=true` and hide is defined with `$show=false`

### SHOW_ELEMENT_DESCRIPTIONS(?show)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Sequence.puml

SHOW_ELEMENT_DESCRIPTIONS()

Person(admin, "Administrator", "People that administrates the products")
System_Boundary(c1, 'Sample')
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
' in a sequence diagram Boundary_End() has to be used instead of  { }
Boundary_End()
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_ELEMENT_DESCRIPTIONS() Sample](https://www.plantuml.com/plantuml/png/LL7DRjD04BxxAOPmY2E5M4MSE3KOYrPgKgjswT6QUAVrYlrPTiSA5UBTcOMKK5z6dfdlPxwzJ8oHPskADzgDPbO44tD87wigud7pf7cQ3tEYE7h7v7WpUbjzqt6S4azL_U5TQz3n_UwceXyoLwIaENJqVIOtqYPavgAxkdqOcfjcr-pxuNFJrNVNRNzzk-_ALL6q59Dt9IghtHeMsrnrueZiuq8QBVbW27X21ZmFAKcB84Ilvf7JObLqpud93f_yx1J6vtAyMCEoGolevQe0-Mgv0RMZM1xfC608Glz01zY6OFI8hBtBYlNRDMoxThDlUe54WlUR2zXzhVDiQum_9iY9Y04F4aT0MR6pOPrzzaVDJ15OMpAYbPqjGJj0IATKG6byYcZXnUhGE5MkOC8_b0VAz4emYGaL-4U0d_2hUBrzEhValtfYxQGiUiKTcPT0pvVU9p4ZzQhlsqwsyjA_wPdc2t6INyhbCNhxF-IId98N_Gq0 "SHOW_ELEMENT_DESCRIPTIONS() Sample")

### SHOW_FOOT_BOXES(?show)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Sequence.puml

SHOW_FOOT_BOXES()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample')
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
' in a sequence diagram Boundary_End() has to be used instead of  { }
Boundary_End()
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_FOOT_BOXES() Sample](https://www.plantuml.com/plantuml/png/LL1DRzD04BtlhnZ28OuKR1LnujGq2lH0IOHToiqQUwVrYlrOTcTbAiH_Pmmf1Lz6ddaVx-rbPanSd5KlZ1zjqGGJSynlcoRXN3yOdifGCgKnU2RFzHXSyzMaSSeyDVithquMFT_UV6ZekzmrQLdsBNqhv4UguwAisklZNV_kUEpwg-ENGrjjb3fHoi5Ng9tnMrZjbcao9-IGLXlLFcOcrr-5uZMcnsgysCAwHHSjhJSAvDjB7ZIUKZNJq6ECed970-nYj6P4Di6lPBL_kOLTUwe_7ZgX98BNzGNSVDuljvsrOSwmjCl00QHQH86uOjc84tIpOQO4R1nPySgIR0t60q8-DmHjy26XWwUe_S7hQWCJ_fOSQ97Nmf4-g27S0_o0d-f_zBbknN_y9DhPMVpK9x9Fp_JSz3PB69dNNNTg1RM0_bwVPTuJP_cbPToduFwbN9BNnTbV "SHOW_FOOT_BOXES() Sample")

### SHOW_INDEX(?show)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Sequence.puml

SHOW_INDEX()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample')
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
' in a sequence diagram Boundary_End() has to be used instead of  { }
Boundary_End()
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![SHOW_INDEX() Sample](https://www.plantuml.com/plantuml/png/LL1DRzD04BtlhnZ28OuKR1LnujGG8ef4IuHToiqQUwVrYlrOTcTbAiH_Pmmf0Lz6ddaVx-rbPanSd5NFZ1zjqGGJSyolcoRXN3yOdifGCgKnU2RFzHXSyzMaSSeyDVjNBuuMFTzUVsZekzmrQLdsBNqhv4UguwAisgkFT_txcxU7BzL6gIEb77o5sXc_XTLkcIPpGWvfjL7jOsPo_PjGlCRqM8qNMrYtwAAbzKQ1V7k9WiPJgcOQUenHLEveW5sCrep89lYLhFRFjx1hZ_NDeHDA8dXPNy3rv_rosraRvWnBiGmSG5f558WhbequGJSRPah0nf4Lhop9rc0y8EHJET067n8wU8hQ7xokDZ3XRyc15daj7Ec36i8zm0_ugVv7d-fM_CTFefsSnKzz8llqJEUcjrd2oBpgkcChg0NqztgMUKUSvPUMSP-2-vToILuNPty1 "SHOW_INDEX() Sample")

## Optional support of additional PlantUML elements

More often a full support of all PlantUML elements are requested.  
They can be set via the new optional `plant="...."` argument of the calls

- `System(..., ?plant)`,
- `System_Ext(..., ?plant)`,
- `Container(..., ?plant)`,
- `Container_Ext(..., ?plant)`,
- `Component(..., ?plant)`,
- `Component_Ext(..., ?plant)`

The already specified `...Db...()` and `...Queue...()` calls are not extended.

But based on the additional (internal) overhead it has to be explicit enabled
via `ENABLE_ALL_PLANT_ELEMENTS`. It can be set with following 2 options

- `!ENABLE_ALL_PLANT_ELEMENTS = 1` directly in the scripts file
  BEFORE the first C4\_\* file is loaded, like e.g.

```plantuml
@startuml
!ENABLE_ALL_PLANT_ELEMENTS = 1
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml
...
@enduml
```

- or via additional command line parameter `-DENABLE_ALL_PLANT_ELEMENTS=1`

If `ENABLE_ALL_PLANT_ELEMENTS` is not set, the diagrams displays the requested "PlantUML element"
but the style is not correct displayed.

**A simple sample with additional "PlantUML elements":**

```plantuml
@startuml
!ENABLE_ALL_PLANT_ELEMENTS = 1
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml

Component(comp, "Copy component")

Component(config, "Config component", $plant="package")

ComponentDb(dbA, "DB A")
' alternative syntax for ComponentDb() with $plant="database"
Component(dbB, "DB B", $plant="database")

Rel_U(comp, config, "Configured by")
Rel_L(comp, dbA, "Reads from")
Rel_R(comp, dbB, "Writes to")

SHOW_LEGEND()
@enduml
```

![Sample with PlantUML elements](https://www.plantuml.com/plantuml/png/NP1FQy904CNl-HHZA5J16Wez5GGJ3UrXJSK_U0oRx6Y2oMxOdLJzzjsjDiJUPkVzPjwRdHdYcjgwyWPn4aOiJaF6qXKBasqQitWP9ziDJE7L6vGohrg1K10rvZq8D3zFZYKLRTOQrBcIX98ckQg3Kwdpmb0HpDzULXMNj5ko02zM5oXiCvshkb7IuOrpzhhtCBVL6FovQgwG_tNzqICY3-NHGRz53nl3K-Fifdx3ynC_uiFW8XkABBHpYmX2gpm3hmYrv5H-8vYh97w1WzBGdnZ1sPxOxHMSUCOD-hqy8ejkIwCkG0-q2TPOfRlxPV_2jne5P5TBEOZTeLlCDN9XuA1LVPVNdUmCzxeaD43AMMm-l_OfYp_YP34SUJEKmlxh3m00)

### List of supported PlantUML elements

| PlantUML element | Support  | Comment                                                                                                               |
| ---------------- | -------- | --------------------------------------------------------------------------------------------------------------------- |
| rectangle        | &#x2705; | already supported (works even without ENABLE_ALL_PLANT_ELEMENTS)                                                      |
| database         | &#x2705; | already supported (works even without ENABLE_ALL_PLANT_ELEMENTS)                                                      |
| queue            | &#x2705; | already supported (works even without ENABLE_ALL_PLANT_ELEMENTS)                                                      |
| node             | &#x274C; | **should not be used**, already defined for Node() (works even without ENABLE_ALL_PLANT_ELEMENTS)                     |
| person           | &#x274C; | **should not be used**, already defined for Person() (works even without ENABLE_ALL_PLANT_ELEMENTS)                   |
|                  |          |                                                                                                                       |
| actor            | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| agent            | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| artifact         | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| boundary         | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| card             | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| circle           | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| cloud            | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| collections      | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| control          | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| entity           | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| file             | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| folder           | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| frame            | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| hexagon          | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| interface        | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| package          | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| stack            | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| storage          | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| usecase          | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
| usecase/         | &#x2611; | requires ENABLE_ALL_PLANT_ELEMENTS                                                                                    |
|                  |          |                                                                                                                       |
| actor/           | &#x274C; | requires ENABLE_ALL_PLANT_ELEMENTS, not working (font color not changed to $bkColor) - and/or conflict with existing? |
| label            | &#x274C; | requires ENABLE_ALL_PLANT_ELEMENTS, not working (font color not changed to $bkColor)                                  |

If `ENABLE_ALL_PLANT_ELEMENTS` is not set, the diagrams displays the requested "PlantUML element"
but the style is not correct.
