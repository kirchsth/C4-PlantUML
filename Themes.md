# Themes

![Theme sample](https://www.plantuml.com/plantuml/png/hLRHRzks4txtNt5r-qCTG8dnGzkN0G7gsDgQmauyosttCC2WfBD4b28ryXJ76FQ_xqXPLknqw83k9J6FlE_x-F5uudj7mb9JgS4BAh52cBxTD5eIvh2rfeAIg7O_ZSTMxAuAIMMJDWvjPZIXfglCLEElqcQbet8yVNkvL4BJfyLyZ8yydsC-3g1ky4BgJ3Kv_Z0UovloOY4rsglQwnua7-w_R9RnAhc_szn_Mizlx-BHnU0rh4NXm3LrRIo1Dk1gaQ43gO55WHOLmYWL3dCmRQXX1gkabhe0HsZHqBv65y6kb5a9kT6lgGFiq8JULyRYnHKmu-ts6BO85lzea77oZb9XWJgF3l-1U5EmOm_Q92Y50pAG8kIubHhpmIJFOuKLQkAzZ8QfoBvoud7_mmXURNamDShOwrVnF5x4T-lDp_VyPte_lr_nV5gqiyENRzwycqtU-HnNYXglOrcKb4WsDV7ZqGNFjChMBEowOuEie_jTeqy1vtE65rxT2bLG9jnUPnwQzzJ9cQnMV2wT3iK8_pYHq5xXzKou4lEvrApb1Ds3Z_yR2aFKKmn8aa8u-Wcv58KL5MoDXLjDQ3KIt0ZzrLT4idU4rM2mHEkC7cMD8rEXZM1w_3MSG1S6imrddd9sr9vo7HA52Z4GMMOQJMx8EbhepGq7Sc7te-p_Z7KkO7W1Vmu0eDSxsc6w4NNDYxzW2fEwLZ8J98qUSkYZU10H9BNruXUVfpusGoKVM4QGveZNPd2uUo1q7i97thJR-7B28a-PNIqOBk5fXPTBKQ1dxrYJpCgQ8fZeeb72-l3IcWUPemEXrBTPjetEl7IX9Es133iPZ7Jm88LFaHPulv1QitDedocgJ2eL7knOX46dQVeoWjz49TY9KosWP1LQdMjIXmHc-w-rkMVYMW6GuuFCy5pUB1tbWeHlD_uO3Z-zckJNEPoCoLXquBiYM2oa8nkE5AJcigp2xmZAS5T0D5H2PZ57JL8e5_coGkT0cO87IDdLCwCEzvgTahvYbxVVBfoPuMMsppjnxZiEULCOEDnMKRZhPvsBHVrrBFluaKPO2QasBWIOABvSy1ZQ1PvvNIB8G2eKB6HcZJDRWlWnAuKk4DfCXds2UT3MepActbfHuTcTxcttvTbLGSQ1RdzFpGUHceRw4eYELpa2ia8x4PpexH-iK3rf5_sb_UJGUUuFw_KouOMdwrmjlhkcA_eUhgNRtFbMdPg-HGIulW4Sa4Bmj20wmj1l8_Z8NzLn8EzFCqmT47e5FmQqkU7aNdP_MKv1LoXo5ruceL_jh2HqGCOJ7NXcDrE6F68-SUkio1A6TO2NFXemUY4dzNYkuJIlSLmVFNsoM2zRe7up9-bdLTdxr7_bk5ijvkTUzTCCtxvvvl4lyTsCtpfROmWjv5RiTFkjwHvEy705__C7BeqUNGJF_BEgd-NXvsvwy9vLDfNw6m00 "Theme sample")

- [📄 C4-PlantUML](README.md#c4-plantuml)
- [📄 Layout Options](LayoutOptions.md#layout-options)
- [📄 Themes](#themes)
  - [Use theme](#use-theme)
  - [List of available C4-themes](#list-of-available-c4-themes)
    - [C4_blue](#c4_blue)
    - [C4_brown](#c4_brown)
    - [C4_green](#c4_green)
    - [C4_sandstone](#c4_sandstone)
    - [C4_superhero](#c4_superhero)
    - [C4_united](#c4_united)
    - [C4_violet](#c4_violet)
  - [Write custom themes](#write-custom-themes)
    - [Following variables could be set in a theme, additional to the skinparams and styles](#following-variables-could-be-set-in-a-theme-additional-to-the-skinparams-and-styles)
    - [(C4 styled) Sequence diagram and themes](#c4-styled-sequence-diagram-and-themes)
- samples
  - [📄 C4 Model Diagrams](samples/C4CoreDiagrams.md#c4-model-diagrams)

## Use theme

Similar to PlantUML themes supports C4-PlantUML `C4_...` specific themes too (sometimes based on existing PlantUML themes).

Additional to the standard themes with skinparam and style definitions requires C4-PlantUML corresponding variable definitions.
Therefore we started with the convention that all C4-PlantUML compatible themes start with `C4_...` in the name
(e.g. theme [`C4_united`](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_united.puml)
bases on the [`united`](https://raw.githubusercontent.com/plantuml/plantuml/master/themes/puml-theme-united.puml) theme
and contains all additional required C4-PlantUML settings that it can be directly used in all C4-PlantUML diagrams).

E.g. in order to invoke theme `C4_united` from a remote repository, you have to use the following directive:

```plantuml
!theme C4_united from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

In order to invoke a local theme `C4_foo`, you have to use the following directive:

```plantuml
!theme C4_foo from /path/to/themes/folder
```

(It is planed that included themes can be loaded via `!theme C4_united from <C4/themes>` too, but this requires a PlantUML extension with is missing atm)

```plantuml
@startuml

!theme C4_united from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes

!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(admin, "Administrator")
System_Boundary(c1, "Sample System") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")

SHOW_FLOATING_LEGEND()
@enduml
```

![Theme sample](https://www.plantuml.com/plantuml/png/fP7BpjCm48NtVWh_OPDA9L5HLwmQGccHUeb8IfUHcmp4mXVBdYXKY7TdJ4lB_izc59zlpfonLm65nr4hze83QE3biXsDHEZvDsyr7n1TU9_dNapPTud3U1a3-CuQ18DPPtN-G_fk23ZavV9jfOJ1qtwNmq_IU-ZplwQ1iHTfEZNsy6f3obSIBAG1dxaOd5NWWpMfwBKqSvuKiSg0Ng3roOpLru2WsmzsDBtmrxHR45GBxHJmcvRC-2_6wNiufnDSMk4SaMUuyC8v9Jk1qfg4ZietSrxKLNPODzJYWR_B5dp_jOnQePIT0ezB1OwMqqPE4A97XJAER2Q929wZrA1eLg28l-yXKxo9v7F7I6HVGFrRxXdh5AYJwhPfgfge23tKfyq6CD0ln18VzFyMLc-Fv_RJxbWqdm-RThVUh0yVqnbRWUdfOly0 "Theme sample")

## List of available C4-themes

### C4_blue

C4_blue theme is the original theme and need no activation.

Theme [C4_blue](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_blue.puml) can be activated with

```plantuml
!theme C4_blue from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fO-npe9048HxdW8Uu6SRgh_243jCB3IM1ewL8-uTv7Okwjkx-WfMCyby-P9f5KD23b9Ky1oux9hhA9dBMrf3wO5D_udIyAZd1JwFMJcvDO8ZQhS6kY_9UOMdhlaxoX1nFlJ4JziddkYhrA9QefCyyS--pU0NdLYn4zaB1uxGYubwdesejy-Hrfhb6m00)

### C4_brown

Theme [C4_brown](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_brown.puml) can be activated with

```plantuml
!theme C4_brown from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyz3e9058HxJW47aDTGMM687IOM6ai3ovCbxW_PDnlqzZwzWjLCCb--P5h1a92zAofOzbnspNrCSGlb8qLVMc2LFL4QjdfUOFEOXPE90HnGc-ZfkIHZ1PQwPdTsGy3rr1E_T9zuefzJYce9nkM9__Qj2h_fmeA3SqV7dWFafgAUPoNgzVkarQRv0G00)


### C4_green

Theme [C4_green](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_green.puml) can be activated with

```plantuml
!theme C4_green from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fS-n3e903CRndQU01v0kJ4uOueQ9WyRHu54vujr1sk-YlhtLLt1ga_xpIzeg1a6EeQZWENBPDTT9c5DvboMM7bXrIoJ3ivvc-7pBokAM14wetHBfCOlp2azTipc68U5yw8bVTXzvf9-fHJKd5_B8VtkhnMywiM8NmZuOdg0NWtgUhAZNxoUjRJO_)

### C4_sandstone

Theme [C4_sandstone](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_sandstone.puml) can be activated with

```plantuml
!theme C4_sandstone from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fS_12i8m383X-vvYUm2NoqwU9iFR10-AHwbjN8TjMfeKzUsDleAd1FBpGKOMKwJ6q7JYCM8x3LSsv5WIONilARPU9FCMe9XdlwpYwwqo5fj8aAItAS9ZBTQpU9Y6pJ4OalDX1dpftQ63dyjDjv8DrU7VNjRu3ITasOMm3ugJy4MX6HSj-lpzPjHDvmS0)

### C4_superhero

Theme [C4_superhero](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_superhero.puml) can be activated with

```plantuml
!theme C4_superhero from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fSyz2i9G3C3nlQTe3s2pT7Ag5BSA3egZrDVOLypx8Cb3lRtHApWba3y_I2ywiPP0LQCU0zP3TvMIaJrogk-SGkrLism1U7gsowg-t8eWknGLexOk1NYixBoeXw7R76cAUZwCW2-xppZ3pvMgMQEZCkFVNhRu3ISKtH7joV2eSZ5enCMADd-_wMsp-G40)

### C4_united

Theme [C4_united](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_united.puml) can be activated with

```plantuml
!theme C4_united from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyn3i8m34Ntdg8z0FNIYQceOYiI0uWHbSGq4KbQnJy2Re_X2aoszDz_qky5KqQ9eMhWE78zTDUIFDZMzxp4sW6hR8doz6nd3rTkHJYR9O4JMhD4UlXidC3Hq6sEOKeu7qRYb-QMBVsaKZK-cL0i_-rR5NxJYGMx4FQ1ezRaegAHPoNQzJkbrq_l1m00)

### C4_violet

Theme [C4_violet](https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes/puml-theme-C4_violet.puml) can be activated with

```plantuml
!theme C4_violet from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyxhi9034Nxh29Pm8kRLAyAYkY2H06YH676P4PuFXfx-EmUmnQeREcUUwGxiYn5Qg2c4uS1ssauttqYbFPQKcYTIEP_WB8y-jMBgvVAM4oAWb5wamBSV36EnS4q_ErfYNBSpO1FpIrQ-4gvwNmqL2t-xCiAl-20B1kYBM7G6fzKDEEgH9y_KqRzzBu1)

## Write custom themes

You can create your own theme on your local file system. You can duplicate any existing theme to create your own one.

By default, a theme file is named `puml-theme-C4_foo.puml` where `C4_foo` is the name of the theme.

In contrast to the normal themes (with skinparams and/or styles) the corresponding color,... variables have to overwritten too (e.g. that the legend is updated... details see below).

If you have any interesting theme, you can also propose a pull request so that we integrate this theme into the C4-PlantUML standard library.

### Following variables could be set in a theme, additional to the skinparams and styles

- stereotype and technology font size

```plantuml
!$STEREOTYPE_FONT_SIZE ?= 12
!$TECHN_FONT_SIZE ?= 12
```

- default text color of all elements

```plantuml
!$ELEMENT_FONT_COLOR ?= "#FFFFFF"
```

- arrow related colors and text size

```plantuml
!$ARROW_COLOR ?= "#666666"
!$ARROW_FONT_COLOR ?= $ARROW_COLOR
!$ARROW_FONT_SIZE ?= 12
```

- (default) boundary related colors and style

```plantuml
!$BOUNDARY_COLOR ?= "#444444"
!$BOUNDARY_BG_COLOR ?= "transparent"
!$BOUNDARY_BORDER_STYLE ?= "dashed"
```

- person related colors

```plantuml
!$PERSON_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$PERSON_BG_COLOR ?= "#08427B"
!$PERSON_BORDER_COLOR ?= "#073B6F"
```

- external person related colors

```plantuml
!$EXTERNAL_PERSON_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_PERSON_BG_COLOR ?= "#686868"
!$EXTERNAL_PERSON_BORDER_COLOR ?= "#8A8A8A"
```

- system related colors

```plantuml
!$SYSTEM_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$SYSTEM_BG_COLOR ?= "#1168BD"
!$SYSTEM_BORDER_COLOR ?= "#3C7FC0"
```

- external system related colors

```plantuml
!$EXTERNAL_SYSTEM_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_SYSTEM_BG_COLOR ?= "#999999"
!$EXTERNAL_SYSTEM_BORDER_COLOR ?= "#8A8A8A"
```

- system boundary related colors and style

```plantuml
!$SYSTEM_BOUNDARY_COLOR ?= $BOUNDARY_COLOR
!$SYSTEM_BOUNDARY_BG_COLOR ?= $BOUNDARY_BG_COLOR
!$SYSTEM_BOUNDARY_BORDER_STYLE ?= $BOUNDARY_BORDER_STYLE
```

- enterprise boundary related colors and style

```plantuml
!$ENTERPRISE_BOUNDARY_COLOR ?= $BOUNDARY_COLOR
!$ENTERPRISE_BOUNDARY_BG_COLOR ?= $BOUNDARY_BG_COLOR
!$ENTERPRISE_BOUNDARY_BORDER_STYLE ?= $BOUNDARY_BORDER_STYLE
```

- container related colors

```plantuml
!$CONTAINER_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$CONTAINER_BG_COLOR ?= "#438DD5"
!$CONTAINER_BORDER_COLOR ?= "#3C7FC0"
```

- external container related colors

```plantuml
!$EXTERNAL_CONTAINER_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_CONTAINER_BG_COLOR ?= "#B3B3B3"
!$EXTERNAL_CONTAINER_BORDER_COLOR ?= "#A6A6A6"
```

- container boundary related colors and style

```plantuml
!$CONTAINER_BOUNDARY_COLOR ?= $BOUNDARY_COLOR
!$CONTAINER_BOUNDARY_BG_COLOR ?= $BOUNDARY_BG_COLOR
!$CONTAINER_BOUNDARY_BORDER_STYLE ?= $BOUNDARY_BORDER_STYLE
```

- component related colors

```plantuml
!$COMPONENT_FONT_COLOR ?= "#000000"
!$COMPONENT_BG_COLOR ?= "#85BBF0"
!$COMPONENT_BORDER_COLOR ?= "#78A8D8"
```

- external component related colors

```plantuml
!$EXTERNAL_COMPONENT_FONT_COLOR ?= $COMPONENT_FONT_COLOR
!$EXTERNAL_COMPONENT_BG_COLOR ?= "#CCCCCC"
!$EXTERNAL_COMPONENT_BORDER_COLOR ?= "#BFBFBF"
```

- node related colors

```plantuml
!$NODE_FONT_COLOR ?= "#000000"
!$NODE_BG_COLOR ?= "#FFFFFF"
!$NODE_BORDER_COLOR ?= "#A2A2A2"
```

- legend colors and sizes

```plantuml
!$LEGEND_TITLE_COLOR ?= "#000000"
!$LEGEND_FONT_COLOR ?= "#FFFFFF"
!$LEGEND_BG_COLOR ?= "transparent"
!$LEGEND_BORDER_COLOR ?= "transparent"
!$LEGEND_DARK_COLOR ?= "#66622E"
!$LEGEND_LIGHT_COLOR ?= "#khaki"

!$LEGEND_DETAILS_SMALL_SIZE ?= 10
!$LEGEND_DETAILS_NORMAL_SIZE ?= 14
```

- legend related texts

```plantuml
!$LEGEND_SHADOW_TEXT ?= "shadow"
!$LEGEND_NO_SHADOW_TEXT ?= "no shadow"
!$LEGEND_NO_FONT_BG_TEXT ?= "last text and back color"
!$LEGEND_NO_FONT_TEXT ?= "last text color"
!$LEGEND_NO_BG_TEXT ?= "last back color"
!$LEGEND_NO_LINE_TEXT ?= "last line color"
!$LEGEND_ROUNDED_BOX ?= "rounded box"
!$LEGEND_EIGHT_SIDED ?= "eight sided"
!$LEGEND_DOTTED_LINE ?= "dotted"
!$LEGEND_DASHED_LINE ?= "dashed"
!$LEGEND_BOLD_LINE ?= "bold"
!$LEGEND_BOUNDARY ?= "boundary"
!$LEGEND_DASHED_BOUNDARY ?= "dashed"
' transparent is ignored, produces smaller legends
' !$LEGEND_DASHED_TRANSPARENT_BOUNDARY ?= "dashed, transparent"
!$LEGEND_DASHED_TRANSPARENT_BOUNDARY ?= "dashed"
```

- sketch related colors, font and texts

```plantuml
!$SKETCH_BG_COLOR ?= "#EEEBDC"
!$SKETCH_FONT_COLOR ?= ""
!$SKETCH_WARNING_COLOR ?= "red"

!$SKETCH_FONT_NAME ?= "Comic Sans MS"

!$SKETCH_FOOTER_WARNING ?= "Warning:"
!$SKETCH_FOOTER_TEXT ?= "Created for discussion, needs to be validated"
```

- size of rectangle shape corner markers

```plantuml
!$ROUNDED_BOX_SIZE ?= 25
!$EIGHT_SIDED_SIZE ?= 18
```

### (C4 styled) Sequence diagram and themes

All sequence diagram specific renderings (like sequence-lifeline-color...) can be directly defined via skinparams and styles.
The advantage is that no separate variable definitions are required anymore.
(But the disadvantage is that all themes have to define there own skinparams and styles.)

A theme could contain e.g. following definitions, skinparams and styles

```plantuml
' $BOUNDARY_BG_COLOR... have to be defined in theme itself that it can be used in styles,...
' (no default values which are defined in C4.puml) 
' If skinparams and styles are defined with concrete values no variables are required 
!$BOUNDARY_BG_COLOR ?= "transparent"
!$BOUNDARY_COLOR ?= "#444444"
!$ARROW_COLOR ?= "#666666"

' replace transparent with concrete background that it can be used as font color too
!if ($BOUNDARY_BG_COLOR == "transparent")
  !$SEQUENCE_BG_COLOR = white
!else
  !$SEQUENCE_BG_COLOR = $BOUNDARY_BG_COLOR
!endif

' "C4 styled" default is no foot boxes
hide footbox
' "C4 styled" default is that lifeline is arrow color
skinparam SequenceLifelineBorderColor $ARROW_COLOR

skinparam SequenceGroupBodyBackgroundColor $SEQUENCE_BG_COLOR
skinparam SequenceGroupFontColor $BOUNDARY_COLOR
skinparam SequenceGroupBackgroundColor $BOUNDARY_COLOR
skinparam SequenceGroupHeaderFontColor $SEQUENCE_BG_COLOR
skinparam SequenceGroupBorderColor $BOUNDARY_COLOR

skinparam SequenceReferenceBackgroundColor $SEQUENCE_BG_COLOR
skinparam SequenceReferenceFontColor $BOUNDARY_COLOR
skinparam SequenceReferenceHeaderBackgroundColor $BOUNDARY_COLOR
' VIA STYLE
' skinparam SequenceReferenceHeaderFontColor $SEQUENCE_BG_COLOR
<style>
referenceHeader {
  fontcolor $SEQUENCE_BG_COLOR
}
</style>
skinparam SequenceReferenceBorderColor $BOUNDARY_COLOR

skinparam SequenceDividerBackgroundColor $SEQUENCE_BG_COLOR
skinparam SequenceDividerFontColor $BOUNDARY_COLOR
skinparam SequenceDividerBorderColor $BOUNDARY_COLOR

' VIA STYLE
' skinparam SequenceDelayFontColor green
<style>
sequenceDiagram {
  delay {
    FontColor $BOUNDARY_COLOR
  }
}
</style>
```

Following sample could be used as starting point for custom themes with sequence diagram support:

[![](https://www.plantuml.com/plantuml/svg/fLPjRzis4FxENt7sMYG1MZi3idqeagv-KLu0DyaKfqC_6RHqieZGf4UUd6H3__jEL2qxbPFK684s4ddFStVF7Ntwv4awAkPQYDQRMu_Z7ES89z0U74rc3j6qXTY3n9ebEW95SAye1vccYfGrKlFHV2vD2beP1EbcnHmDmVjX78rwuuilqUJYSZ2w7KOdxKwtqsa3MIWyWhQ9rFfHj5G6RvVIAJdLEC47vSdljty4jmy4m1wqA4J7ePqgvscCdY1pTWvlPqYJccKfTO7RIBe1xmMicDOP1veomfLD2xN7PorpeeN_qEqwUT-PiIB5b9DoB1EXeGvhqhrJBiazvTt1qVjhBGtTVXvryO7FKqpNJaogibBXuyQ2wruyXgjJ69z7doCeZTxqhsulXxtuwwH_DXbSZQxYJgS3kLnYAUiK8SLC6Kn16QZ2LkHHP_mYG_4IQKgpmbSsdXur-dTCmkJxnfPuMMY2eA27-rmbEKYtISpgTnRSBmV0c8iC_9qo2-dat8CqwNVA9vZGCInDuf1mHStELlMgh1t-NIZ7vgBLJ1F-u8ua9urdLsYelMcqjlZbAApoj1V7Ltzj7lqULkXcXmij4uGDmX-2dChaRkPiOTAjqaaFcJN4zjew86j36-zlYVlaQToXZrjlRg8_RwFBGRHXLsfDM7VTTfkcWtK7bJUsKZzjrtLKGUZCMeAfVK0lSfLYUEVNvp4XPwqo39TQbGLozhvALzG5Xnik6Pe4Hzyj-zQbw0P1bCq2Y2sOCrPtqRVfOx-MkW8s4tyEVMeD1SnQbvS1QrSxmSvHSbh1suuHhWLfEjk2YJ53Lpxif4a3lOikDQXAyZM5zk3BHGzknbz74J-_HlUoPiUXyJuAznG3_me8jojv3lXD77Shx8iQxgRzK2qLs--k_1gxW-uho8j1lYRs4BLyN3iDqxfMrTUEv8n1GTMq18GdWEU31VYsAJ6x_jXOZTcqmnXlAPFe8iMV7jeyxbSfXybJ_qZMJFzp6ZSyrB-gr-YyDVizhH9y1-tmjtsmskxRAM_o_xmbP49gAGc1tuM8KQzGbLMle1mDgKIIiWRYqfsd0DG4laWIz3uhD2Gov0PGKWHiu6bIz1Yo84oPezG3l9qZS9EaO3F8fDA5guYqjGluzV3m44XLNp_LQiGulBo17X5VWL0e05P1bF_AEmfsYGxMzl01b56q9TKSjRRCKAE2903ZNFdL6BM6DppoeTJXqz6NZe0HGl3Cl61c9RNwfqhrv6GNHLyJBaQ_iCPp8OEl61T8wWK_nZBSWVnfVxA1QFWjlzj-Wxao1Q47BOdDUM-B-qHgxM6f92noQm9Ot9ppQ1r5Pz7bSFz0V6Bbk6d_0m00)](https://www.plantuml.com/plantuml/uml/fLPjRzis4FxENt7sMYG1MZi3idqeagv-KLu0DyaKfqC_6RHqieZGf4UUd6H3__jEL2qxbPFK684s4ddFStVF7Ntwv4awAkPQYDQRMu_Z7ES89z0U74rc3j6qXTY3n9ebEW95SAye1vccYfGrKlFHV2vD2beP1EbcnHmDmVjX78rwuuilqUJYSZ2w7KOdxKwtqsa3MIWyWhQ9rFfHj5G6RvVIAJdLEC47vSdljty4jmy4m1wqA4J7ePqgvscCdY1pTWvlPqYJccKfTO7RIBe1xmMicDOP1veomfLD2xN7PorpeeN_qEqwUT-PiIB5b9DoB1EXeGvhqhrJBiazvTt1qVjhBGtTVXvryO7FKqpNJaogibBXuyQ2wruyXgjJ69z7doCeZTxqhsulXxtuwwH_DXbSZQxYJgS3kLnYAUiK8SLC6Kn16QZ2LkHHP_mYG_4IQKgpmbSsdXur-dTCmkJxnfPuMMY2eA27-rmbEKYtISpgTnRSBmV0c8iC_9qo2-dat8CqwNVA9vZGCInDuf1mHStELlMgh1t-NIZ7vgBLJ1F-u8ua9urdLsYelMcqjlZbAApoj1V7Ltzj7lqULkXcXmij4uGDmX-2dChaRkPiOTAjqaaFcJN4zjew86j36-zlYVlaQToXZrjlRg8_RwFBGRHXLsfDM7VTTfkcWtK7bJUsKZzjrtLKGUZCMeAfVK0lSfLYUEVNvp4XPwqo39TQbGLozhvALzG5Xnik6Pe4Hzyj-zQbw0P1bCq2Y2sOCrPtqRVfOx-MkW8s4tyEVMeD1SnQbvS1QrSxmSvHSbh1suuHhWLfEjk2YJ53Lpxif4a3lOikDQXAyZM5zk3BHGzknbz74J-_HlUoPiUXyJuAznG3_me8jojv3lXD77Shx8iQxgRzK2qLs--k_1gxW-uho8j1lYRs4BLyN3iDqxfMrTUEv8n1GTMq18GdWEU31VYsAJ6x_jXOZTcqmnXlAPFe8iMV7jeyxbSfXybJ_qZMJFzp6ZSyrB-gr-YyDVizhH9y1-tmjtsmskxRAM_o_xmbP49gAGc1tuM8KQzGbLMle1mDgKIIiWRYqfsd0DG4laWIz3uhD2Gov0PGKWHiu6bIz1Yo84oPezG3l9qZS9EaO3F8fDA5guYqjGluzV3m44XLNp_LQiGulBo17X5VWL0e05P1bF_AEmfsYGxMzl01b56q9TKSjRRCKAE2903ZNFdL6BM6DppoeTJXqz6NZe0HGl3Cl61c9RNwfqhrv6GNHLyJBaQ_iCPp8OEl61T8wWK_nZBSWVnfVxA1QFWjlzj-Wxao1Q47BOdDUM-B-qHgxM6f92noQm9Ot9ppQ1r5Pz7bSFz0V6Bbk6d_0m00)
