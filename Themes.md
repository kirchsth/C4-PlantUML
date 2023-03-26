# Themes

Similar to PlantUML themes supports C4-PlantUML `C4_...` specific themes (based on existing PlantUML themes).

![](https://www.plantuml.com/plantuml/png/hLRHRzks4txtNt5r-qCTG8dnGzkN0G7gsDgQmauyosttCC2WfBD4b28ryXJ76FQ_xqXPLknqw83k9J6FlE_x-F5uudj7mb9JgS4BAh52cBxTD5eIvh2rfeAIg7O_ZSTMxAuAIMMJDWvjPZIXfglCLEElqcQbet8yVNkvL4BJfyLyZ8yydsC-3g1ky4BgJ3Kv_Z0UovloOY4rsglQwnua7-w_R9RnAhc_szn_Mizlx-BHnU0rh4NXm3LrRIo1Dk1gaQ43gO55WHOLmYWL3dCmRQXX1gkabhe0HsZHqBv65y6kb5a9kT6lgGFiq8JULyRYnHKmu-ts6BO85lzea77oZb9XWJgF3l-1U5EmOm_Q92Y50pAG8kIubHhpmIJFOuKLQkAzZ8QfoBvoud7_mmXURNamDShOwrVnF5x4T-lDp_VyPte_lr_nV5gqiyENRzwycqtU-HnNYXglOrcKb4WsDV7ZqGNFjChMBEowOuEie_jTeqy1vtE65rxT2bLG9jnUPnwQzzJ9cQnMV2wT3iK8_pYHq5xXzKou4lEvrApb1Ds3Z_yR2aFKKmn8aa8u-Wcv58KL5MoDXLjDQ3KIt0ZzrLT4idU4rM2mHEkC7cMD8rEXZM1w_3MSG1S6imrddd9sr9vo7HA52Z4GMMOQJMx8EbhepGq7Sc7te-p_Z7KkO7W1Vmu0eDSxsc6w4NNDYxzW2fEwLZ8J98qUSkYZU10H9BNruXUVfpusGoKVM4QGveZNPd2uUo1q7i97thJR-7B28a-PNIqOBk5fXPTBKQ1dxrYJpCgQ8fZeeb72-l3IcWUPemEXrBTPjetEl7IX9Es133iPZ7Jm88LFaHPulv1QitDedocgJ2eL7knOX46dQVeoWjz49TY9KosWP1LQdMjIXmHc-w-rkMVYMW6GuuFCy5pUB1tbWeHlD_uO3Z-zckJNEPoCoLXquBiYM2oa8nkE5AJcigp2xmZAS5T0D5H2PZ57JL8e5_coGkT0cO87IDdLCwCEzvgTahvYbxVVBfoPuMMsppjnxZiEULCOEDnMKRZhPvsBHVrrBFluaKPO2QasBWIOABvSy1ZQ1PvvNIB8G2eKB6HcZJDRWlWnAuKk4DfCXds2UT3MepActbfHuTcTxcttvTbLGSQ1RdzFpGUHceRw4eYELpa2ia8x4PpexH-iK3rf5_sb_UJGUUuFw_KouOMdwrmjlhkcA_eUhgNRtFbMdPg-HGIulW4Sa4Bmj20wmj1l8_Z8NzLn8EzFCqmT47e5FmQqkU7aNdP_MKv1LoXo5ruceL_jh2HqGCOJ7NXcDrE6F68-SUkio1A6TO2NFXemUY4dzNYkuJIlSLmVFNsoM2zRe7up9-bdLTdxr7_bk5ijvkTUzTCCtxvvvl4lyTsCtpfROmWjv5RiTFkjwHvEy705__C7BeqUNGJF_BEgd-NXvsvwy9vLDfNw6m00)

- [📄 C4-PlantUML](README.md#c4-plantuml)
- [📄 Layout Options](LayoutOptions.md#layout-options)
- [📄 Themes](#themes)
  - [Use theme](#use-theme)
  - [List of available C4-themes](#list-of-available-c4-themes)
  - [How to write custom theme](#how-to-write-custom-theme)
    - [Following variables could be set in theme definitions too](#following-variables-could-be-set-in-theme-definitions-too)
- samples
  - [📄 Core Diagrams](samples/C4CoreDiagrams.md#c4-model-diagrams)

## Use theme

WIP ...

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

C4_blue theme is the original theme and need no activation, but it could be used as starting point of another theme.

It can be activated with  
```plantuml
!theme C4_blue from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fO-npe9048HxdW8Uu6SRgh_243jCB3IM1ewL8-uTv7Okwjkx-WfMCyby-P9f5KD23b9Ky1oux9hhA9dBMrf3wO5D_udIyAZd1JwFMJcvDO8ZQhS6kY_9UOMdhlaxoX1nFlJ4JziddkYhrA9QefCyyS--pU0NdLYn4zaB1uxGYubwdesejy-Hrfhb6m00)

### C4_brown

It can be activated with  
```plantuml
!theme C4_brown from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyz3e9058HxJW47aDTGMM687IOM6ai3ovCbxW_PDnlqzZwzWjLCCb--P5h1a92zAofOzbnspNrCSGlb8qLVMc2LFL4QjdfUOFEOXPE90HnGc-ZfkIHZ1PQwPdTsGy3rr1E_T9zuefzJYce9nkM9__Qj2h_fmeA3SqV7dWFafgAUPoNgzVkarQRv0G00)


### C4_green

It can be activated with  
```plantuml
!theme C4_green from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fS-n3e903CRndQU01v0kJ4uOueQ9WyRHu54vujr1sk-YlhtLLt1ga_xpIzeg1a6EeQZWENBPDTT9c5DvboMM7bXrIoJ3ivvc-7pBokAM14wetHBfCOlp2azTipc68U5yw8bVTXzvf9-fHJKd5_B8VtkhnMywiM8NmZuOdg0NWtgUhAZNxoUjRJO_)

### C4_united

It can be activated with  
```plantuml
!theme C4_united from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyn3i8m34Ntdg8z0FNIYQceOYiI0uWHbSGq4KbQnJy2Re_X2aoszDz_qky5KqQ9eMhWE78zTDUIFDZMzxp4sW6hR8doz6nd3rTkHJYR9O4JMhD4UlXidC3Hq6sEOKeu7qRYb-QMBVsaKZK-cL0i_-rR5NxJYGMx4FQ1ezRaegAHPoNQzJkbrq_l1m00)


### C4_violet

It can be activated with  
```plantuml
!theme C4_violet from https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/themes
```

![](https://www.plantuml.com/plantuml/png/fOyxhi9034Nxh29Pm8kRLAyAYkY2H06YH676P4PuFXfx-EmUmnQeREcUUwGxiYn5Qg2c4uS1ssauttqYbFPQKcYTIEP_WB8y-jMBgvVAM4oAWb5wamBSV36EnS4q_ErfYNBSpO1FpIrQ-4gvwNmqL2t-xCiAl-20B1kYBM7G6fzKDEEgH9y_KqRzzBu1)

## How to write custom theme

WIP ...

The sample theme C4_FirstTest [puml-theme-C4_FirstTest.puml](themes/puml-theme-C4_FirstTest.puml)  is stored in the themes folder

### Following variables could be set in theme definitions too

``` plantuml
!$ELEMENT_FONT_COLOR ?= "#FFFFFF"

!$ARROW_COLOR ?= "#666666"
!$ARROW_FONT_COLOR ?= $ARROW_COLOR
!$ARROW_FONT_SIZE ?= 12

!$STEREOTYPE_FONT_SIZE ?= 12
!$TECHN_FONT_SIZE ?= 12

!$BOUNDARY_COLOR ?= "#444444"
!$BOUNDARY_BG_COLOR ?= "transparent"
!$BOUNDARY_BORDER_STYLE ?= "dashed"

!$PERSON_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$PERSON_BG_COLOR ?= "#08427B"
!$PERSON_BORDER_COLOR ?= "#073B6F"
!$EXTERNAL_PERSON_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_PERSON_BG_COLOR ?= "#686868"
!$EXTERNAL_PERSON_BORDER_COLOR ?= "#8A8A8A"

!$SYSTEM_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$SYSTEM_BG_COLOR ?= "#1168BD"
!$SYSTEM_BORDER_COLOR ?= "#3C7FC0"
!$EXTERNAL_SYSTEM_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_SYSTEM_BG_COLOR ?= "#999999"
!$EXTERNAL_SYSTEM_BORDER_COLOR ?= "#8A8A8A"

!$CONTAINER_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$CONTAINER_BG_COLOR ?= "#438DD5"
!$CONTAINER_BORDER_COLOR ?= "#3C7FC0"
!$EXTERNAL_CONTAINER_FONT_COLOR ?= $ELEMENT_FONT_COLOR
!$EXTERNAL_CONTAINER_BG_COLOR ?= "#B3B3B3"
!$EXTERNAL_CONTAINER_BORDER_COLOR ?= "#A6A6A6"

!$COMPONENT_FONT_COLOR ?= "#000000"
!$COMPONENT_BG_COLOR ?= "#85BBF0"
!$COMPONENT_BORDER_COLOR ?= "#78A8D8"
!$EXTERNAL_COMPONENT_FONT_COLOR ?= $COMPONENT_FONT_COLOR
!$EXTERNAL_COMPONENT_BG_COLOR ?= "#CCCCCC"
!$EXTERNAL_COMPONENT_BORDER_COLOR ?= "#BFBFBF"

!$NODE_FONT_COLOR ?= "#000000"
!$NODE_BG_COLOR ?= "#FFFFFF"
!$NODE_BORDER_COLOR ?= "#A2A2A2"

!$LEGEND_TITLE_COLOR ?= "#000000"
!$LEGEND_FONT_COLOR ?= "#FFFFFF"
!$LEGEND_BG_COLOR ?= "transparent"
!$LEGEND_BORDER_COLOR ?= "transparent"
!$LEGEND_DARK_COLOR ?= "#66622E"
!$LEGEND_LIGHT_COLOR ?= "#khaki"
!$LEGEND_DETAILS_SMALL_SIZE ?= 10
!$LEGEND_DETAILS_NORMAL_SIZE ?= 14

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
'$LEGEND_DASHED_TRANSPARENT_BOUNDARY ?= "dashed, transparent"
!$LEGEND_DASHED_TRANSPARENT_BOUNDARY ?= "dashed"

!$SKETCH_BG_COLOR ?= "#EEEBDC"
!$SKETCH_FONT_COLOR ?= ""
!$SKETCH_WARNING_COLOR ?= "red"
!$SKETCH_FONT_NAME ?= "Comic Sans MS"

!$SKETCH_FOOTER_WARNING ?= "Warning:"
!$SKETCH_FOOTER_TEXT ?= "Created for discussion, needs to be validated"

!$ROUNDED_BOX_SIZE ?= 25
!$EIGHT_SIDED_SIZE ?= 18
```

