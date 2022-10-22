# Extended C4-PlantUML

This branch is basically https://github.com/plantuml-stdlib/C4-PlantUML/tree/master
extended with my open PRs.

**Old master branch**

The [old master branch](https://github.com/kirchsth/C4-PlantUML/blob/master/README.md) is still working. But it will not be updated anymore.

# C4-PlantUML

![Container diagram for Internet Banking System](https://www.plantuml.com/plantuml/png/hLPlZzh64txlJp4XYM8a7-Yd_FAcqadXm6qkWZkAkQJlq7ezsAkiTztTDHog-jqxQsmCNAfKQj_SiJCxp_Fi_1duQ1qphYvby0wuLZiq3eI3lN05i2mJJcZ59BdAagaCf508pEHrYSh1pMmLpoVh-o_nvlvXEd-QnRU3qG2SXjeYICsPb8VWbTZ2snqpWgKID_WihBFXu3foC0m0NWd5PPqXZCQZqNZw_yrKAyU8qumgh_4LIeldzmhdAllJU6pOVfIJvZebPiCfYlIDIFNucp2yiAuWj9kbPCezBUPZV2P_XjbtALGcja6GV7hykbd6g-JnOVFuj9xVFyJXa9AqPha5MrULDWwK1binZXQ40bSWA5OYX2cpc84-cceYCfGteNAm3WrgTwZGHh0l12yWq-gTEm6sQ4mTIcrmE09YlD-Up0R1uEyr4axMKKhCINBK_WU7pstvcY0ecFK5IH4otD8pis2IPR54Nq1wIpX86Vz6WQSq329uiwN3L4jjRj_4ytWHFwmtFp_Id-dZ_755_ZG_UWUltx__C9jyy36sO1NUnY8lN28ejua_XqFo79MjITXjnmQyeuCGVGXO7pCS3Bsy5Sf66hC7nJqsFQhJCrcjg32T4D-FV-j8t47YxOpP0hEvK2Jc0js3Z_yR2krSJn4uuIJ2AQ6G2PORLi9M6xXN3er21tTCVVCjaHoimp88bcYiLY6lhTCbcWYcfq-32NHcqDkcw2b5HySoLqqWauqD6EUwLiuEICSHUdD7XeoPGyZ_HrZN0WP3-2C0W5vlkCTqmwgABd_552PL9GLdVX4CoFIPxLW4IMMy-CMNgRVDK8eToMYaMKTtERGp24nbZVd4ctOFNqv8v2KpjIp19UIMUBDaENhsZZNXHbGkWedAQycCDo-DtedCJuQKtsVPreeVTvXm1py8l6uIQM4dc0yH1kYza1gzjsXUA2frAYIswLZumqdJz7K4lx6IKIOkjO0KfV0JQklKegEQ_MDjzeMuem38S2SuNikRfM767FFxnfUX_UZL9B_EuUBij25jVZk2mLnOPvgIWb3KbcNpEOAYcHLWDVKLDvYXSe996_csGcj1wfmEwFZeHQBQmQPC2T-no_llDyvCqpNJnvrdxaSPyaaXu6PQMMvlNwmk4lNdgUtZPnTYoOJSsCP0HF7DWixjo7dcDPL5DAHCma9mewtUEeYVUS5KZd2C9DWpp5PRZqgOQalpZLSptQVTjsVN1PmCtVlEamyirRNhMo0wZN84pZ1bMPE9Flt12kNPkkY7zicYzToVrkjbGXSlxz68_V1Es_GzN4ktUV2xEjNzYcZW-WNG8ZN6ouRe29jz6y5d-beTD-HzDHjNYz0h-7T0cpiAxcNtmt89kaAMMTWQNJRxQc-4GmjEUwAMPtOt9SWJvbcshfei8LWBUEEj3KOlvB8VBpHSnzMM-gEdJnRh9G5TrE0Y_BehJtdgl-LeMotcrxdgtGH__D4pZt-97sRXCDXgxT10PjXU7RzhkXzGi1l1MrzmwiXmsEIi_tdblNJyqhc3ZwIoBkLV "Container diagram for Internet Banking System")

C4-PlantUML combines the benefits of [PlantUML](https://plantuml.com/) and the [C4 model](https://c4model.com/) for providing a simple way of describing and communicate software architectures – especially during up-front design sessions – with an intuitive language using open source and platform independent tools.

C4-PlantUML includes macros, stereotypes, and other goodies (like VSCode Snippets) for creating C4 diagrams with PlantUML.

  - [Getting Started](#getting-started)
  - [Supported Diagram Types](#supported-diagram-types)
  - [Relationship Types](#relationship-types)
  - [Layout (arrange) elements (without relationships)](#layout-arrange-elements-without-relationships)
  - [Global Layout Options](#global-layout-options)
  - [Sprites and other images](#sprites-and-other-images)
  - [Custom tags/stereotypes support and skinparam updates](#custom-tagsstereotypes-support-and-skinparam-updates)
    - [Element specific tag definitions](#element-specific-tag-definitions)
    - [Boundary specific tag definitions](#boundary-specific-tag-definitions)
    - [Comments](#comments)
    - [Sample with different tag combinations](#sample-with-different-tag-combinations)
    - [Sample with tag dependent sprites and custom legend text](#sample-with-tag-dependent-sprites-and-custom-legend-text)
    - [Sample with different boundary tag combinations](#sample-with-different-boundary-tag-combinations)
    - [Custom schema definition](#custom-schema-definition)
  - [Element and Relationship properties](#element-and-relationship-properties)
  - [Version information](#version-information)
  - [Snippets for Visual Studio Code](#snippets-for-visual-studio-code)
  - [Live Templates for IntelliJ](#live-templates-for-intellij)
    - [Prerequisites](#prerequisites)
    - [Install](#install)
    - [Usage](#usage)
  - [Advanced Samples](#advanced-samples)
    - [techtribes.js](#techtribes.js)
    - [Message Bus and Microservices](#message-bus-and-microservices)
  - [Background](#background)
  - [License](#license)

## Getting Started

At the top of your C4 PlantUML `.puml` file, you need to include the `C4_Context.puml`, `C4_Container.puml` or `C4_Component.puml` file found in the `root` of this repo.

To be independent of any internet connectivity, you can also download the files found in the `root` and activate the local conversion with additional command line argument `-DRELATIVE_INCLUDE="."` (that the local files are included)

```plantuml
java -jar plantuml.jar -DRELATIVE_INCLUDE="."  ...
```

If you want to use the always up-to-date version in this repo, use the following:

```plantuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
```

Now let's create a C4 Container diagram:

\(If you don't want run PlantUML locally you can use e.g. the [PlantUML Web Server](https://www.plantuml.com/plantuml/uml/ZOxDIWGn48JlUOeufn5qSjcJfvNHsugBFsV99iqcsEc4T0VTjpSCE2AYUAeAgVwgjYosIakevytBBK824bPdaHms3pg85BuofjgtwHWbj4DZg2wJzDpaSZAliRh04ioykToZ9Nc-snbux_yUlEdGkOTj9AXJwJLAxQ5ofh4iSetHyeKUTlO0E7HpNoHcigXlW5sDosiuLojaT9_kn-aJk40Py_7q1-Znn09fv4N-swuU0ByFNbVyZlYQqmbR8DyIVW00) too.)

After you have included `C4_Container.puml` you can use the defined macro definitions for the C4 elements: `Person`, `Person_Ext`, `System`, `System_Ext`, `Container`, `Relationship`, `Boundary`, and `System_Boundary`

```plantuml
@startuml C4_Elements
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(personAlias, "Label", "Optional Description")
Container(containerAlias, "Label", "Technology", "Optional Description")
System(systemAlias, "Label", "Optional Description")

Rel(personAlias, containerAlias, "Label", "Optional Technology")
@enduml
```

![test](https://www.plantuml.com/plantuml/png/ZOxDIWGn48JlUOeufn5qSjcJfvNHsugBFsV99iqcsEc4T0VTjpSCE2AYUAeAgVwgjYosIakevytBBK824bPdaHms3pg85BuofjgtwHWbj4DZg2wJzDpaSZAliRh04ioykToZ9Nc-snbux_yUlEdGkOTj9AXJwJLAxQ5ofh4iSetHyeKUTlO0E7HpNoHcigXlW5sDosiuLojaT9_kn-aJk40Py_7q1-Znn09fv4N-swuU0ByFNbVyZlYQqmbR8DyIVW00 "test")

In addition to this, it is also possible to define a system or component boundary.

Take a look at the following sample of a C4 Container Diagram:

```plantuml
@startuml Basic Sample
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(admin, "Administrator")
System_Boundary(c1, "Sample System") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![Basic Sample](https://www.plantuml.com/plantuml/png/JP3FJkD03CRlUGflzf9AtKHTxMbFJIC41ueYaiAncauC6J5_HZEEGeLuTpngQPcBDVv-jZzx7Ka4ceo6ZOXAGYUCrvZzKbRgQK0OYNpyNrL1pEMhed4wJ163T9RGKYcTgTvKa6EaiMh-_McriBJRtbVuplg00oVt3SD2MGobvpbPrcA8pXPYCCek8QzJL96281VoHTOT8w7PRzna1n6EXLmnTB859orVm4S6_2wTYnaFU-4zayzuWDfxhQGWvMpEgURt4kgkBHzkUYu927_B5MoVcgJLMhivGbeg0ZdWZRnWn4oQL1hPpue80v0og7bMP8kVPvC5dKJkSyPOp1vHVoztjRMBNCdnhk_RZga4NTHhcrkao5zCuIKuyxDapHTD1_m2 "Basic Sample")

Entities can also be decorated with icons/sprites using the $sprite parameter, for example:

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

!define DEVICONS https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/devicons
!define FONTAWESOME https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/font-awesome-5
!include DEVICONS/angular.puml
!include DEVICONS/java.puml
!include DEVICONS/msql_server.puml
!include FONTAWESOME/users.puml

LAYOUT_WITH_LEGEND()

Person(user, "Customer", "People that need products", $sprite="users")
Container(spa, "SPA", "angular", "The main interface that the customer interacts with", $sprite="angular")
Container(api, "API", "java", "Handles all business logic", $sprite="java")
ContainerDb(db, "Database", "Microsoft SQL", "Holds product, order and invoice information", $sprite="msql_server")

Rel(user, spa, "Uses", "https")
Rel(spa, api, "Uses", "https")
Rel_R(api, db, "Reads/Writes")
@enduml
```

![Sprites/Icons](https://www.plantuml.com/plantuml/png/hL9DZzCm5BpdLtWh3brfkpu05oIahTh2Lkf7wGSLf-hLVcaCZXtyd9QVptEQhI8-90wSx7Z6CvvvUQ888TQbpUwCKxRMA8eOAtedPO3Buyd4eZxMX45v5z75H-LB-Sq4LL0ivEZDO6N1nTry9l47uner7nv6J0RZC3nMIJgxqvZpfnXFFaz7oyNc7pnYNO4EhsMLz5baO1WTvCmOK1LCH98bKCGWDPuJHZUN3yl5ThYVR9RpoNyrQixWWkHB7Boz5NPB9S6TQWjjwD_Xht26ls4bVRS7VjaPVxdUJIDhPb3RwMpuPRdR7lRJxVDXDlauMOpxzrcsOe9t_KHy4BrHJT6N67gyNw6lB8fOG1GEKOigU5shI0o-kYPztsiCUlVPRO1zge0lRrR3fD46JDjjWQ9aYZ1SPSX1jTAHprLhUyM0FSI5k-yQlIXrhQ0oB3nSJPD-AYkjp-2qHH9WhU3PCP58M7yogYkNs5sjyR6lZtnx316EG9YKvaO5JpwFOlDfraXxg-cbXWVXWyOWs8wVVVP68Q-v3oL4urtNh3ChzipMQDk-hrtj22d9DxyU4nBU89plp_1XVStUF7cDe4dkarM2dz1fdlTF "Sprites/Icons")

Similar to icons/sprites is it possible to add links to all elements and relationships:

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

Person(admin, "Administrator", $sprite="person2", $link="https://github.com/plantuml-stdlib/C4-PlantUML/blob/master/LayoutOptions.md#hide_person_sprite-or-show_person_spritesprite")
System_Boundary(c1, "Sample System", $link="https://github.com/plantuml-stdlib/C4-PlantUML") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", $descr="Allows users to compare multiple Twitter timelines", $link="https://github.com/plantuml-stdlib/C4-PlantUML/blob/master/LayoutOptions.md")
}
System(twitter, "Twitter", $link="https://github.com/plantuml-stdlib/C4-PlantUML")

Rel(admin, web_app, "Uses", "HTTPS", $link="https://plantuml.com/link")
Rel(web_app, twitter, "Gets tweets from", "HTTPS", $link="https://plantuml.com/link")
@enduml
```

> `png` itself supports no links, therefore the following image is generated as `svg` image.
> Github does not support `svg` links in README.md.
> If you click on the image a new window is opened and there you can use the links.

![Click on the image that the links are working](https://www.plantuml.com/plantuml/svg/jP9FQzj04CNl-XHRfGS7R8c4dWg6kAQqXwGrjT8UnKexhPRidsLcX6fAltjdhJWXz5H3TT2YDwFtVZpfXbWZZzuLhspetMX03So9tjOrwgdwONaOkv40-nWO0bTzzFM3nNuW7khjczNEwS3tTxSr_9Iv0IDYkvLbRGDWbR9riGEa61RQU1kMgjpaqnAZveZbKhscX9PXNQRZtdMMd0qFw_B4CdCSmrCE5DSLiN6sUy7GkTZLNXC3rhVw44V-dDZ6G9Kt5uCrqCu9xHouYhYY8KulrVbUNXRxWnZvzbqSWz5uMFHNmhxNFZbGy-nSqF9I_IgKN4z5BIReMfsI97o3JcrIShRNcRqKQNknL9lzhlhqlf5N4DHrTQNklcvplW7gSLrkd8iJgVofI75KGf2qRFhHiSt4pMIP0HLR3y8Cz5zQbjf-FnQtu3bH-1-ppw-hABw0E_q_prNT4r3kvsFJxFP_kvyiZ_vv94RPvydWcV03CCaZvECxHl-FhZSGZ4X_0000 "Click on the image that the links are working")

Elements and relationships can be decorated with tags and explained via a calculated legend, for example:

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

AddElementTag("v1.0", $borderColor="#d73027")
AddElementTag("v1.1", $fontColor="#d73027")
AddElementTag("backup", $fontColor="orange")

AddRelTag("backup", $textColor="orange", $lineColor="orange", $lineStyle = DashedLine())

Person(user, "Customer", "People that need products")
Person(admin, "Administrator", "People that administrates the products via the new v1.1 components", $tags="v1.1")
Container(spa, "SPA", "angular", "The main interface that the customer interacts with via v1.0", $tags="v1.0")
Container(spaAdmin, "Admin SPA", "angular", "The administrator interface that the customer interacts with via new v1.1", $tags="v1.1")
Container(api, "API", "java", "Handles all business logic (incl. new v1.1 extensions)", $tags="v1.0+v1.1")
ContainerDb(db, "Database", "Microsoft SQL", "Holds product, order and invoice information")
Container(archive, "Archive", "Audit logging", "Stores 5 years", $tags="backup")

Rel(user, spa, "Uses", "https")
Rel(spa, api, "Uses", "https")
Rel_R(api, db, "Reads/Writes")
Rel(admin, spaAdmin, "Uses", "https")
Rel(spaAdmin, api, "Uses", "https")
Rel_L(api, archive, "Writes", "messages", $tags="backup")

SHOW_LEGEND()
@enduml
```

![tags](https://www.plantuml.com/plantuml/png/bLJVJzim47xdh_2oFQGQQs4_X3G9YQf5OrBPkXR48xhQryJ3iIFVfS1_ltEQKkWgfZtPkljyttrtNt96396RoXsyiLwxng0gcMlwEXX4kEyNbijcqH167JoZvxuErU3EHbqIbuFHvmzJ1vwlBoS3V92yGIF1sv60mNgC_JgLFXWQS-wmalTNKEJPwhX_b1sgTuiG3SPHS26UPc_DoQUZZoTPRm_wEA6NKlHVs0NekwRUGOS8la019_GCtGwIyM47AK4dtUyDpldHeJfLOw0IpKGYUKygJp5Iy7cQrA7AHWrng31cSfzYgEK5by3A8nfLns0QpIGDTQ_0LDOBT9XEIno1mrzlOPj4aX0-5L8h2st0uxrAqrAof3fuz4ojG2Zej1sZK3wj9gSQX68-7IOcaTWuQ4clf58b46KzOro2xXf83BeJjiv18hyNYxGTT5lTqXtjqWsVwrJxcU7v3FwtXSq0Nb4DjKqTJBydmj-mWdHUW3SEIO5pIjmkG2BbGc6rojDdqT-EjhKvsU2fzrBi-rsgyI8t2oa-1eO542QYIwjZeB1aDVyrQPc3CxJPvA5gFmWbtOYwLR0QvLo6M04BuqiTKPTsXKdB-fQbQsCifyOBwuiKc7E8ekkBUaI8MpDit2_6dQ7hNBlsmpKXfPVjNq00ATzcP73xqxUpzL1RiJC4GuERQ1cxzCRTs_tlv-ZIhn5DraHRwHsFt2eaWWBtIfnV_BovdPn_E_ynpdi7P-XDKxa_ "tags")

## Supported Diagram Types

> * `arg`.. argument required (e.g. `alias`)
> * `?arg`.. argument optional  (e.g. `?descr`)

* System Context & System Landscape diagrams
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Context.puml`
  * Macros: 
    * `Person(alias, label, ?descr, ?sprite, ?tags, $link)`
    * `Person_Ext`
    * `System(alias, label, ?descr, ?sprite, ?tags, $link)`
    * `SystemDb`
    * `SystemQueue`
    * `System_Ext`
    * `SystemDb_Ext`
    * `SystemQueue_Ext`
    * `Boundary(alias, label, ?type, ?tags, $link)`
    * `Enterprise_Boundary(alias, label, ?tags, $link)`
    * `System_Boundary`
  * Sprites:
    * `person`
    * `person2`
    * `robot`
    * `robot2`

* Container diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml`
  * Additional Macros: 
    * `Container(alias, label, ?techn, ?descr, ?sprite, ?tags, $link)`
    * `ContainerDb`
    * `ContainerQueue`
    * `Container_Ext`
    * `ContainerDb_Ext`
    * `ContainerQueue_Ext`
    * `Container_Boundary(alias, label, ?tags, $link)`

* Component diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml`
  * Additional Macros: 
    * `Component(alias, label, ?techn, ?descr, ?sprite, ?tags, $link)`
    * `ComponentDb`
    * `ComponentQueue`
    * `Component_Ext`
    * `ComponentDb_Ext`
    * `ComponentQueue_Ext`

* Dynamic diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Dynamic.puml`
  * Additional Macros: 
    * `RelIndex(index, from, to, label, ?tags, $link)`
    * (lowercase) `increment($offset=1)`: increase current index (procedure which has no direct output)
    * (lowercase) `setIndex($new_index)`: set the new index (procedure which has no direct output)
    * `LastIndex()`: return the last used index (function which can be used as argument)

    following 2 macros requires V1.2020.24Beta4 (can be already tested with https://www.plantuml.com/plantuml/)
    * `Index($offset=1)`: returns current index and calculates next index (function which can be used as argument)
    * `SetIndex($new_index)`: returns new set index and calculates next index (function which can be used as argument)

* Deployment diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Deployment.puml`
  * Additional Macros: 
    * `Deployment_Node(alias, label, ?type, ?descr, ?sprite, ?tags, $link)`
    * `Node(alias, label, ?type, ?descr, ?sprite, ?tags, $link)`: short name of Deployment_Node()
    * `Node_L(alias, label, ?type, ?descr, ?sprite, ?tags, $link)`: left aligned Node()
    * `Node_R(alias, label, ?type, ?descr, ?sprite, ?tags, $link)`: right aligned Node()

Take a look at each of the [C4 Model Diagram Samples](samples/C4CoreDiagrams.md).

## Relationship Types

* `Rel(from, to, label, ?techn, ?descr, ?sprite, ?tags, $link)`
* `BiRel` (bidirectional relationship)

You can force the direction of a relationship by using:

* `Rel_U`, `Rel_Up`
* `Rel_D`, `Rel_Down`
* `Rel_L`, `Rel_Left`
* `Rel_R`, `Rel_Right`

In following sample a person uses different systems, and a group of persons which have bidirectional relationships

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
HIDE_STEREOTYPE()

Person(a, "A")
Person(b, "B")
Person(c, "C")
Person(d, "D")
Person(e, "E")

BiRel_U(a, b, "talk with")
BiRel_R(a, c, "talk with")
BiRel_D(a, d, "talk with")
BiRel_L(a, e, "talk with")

Person(x, "X")
System(s1, "S1")
System(s2, "S2")
System(s3, "S3")
System(s4, "S4")

Rel_U(x, s1, "uses")
Rel_R(x, s2, "uses")
Rel_D(x, s3, "uses")
Rel_L(x, s4, "uses")
@enduml
```

![(unidirectional) relationship versus bidirectional relationship](https://www.plantuml.com/plantuml/png/RP11Qxj044VlVehySqhWNoNggQSqAhHWgMW2xKaskqELw1fsHv9--yueHOKSttlBZs7t5eN1lcsSVxMMJQzWLI5UxRFd6N5plski-dDlmSXE8sXqPTTwbzh8ocBbHU5JrWYDf_VKWpjr1Ofa6T5ZKMimxfMdNz_Yf2oEIPvy7B-oPBDrd0oCxVH6_5-jNzRRFpmJ7YQKXD64YZ2U40WJGkTGvz2K9nxZ0HJDPNMZmwcDAUSa7wQOatgOKawmIDFXT_AVnCMFHMWtTaTSx6R2P-7FHC0Yc8cGHSYRu_aqESpq5YpPyN2M_bB6WmoMCXraECazQ4L__mi0 "(unidirectional) relationship versus bidirectional relationship")

## Layout (arrange) elements (without relationships)

In rare cases, you can force the layout of elements which have no relationships by using:

* `Lay_U(from, to)`, `Lay_Up(from, to)`
* `Lay_D(from, to)`, `Lay_Down(from, to)`
* `Lay_L(from, to)`, `Lay_Left(from, to)`
* `Lay_R(from, to)`, `Lay_Right(from, to)`

In following sample a person uses different systems, and a group of persons which have no relationships

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
HIDE_STEREOTYPE()

Person(a, "A")
Person(b, "B")
Person(c, "C")
Person(d, "D")
Person(e, "E")

Lay_U(a, b)
Lay_R(a, c)
Lay_D(a, d)
Lay_L(a, e)

Person(x, "X")
System(s1, "S1")
System(s2, "S2")
System(s3, "S3")
System(s4, "S4")

Rel_U(x, s1, "uses")
Rel_R(x, s2, "uses")
Rel_D(x, s3, "uses")
Rel_L(x, s4, "uses")
@enduml
```

![Relationship versus Layout](https://www.plantuml.com/plantuml/png/LSrHQxCm5CRnUpz5trufl5EgNksgcmeRE2PQORkIc1ocJ6D9JbZxxNTY6R5tv_yZF3bgP0hDF7d_Hiad8s0t89xrOnGfzXD-ZJYOtcXGV9484aE-pD7tgFYWSOYozA6QcCJshOpWWY052C8keyTibA32ivr-USsBhZaLTV5--gmAF_2y2fHUfC_-x_PF--0lUyfdbvmoSoaeSvT0ML1w9RjshPtgW_MkxSrlTsvlSRjBUuFx_4837pJGN3N2xEi3TNFOG6mXta1Y8Tb0QY4by6gOkjPEhZD6WoQrMAyOtsE-OdAFvOgfmoD8OURf5m00 "Relationship versus Layout")

(In combination with [SHOW_FLOATING_LEGEND()](LayoutOptions.md#show_floating_legend)) a greater distance between an element and the
e.g. floating legend could be required that all e.g. corners of the drawing area can be reached.

* `Lay_Distance(from, to, ?distance)`: Sets the distance between `from` and `to` with down alignment (Lay_Distance(from,to,0) equals Lay_D(from, to)). The default alias of the floating legend is LEGEND().

In following sample the floating legend should be in the left bottom corner of the drawing are.
(The normal SHOW_LEGEND() call requires no extra Lay_Distance() call and the legend is automatically drawn below the diagram on the right side)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

!define DEVICONS https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/devicons
!define FONTAWESOME https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/font-awesome-5
!include DEVICONS/angular.puml
!include DEVICONS/java.puml
!include DEVICONS/msql_server.puml
!include FONTAWESOME/users.puml

Person(user, "Customer", "People that need products", $sprite="users")
Container(spa, "SPA", "angular", "The main interface that the customer interacts with", $sprite="angular")
Container(api, "API", "java", "Handles all business logic", $sprite="java")
ContainerDb(db, "Database", "Microsoft SQL", "Holds product, order and invoice information", $sprite="msql_server")

Rel(user, spa, "Uses")
Rel(spa, api, "Uses")
Rel_R(api, db, "Reads/Writes")

SHOW_FLOATING_LEGEND()
Lay_Distance(LEGEND(), db, 1)
@enduml
```

![db below legend, 1 unit distance](https://www.plantuml.com/plantuml/png/hL7DZXez4BpFKtZHTm1fmVgKv18fKX2mkqZy4633STJO3UF4Oq_S7aZUFcqOq2XHf1no6azLkyfL_M2SihL6KSHOqNif0vm7HnEBUbyJ1kLTH1S7ofVogmcge5Z8qTl-oeABh_EPnE_CQzGCvYCU1kCm3Agwj5dseF70ls8y-JmTBHURl_28TGKwl95LqcUHlc6sV-29FbN1H2HP0aKCKkCfSNHtULekjiFTPBESJ_wfqGM3Cv8liVykknLsJoN17MiBJUZVwIzmWZzn9NspEM4uuI_NssbaUZirdQxuw5qtGO-YCwef-X93Xyyhz9L54Gk8mY5gKGMlQnM9oV-kcJvqBbATNdPVLPSguCkRrJ1fD57ISLkWA7b461Sn740rqf5nrTXUEM0FSUQMsqOtfROLL8Q5Xwjfqa-rfEyBE6sH15WhU4iyI2IiFnhLbalJRQtnlgltV7iC4VP0c9JcHWLF_X35vjFi8ksjfbiDZy87ZK6m7J_xv8r2_XvyA24QxzfchQsmPxP6s_HzxUgLC5MOu0kGOhNHV7rDUddW6a6Jt2NXH6URb-KkVvejXzlfuZcVJPudYt6tbytWHpus5C4fxDxGgyJ_lUmZEitR_ma0 "db below legend, 1 unit distance")

## Global Layout Options

C4-PlantUML also comes with some layout options to make it easy and reusable to create nice and useful diagrams:

* [LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT() or LAYOUT_LANDSCAPE()](LayoutOptions.md#layout_top_down-or-layout_left_right-or-layout_landscape)
* [LAYOUT_WITH_LEGEND() or SHOW_LEGEND(?hideStereotype)](LayoutOptions.md#layout_with_legend-or-show_legend)
* [SHOW_FLOATING_LEGEND(?alias, ?hideStereotype) and LEGEND()](LayoutOptions.md#show_floating_legendalias-hidestereotype-and-legend)
* [LAYOUT_AS_SKETCH() and SET_SKETCH_STYLE(?bgColor, ?fontColor, ?warningColor, ?fontName, ?footerWarning, ?footerText)](LayoutOptions.md#layout_as_sketch)
* [HIDE_STEREOTYPE()](LayoutOptions.md#hide_stereotype)

C4-PlantUML also comes with some person sprite/portrait options:

* [HIDE_PERSON_SPRITE()](LayoutOptions.md#hide_person_sprite)
* [SHOW_PERSON_SPRITE(?sprite)](LayoutOptions.md#show_person_sprite)
* [SHOW_PERSON_PORTRAIT()](LayoutOptions.md#show_person_portrait)
* [SHOW_PERSON_OUTLINE()](LayoutOptions.md#show_person_outline) (requires PlantUML version >= 1.2021.4)

## Sprites and other images

C4-PlantUML offers predefined person and robot sprites which can be directly used:

* `person`,`person2`
* `robot`, `robot2`

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml

Person(pB, "Sam", $sprite="person2")
Person_Ext(pA, "Bob", $sprite="person")

System_Ext(robB, "Robot A", $sprite="robot2")
System_Ext(robA, "Robot B", $sprite="robot")

SHOW_LEGEND()
@enduml
```

![Predefined person and robot sprites](https://www.plantuml.com/plantuml/png/PS_1IiGm4CRnUv-Y5WzTM3SWdWHXsxNeOTN5HJoM9XrCiCc4oGJNjpSf8hAzplpumxSDF117EnKNngafZb1gPXzkXQ3XQ_DXM4SP0v12n-1uez2AJqDA1zPYTtDrc0R7Rqzx0QVq7s5Cntw7rgFBtETqSG0Aw6hVhilgEDXgNLu6JuRXhlBpwxfQ_QA-Et7jcmHRb4kON77y3WnsXeGoDrzH8fVDVqxvbB9dkldJxKBFxSUNztxVFNJFz_MgsAP5QS0F "Predefined person and robot sprites")

Additional `$sprite` (images) can be defined with following PlantUML supported options:

* included (standard library) sprites via their `{SpriteName}`; details see [sprites](https://plantuml.com/sprite)
* images via `img:{File or Url}`
* OpenIconic via `&{OpenIconicName}`; details see [openiconic](https://plantuml.com/openiconic)

Size of the displayed images can be changed with `,scale={factor}`.
Color of the displayed images can be changed with `,color={color}   `.

(If sprites are defined via $tags then the calculated legend is updated too)

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

'stdlib users.puml defines sprite "users"
!include <office/users/users.puml>


AddRelTag("plantuml", $textColor="$ARROW_COLOR", $lineColor="$ARROW_COLOR", $sprite="img:http://plantuml.com/logo3.png{scale=0.3}", $legendSprite="img:http://plantuml.com/logo3.png{scale=0.1}", $legendText="console triggered")

Person(user, "user group displayed with a sprite", $sprite="users")


Container(container, "Container with scaled and colored OpenIconic", $sprite="&folder,scale=5.0,color=gray")

System(system, "System with an image", $sprite="img:http://plantuml.com/logo3.png")

Rel(user, system, "Rel with image (via tags)", $tags="plantuml")
Rel(user, container, "Rel with OpenIconinc", $sprite="&folder")

SHOW_LEGEND()
@enduml
```

![Sprite, image and OpenIconic](https://www.plantuml.com/plantuml/png/bP91RzGm48Nl_XL3L45MsYP5XSkAe5PB1KWBMwL572itddKjENPaEvGLuhypjfTi3d3OKvonvvltddtb0tTXx3LxeKodHu7m5CBWLtNj-7CbLNWQ7qUFhhCce0bLP_jwqDp4ddCVX5QFzVhD-MqiVVkogNlk0pegFQofWok3hXeYdxtAfo7IVAg1m1qTyE07fm92aRQAevHtThTJ7TQfNXyRtpF6heLeKTzpMHP_zHHBE0luCwojjgufpgxRTllzORtTRDkufMdMVxQoWAPGlLn5_wjwCfaSQoljPJKO-SjtN6DpKLt-JaYKQCJToTslPzttfBWfA5zlDK9mIafqA8e5OxTas9eo6b_cT40wEmuWbAS9UnJmJ3S4_93Wt4hEaY1ikeYoowj4cwePaPG9u4P05pEYzNP0yvbQL3VdljnPBOYGhRojBfRfV2CTtyTnTtiVi2zz-j2S_7_GQK3rNE99aKTeY_gGmiIbKe9c8fG_58V0fLz4U5mqntUnc06c3EQCoQhvbzTawnEzbytDnvkl7ye5kq8Z2Fm7 "Sprite, image and OpenIconic")

Relationship specific sprites are typically smaller and therefore following options are possible:
* use smaller icons (like the $triangle in the following sample)
* use an additional scale factor (direct as part of the argument, or via a variable)
* if sprite argument starts with `&` an OpenIconic name can be used too (details see https://useiconic.com/open)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Context.puml

Person(user, "User")
Person(user1, "User 1")
Person(user2, "User 2")
Person(user3, "User 3")

System(system, "System")

' normal sprites are too big 
Rel_L(user, user2, "informs", "courier", "normal sprites are too big", $sprite="person2")

' scaled sprites are ok
Rel_R(user, user3, "informs", "courier", "scaled sprites are OK", $sprite="person2,scale=0.5")

' combine sprite and scale to a new sprite
!$combinedSprite="person2,scale=0.5"
Rel_R(user, user3, "informs", "courier", "combined sprites are OK", $sprite=$combinedSprite)

' special smaller sprites can be used
sprite $triangle {
    00000000000
    00000F00000
    0000FBF0000
    0000FBF0000
    000F999F000
    000F999F000
    00F66666F00
    00F66666F00
    0F3333333F0
    0F3333333F0
    0FFFFFFFFF0
    00000000000
}
Rel_R(user1, system, "orders", "http", "small sprites, like the small triangle", $sprite="triangle")

' if sprite starts with &, sprite defines a OpenIconic, details see https://useiconic.com/open/
Rel_D(user, user1, "requests", "async message", "if sprite starts with &, it defines a OpenIconic like &envelope-closed", $sprite = "&envelope-closed")
@enduml
```

![Relationship with sprite or OpenIconic](https://www.plantuml.com/plantuml/png/bLHHQzim47xthxY6qBMGncco3J88b7KOnZfQMlfS5EaIYyYIfvENbR7_FbcoccID1xqN-RxJtVVTSV8LEMPTKwdiH6gk6e5GEbVJfpotR3jUIrSsouRGSgCTQZVcfietqlAIN9bVlx-uKqoxn-ytEVxoSO72Wq_N_hBtntLREBj3IqQVjLL6C7Zqn-1y7xpiKBWynAS9dnxYiuJFF9uzF9F3wep2uIFHRoFlG1jRCGLKM-cGW5a4PmmivHgoUrHFDvsen2RrocVGm7zoqrY9jltih-AZmmWl1dKGE8t4n9b2SP1YDe7oVezorajv9F_ssn6sKRYuc8m_H5vkggNKs2K2qo9AyOA1WSPj5ybEXjrLyT1RyGrwKx5-nV_mnIdLo6KxMJzUXVObcJCDIsmfHHOn63ehcLuhXDyPU9liRESNXtxnkVYVNypdywBVBpwsLlJvnInQqUSdcxpI-oSEDkt-o-OQAz26oRPFi3t3OD9OHg3a1i6L215F8zdVYuJ5TP2hj0dXcHDifIlXT9HGWIkfaO31ROtwApTQyf577PEAW73tC_1QPGY77u3nj_FGnPTkFT8xjlYZGNAX2qRFcaE5H6oDBT0hHxgZKcB3fwX_elAK5rmPGh5h5nOmU1KzpwvGYwPIVm40 "Relationship with sprite or OpenIconic")

## Custom tags/stereotypes support and skinparam updates

Additional tags/stereotypes can be added to the existing element stereotypes (component, ...) and highlight,... specific aspects:

* `AddElementTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`:
  Introduces a new element tag. The styles of the tagged elements are updated and the tag is displayed in the calculated legend.
* `AddRelTag(tagStereo, ?textColor, ?lineColor, ?lineStyle, ?sprite, ?techn, ?legendText, ?legendSprite)`:
  Introduces a new Relationship tag. The styles of the tagged relationships are updated and the tag is displayed in the calculated legend.
* `AddBoundaryTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?type, ?legendText)`:
  Introduces a new Boundary tag. The styles of the tagged boundaries are updated and the tag is displayed in the calculated legend.
* `UpdateElementStyle(elementName, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`:
  This call updates the default style of the elements (component, ...) and creates no additional legend entry.
* `UpdateRelStyle(textColor, lineColor)`:
  This call updates the default relationship colors and creates no additional legend entry.
* `UpdateBoundaryStyle(?elementName, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?type, ?legendText)
  This call updates the default style of the existing boundaries and creates no additional legend entry.
  If the element name is "" then it updates generic, enterprise, system and container boundary style in on call.
* `RoundedBoxShape()`: This call returns the name of the rounded box shape and can be used as ?shape argument.
* `EightSidedShape()`: This call returns the name of the eight sided shape and can be used as ?shape argument.
* `DashedLine()`: This call returns the name of the dashed line and can be used as ?lineStyle argument.
* `DottedLine()`: This call returns the name of the dotted line and can be used as ?lineStyle argument.
* `BoldLine()`: This call returns the name of the bold line and can be used as ?lineStyle argument.

Each element can be extended with one or multiple custom tags via the keyword argument `$tags="..."`, like `Container(spaAdmin, "Admin SPA", $tags="v1.1")`.
Multiple tags can be combined with `+`, like `Container(api, "API", $tags="v1.0+v1.1")`.

### Element specific tag definitions

Sometimes an added element tag is element specific and all element specific colors should be used, e.g. a specific user role should be defined as element tag with the specific colors `...PERSON_...` like
```plantuml
AddElementTag("admin", $fontColor=$ELEMENT_FONT_COLOR, $bgColor=$PERSON_BG_COLOR, $borderColor=$PERSON_BORDER_COLOR, $sprite="osa_user_audit", $legendText="administration user")
```
Therefore element Add...Tag() shortcuts are added which use the specific colors as default values and the call can be simplified like
```plantuml
AddPersonTag("admin", $sprite="osa_user_audit", $legendText="administration user")
```

Following calls introduces new element tags with element specific default colors:
* `AddPersonTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?legendText, ?legendSprite)`
* `AddExternalPersonTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?legendText, ?legendSprite)`
* `AddSystemTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?legendText, ?legendSprite)`
* `AddExternalSystemTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?legendText, ?legendSprite)`
* `AddComponentTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`
* `AddExternalComponentTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`
* `AddContainerTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`
* `AddExternalContainerTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?techn, ?sprite, ?legendText, ?legendSprite)`
* `AddNodeTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?sprite, ?techn, ?legendText, ?legendSprite)`
  (node specific: $type reuses $techn definition of $tags)

### Boundary specific tag definitions

Like the element specific tag definitions exist boundary specific calls with their default colors **and type**:
* `UpdateContainerBoundaryStyle(?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?type, ?legendText)`
* `UpdateSystemBoundaryStyle(?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?type, ?legendText)`
* `UpdateEnterpriseBoundaryStyle(?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape, ?type, ?legendText)`

### Comments

* `SHOW_LEGEND()` supports the customized stereotypes
      (`LAYOUT_WITH_LEGEND()` cannot be used, if the custom tags/stereotypes should be displayed in the legend).
* `SHOW_LEGEND()` has to be last line in diagram.
* Don't use space between `$tags` and `=` (PlantUML does not support it).
* Don't use `,` as part of the tag names (PlantUML does not support it in combination with keyword arguments).
* If 2 tags define the same skinparam, the first definition is used.
* If specific skinparams have to be merged (e.g. 2 tags change the font color) an additional combined tag has to be defined. Use `&` as part of combined tag names.

* Colors of relationship tags cannot be automatically merged (PlantUML does not support it).
  If one tag modifies the line color and the other the text color, an additional combined tag has to be defined and used.

### Sample with different tag combinations

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml

UpdateElementStyle(person, $fontColor="green")
AddElementTag("v1.0", $fontColor="#d73027", $borderColor="#d73027")
AddElementTag("v1.1", $fontColor="#ffffbf", $borderColor="#ffffbf")
AddElementTag("v1.0&v1.1", $fontColor="#fdae61", $borderColor="#fdae61")
AddElementTag("fallback", $bgColor="#444444")

' If spaces are requested in the legend, legend text with space has to be defined (incl. all other additional details)
AddElementTag("microService", $shape=EightSidedShape(), $legendText="micro service (eight sided) (no text, no back color)")
' If no special tag names should be displayed in legend, no explicit legend text definition is required (all additional details are automatically calculated) 
AddElementTag("storage", $shape=RoundedBoxShape())

UpdateRelStyle(black, black)
AddRelTag("service1", $textColor="red")
AddRelTag("service2", $lineColor="red")
AddRelTag("service1&service2", $textColor="red", $lineColor="red")

Container(spa, "SPA", "angular", "The main interface that the customer interacts with via v1.0", $tags="v1.0")
Container(spaAdmin, "Admin SPA", "angular", "The administrator interface that the customer interacts with via new v1.1", $tags="v1.1")
Container(api, "API", "java", "Handles all business logic (incl. new v1.1 extensions)", $tags="v1.0&v1.1+v1.0+v1.1")
Container(spa2, "SPA2", "angular", "The main interface that the customer interacts with via v1.0", $tags="v1.0+fallback")
Container(spaAdmin2, "Admin SPA2", "angular", "The administrator interface that the customer interacts with via new v1.1", $tags="fallback+v1.1")

Container(services, "Services", "techn", $tags="microService")
Container(fileStorage, "File storage", "techn", $tags="storage")

Rel(spa, api, "Uses", "https")
Rel(spaAdmin, api, "Uses", "https")
Rel_L(spa, spa2, "Updates", "https")
Rel_R(spaAdmin, spaAdmin2, "Updates", "https")

Rel_D(api, services, "uses service1 via this call", $tags="service1")
Rel_D(api, services, "uses service2 via this call", $tags="service2")
Rel_D(services, fileStorage, "both services stores via this call", $tags="service1&service2+service1+service2")

SHOW_LEGEND(false)
@enduml
```

![merged tags](https://www.plantuml.com/plantuml/png/jLLDR-Cs4BtxLqpTOcl1Rhns5rsWG81DisbtWRGDuWGz1cDnBB5BaIg7oiU_xr0q2pbo6_GG7KoAy_Zuvcc6_i01VUWQC_bAsz9qYg0EeUKVbqkF3oUL3dMtxPXywMmW6qvAroo_Q5_M7Ehb-RllhWpQSFlhvP8U9Qv8oUBTkMjQPoEyZTIJsrPXe0j3ZQnjmfEXMKkUdLt0DpiXFdV6-TDfvOdij9YSARN7tc0rczwlJjvE3v5Vg_VVlrs_ZwjRvnNvm_MZ7Ald73jvjhinHre_hkFDKIA5zCDgJ9JMnqGxD6QBvPT-HvNHx_f7q9DluVCEkCMI6D0JUFgh8mwaG5i8DO6XIhnUx4S8uZqyw52dJL0ZGt2m9L2qqrRspUB7FG4v5vmGU42bTD3EeX5CG6rufBBHfNSRylUwfAYKQspfz49NTTXeHMeJtsU5H9AC6r5ncdO1fsqmemW7ZlW2PjRrMXSWasW0b37tObgab6MLMoer6WXOWSM66BXsdL5zCffRWq_9Xco1xA77rkXIXw4TAVC-HT3SEwXzD48i62UVRCOkk0Q3BWNp1F9RTWP35FxS6WxEOpLmvTfriVP_SezxLufSzDTaKi5lZIIyW7xelPP88ajUzVKZqdDLYThfCTmwueosz09kzIPl61CVfPYSEnjGLlsCMrp0T7DrDfK1RIK--3YzgGaQWO2sWVmkrbgeCVGrMNOizf5FCIm3fvAyrmYvWmDMV9hwkJWyxamrsie9_GZ7JyOOqnmyYlt_LuAb1qYzEv2nEf21hOuAhZx70__4UupZ9xJA4FUji-rOWCnWNANBt5IP6VeRaBMpN1oSaYwDUPpDu-nvxklazVhLp9xd2-Uew-kXxUlNzpsBoLuC9QMAvMZ8VXf512fh-m_1uSKqp6Yd3MrIQygkd-KDSgUEMN9414Zdf99F5N3BwTZ-Zr3YAPpC-W_CtMKYsN_HrFuZqFM0Ai_-1TxZFwQo73ZJCN5-N_KUXrepn5jha5sAHtzVPbc_mBBEB8CFTEZrreKQSh0tNORZfEFxQPvNveFp9fjFl_znTtdnoyLl7sTICap5v0DPrJNcRm00 "merged tags")

### Sample with tag dependent sprites and custom legend text

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml

!include <office/Servers/database_server>
!include <office/Servers/file_server>
!include <office/Servers/application_server>
!include <office/Concepts/service_application>
!include <office/Concepts/firewall>

AddExternalPersonTag("anonymous_ext", $sprite="osa_user_black_hat", $legendText="anonymous user")
AddPersonTag("customer", $sprite="osa_user_large_group", $legendText="aggregated user")
AddPersonTag("admin", $sprite="osa_user_audit,color=red", $legendSprite="osa_user_audit,scale=0.25,color=red", $legendText="administration user")

AddContainerTag("webApp", $sprite="application_server", $legendText="web app container")
AddContainerTag("db", $sprite="database_server", $legendText="database container")
AddContainerTag("files", $sprite="file_server", $legendText="file server container")
AddContainerTag("conApp", $sprite="service_application", $legendText="console app container")

AddRelTag("firewall", $textColor="$ARROW_COLOR", $lineColor="$ARROW_COLOR", $sprite="firewall,scale=0.3,color=red", $legendText="firewall")

Person_Ext(anonymous_user, "Bob", $tags="anonymous_ext")
Person(aggregated_user, "Sam, Ivone", $tags="customer")
Person(administration_user, "Bernd", $tags="admin")

System_Boundary(c1, "techtribes.js"){
    Container(web_app, "Web Application", "Java, Spring MVC, Tomcat 7.x", $tags="webApp")
    ContainerDb(rel_db, "Relational Database", "MySQL 5.5.x", $tags="db")
    Container(filesystem, "File System", "FAT32", $tags="files")
    ContainerDb(nosql, "NoSQL Data Store", "MongoDB 2.2.x", $tags="db")
    Container(updater, "Updater", "Java 7 Console App", $tags="conApp")
}

Rel(anonymous_user, web_app, "Uses", "HTTPS", $tags="firewall")
Rel(aggregated_user, web_app, "Uses", "HTTPS", $tags="firewall")
Rel(administration_user, web_app, "Uses", "HTTPS", $tags="firewall")

Rel(web_app, rel_db, "Reads from and writes to", "SQL/JDBC, port 3306")
Rel(web_app, filesystem, "Reads from")
Rel(web_app, nosql, "Reads from", "MongoDB wire protocol, port 27017")

Rel_U(updater, rel_db, "Reads from and writes data to", "SQL/JDBC, port 3306")
Rel_U(updater, filesystem, "Writes to")
Rel_U(updater, nosql, "Reads from and writes to", "MongoDB wire protocol, port 27017")

Lay_R(rel_db, filesystem)

SHOW_LEGEND()
@enduml
```

![tags with sprites and custom legend](https://www.plantuml.com/plantuml/png/dLPTR-Cs47pth-0Pz-00ZfLpcWOewiCvTjhhmRca_cWUXRMubjMZI9MauZEA_lSkgLXqREMZpLF4dPqTxWo3V38Mj2rpqNgNoKIK7DdQsiBy54KQDhqqi-joMHhKYP8MfUqbAe--PJfP6xkEHZ-StWcGTd4pYV0xrJboEen718PCekuLZhhrZkEAFfaoS4S7RnWnqc3MoFDCycWtubGLA0qcfSxi5aX2PZ6nfSR-QKQz9ih1MDIxczJZef7ASoMzbkFYWYP784HL3lMVrMgL9HZDK3-WDX472qim61j_yF5vv2eJRq11KOWi0Pif-JoO5fbWOKta47GGxtMz02S96ZTqgO-jrf3pQx96In1tD5V9EQITDaWbjxagJKo-jRlilIbegpXeAmEnCoDU2aY-nMlmLO4fcJidx22qCeThdxW9Uyn9QQpAKJUI2j0fngbMPN54cwOQKx38ctd1XQ6H54gUsMwYXD83ZJmGpvgH9W61WxDU_-AeAQXnqp9ZjL_rJf6JL6VRgzhWSbWK-xAEVJtafXv6A9Ric8ZvY9Wlzqb3-1eOG_bbIfTBiyzA1ysCLObLfPT9gNYmW8Qe7h9Jar42ZxRWwASeFF4kmgxNKjV8MzL-FvnER-_ZqUtaTkffgRMf50JLJBNnvy_v7h1EJ1M-c5vF9pmNbuGkQryfxu-5r0mE7jF9OsCd97hNDOEyotvxK1Bhvl1UGj-JxDKJKKiUsZp8gPnjZSKylbAbvA2tdUG3WIqcQwkp9PhUdwPzydUBqKzjN8SIwEmXu3rbSVZ4gFONU80kSsz7fkpcZr6NpLLEPNRP-rxFtmN_v2dpUDdHA6A-91uoqdE2OEF7V3hwc-tizmcxw5tii_7b8LF7fzNVZPf-eGzMtRJjFeVpytxezj06ALAPlmJ1loeQwKMmcLMwag5agiPNhD_hloAaB3XORy6Y-cst97P9g2h8RXN1KIMhrVpJQj4IZi8JjhymQ1pRv_dyRXO8GWXzVyZH_oKu3DH_9V4iTSEUmy0DMscLCv2SRTnpCymgHqORZxwChoWzXTAMdP-V_LYf2JnF70vSXx2TYm6nxz-6LB92AwiI9Hw7zI_FFbm-oeuNmS1NX1CANbCVw0xqtzUNFyA52pIlwytNcS0sdjOFB8odqkmp_UMRNFzw_NNSEMbzGidTVpF_0W00 "tags with sprites and custom legend")

### Sample with different boundary tag combinations

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml

' Update the generic boundary style and the "system", "enterprise", "container" boundaries styles too
UpdateBoundaryStyle($bgColor="gold", $fontColor="brown", $borderColor="brown")
' (Re-)Updates the system boundary styles; re-set $bgColor avoids '(no back color)' in legend too
UpdateSystemBoundaryStyle($bgColor="gold", $fontColor="white", $borderColor="white")

Boundary(b, "A Boundary") {
}

Container_Boundary(cb, "A Container Boundary") {
}

System_Boundary(sb, "A System Boundary") {
}

' defines a new border style incl. new border type
AddBoundaryTag("repository", $bgColor="green", $fontColor="white", $borderColor="white", $shadowing="true", $shape = RoundedBoxShape(), $type="GitHub repository")

Boundary(c4Respository, "plantuml-stdlib/C4-PlantUML", $tags="repository") {
  Component(readMe, "README.md", "Markdown")
}

' boundary tags are internally extended with '_boundary' that it uses a different name space
' this enables different element and boundary styles for the same tag name
AddBoundaryTag("v1", $bgColor="lightgreen", $fontColor="green", $borderColor="green")
AddElementTag("v1", $bgColor="lightred", $fontColor="red", $borderColor="red")

Boundary(anotherBoundary, "Another Boundary", $type="BOUNDARY TYPE", $tags="v1") {
  Component(anotherComponent, "Another Component", $techn="COMPONENT TYPE", $tags="v1", $descr="Component and boundary use different tag name spaces that both v1 tags can use different styles")
}

Lay_R(b, cb)
Lay_R(cb, sb)

Lay_D(b, c4Respository)

Lay_R(c4Respository, anotherBoundary)

SHOW_LEGEND()
@enduml
```

![custom border tags](https://www.plantuml.com/plantuml/png/bLH1R_8u4BtdLyn6bKYa0ghKqwwGIW6rXm8Lj5hrX1nxIAm6ExATKhJQ__vvCA5f-Bv3Jp1lPfuVysQuiuuPL-_Aw2-fU5aBXCAvoluz71gs7-JI5NLMMpHSAuVA3RZU3T-buOLrnN1ostykcNAlywSXVlgyGE71pKJlAgsel2Bgg0UlbM0EmHK8EIeqaaEcQoMOEO1rXnA1AN5Cn_PW7UxYQuWz0PhAI8iKaG8cVM_Sj4gqeTc2qpeARzoVQDUKIAwoVA9BRKPnhalXQQwsdkO4PKRl5M6PDWBDDpJrefCLzjF0Qe_QWhIESliF6EnRTD0y1kn3Is6XboWD6UFlm0bEUo0Lb9YZ4Yt1woFf3sJl2-cm8xj1qoXgc9BC3sqCJHYdy5_qVnHDcZ5kpeKyL9up5pr1ubU33Gq1lgZkWS2jvx70GE4UWioJpRHbWpRi3XL6Oo4QbXUM9x71Iblfj2UzXjOm3ABwmJGyQWicz5wgV1GxKpTGXJ225Rs8_k7FDI59wdEaPXG_IFTOPz1IqPuhlrsXRJ9-45N959rGtpfHognz5J5HijoEsh-8nWHmlf7481Dpz4IhsNWwdmrsP7WyP-PTX4sacNuj7V41CpHAXqQniZn0Stombww0tgOfxe4hc0FfeBP7FuJSRj6WSg3O3i5MZ6D4LT82AfQLQ5irMEAEFfaItQM7hJRX9ZmFQIB2IoC_RhuPMCgySBzpCM1T5mEQ4kiiIFaZgS7kcH3I9IIiRILJsXLecfYscf3s2PoNudxvkfYELs_mylOyEnjBOZg6Dgnde4Lxneu4o0irYYVB-VDoCLkyN33JTu6MU-MXiMi6sThoo_UrVBN1_Co_31ytOMyuKvsUO6VOiYTssApeVuDdwIdWFh8-EePJodrR_xHfwXn5Px2-RFsu_7VpD7kOBQP96jsX4lvaVW40 "custom border tags")

### Custom schema definition

If the custom (color) schema is defined via `UpdateElementStyle()` then the legend of existing elements is updated too.

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Context.puml

!$COLOR_A_5 = "#7f3b08"
!$COLOR_A_4 = "#b35806"
!$COLOR_A_3 = "#e08214"
!$COLOR_A_2 = "#fdb863"
!$COLOR_A_1 = "#fee0b6"
!$COLOR_NEUTRAL = "#f7f7f7"
!$COLOR_B_1 = "#d8daeb"
!$COLOR_B_2 = "#b2abd2"
!$COLOR_B_3 = "#8073ac"
!$COLOR_B_4 = "#542788"
!$COLOR_B_5 = "#2d004b"
!$COLOR_REL_LINE = "#8073ac"
!$COLOR_REL_TEXT = "#8073ac"

UpdateElementStyle("person", $bgColor=$COLOR_A_5, $fontColor=$COLOR_NEUTRAL, $borderColor=$COLOR_A_1, $shadowing="true")
UpdateElementStyle("external_person", $bgColor=$COLOR_B_5, $fontColor=$COLOR_NEUTRAL, $borderColor=$COLOR_B_1)
UpdateElementStyle("system", $bgColor=$COLOR_A_4, $fontColor=$COLOR_NEUTRAL, $borderColor=$COLOR_A_2)
UpdateElementStyle("external_system", $bgColor=$COLOR_B_4, $fontColor=$COLOR_NEUTRAL, $borderColor=$COLOR_B_2)
UpdateRelStyle($lineColor=$COLOR_REL_LINE, $textColor=$COLOR_REL_TEXT)

Person(customer, "Personal Banking Customer")
System(banking_system, "Internet Banking System")

System_Ext(mail_system, "E-mail system")
System_Ext(mainframe, "Mainframe Banking System")

Rel(customer, banking_system, "Uses")
Rel_Back(customer, mail_system, "Sends e-mails to")
Rel_Neighbor(banking_system, mail_system, "Sends e-mails")
Rel(banking_system, mainframe, "Uses")

SHOW_LEGEND()
@enduml
```

![custom schema](https://www.plantuml.com/plantuml/png/dL9TRvim57tdLr0MJOcK9eIG1asAr9AXhH9DgdneUqC6tmGKOoBRgEs_dy5ik2rTfIWluNpSUuxjMouG4sLEZAkC9gJ4OAP2dFctyPYXfz4n4saPbnnOKb01L8oI8X-VCfQaNAJZfNlzI10L-uTm3C-Inu0b62sbM7wFpjLWuwgtN8VhJNGNpSo5QNsP7wQnxLaQxjPuF9rvzesEJsiSRC-Pk3hkrFW1nzxDLCSd2WUmOstEAjZlDdUXukRLh-NyneCzZ23MSRKZTb2C7HrNcJnxFaM9ZgiECzUPUvwEgyuEjcrNcxy9mYYyNmKTmnIv2txlNf76_eoHW8103bHinGk1ldK6nWjg3SrUV5mMf62BzgmbU93tqCBjKLJwWc5WRpmJIV0KuU8feyU59LW9rg1pSNNRZ28IVPZ0lo21l8tkTVo52yWxUxeNz7G-AVNXEl-2TNwxRWD4hUgHZ8AcQX_4qFmgP0wDQz_3m30Uw-Fk9oKNHGviQ5eAGSJq4Jt9QpEN3ITlRbltwCUAQMf9ppsjYeBuvr52wMWiKV0i-ZdAIEi9hgjlapVADq9wO2W7ANlu-xzZjgol9N-NQi-1IvbKHJvAJfhqTP8jKCnDgFDmKnIDPmNPCPNd_wxkVzpAskLG9TfKnlRd-bSK1Z-2rVV-mBYLKygS_040 "custom schema")

## Element and Relationship properties

A model can be extended with (a table of) properties that concrete deployments or more detailed concepts can be documented:

* `SetPropertyHeader(col1Name, col2Name, ?col3Name, ?col4Name)`
  The properties table can have up to 4 columns. The default header uses the column names "Name", "Description".
* `WithoutPropertyHeader()`
  If no header is used, then the second column is bold.
* `AddProperty(col1, col2, ?col3, ?col4)`
  (All columns of) a property which will be added to the next element.

Following sample uses all 3 different property definitions (and the aligned deployment node).

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Deployment.puml

' default header Property, Value
AddProperty("Name", "Flash")
AddProperty("Organization", "Zootopia")
AddProperty("Tool", "Internet Explorer 7.0")
Person(personAlias, "Label", "Optional Description (with default property header)")

SetPropertyHeader("Property","Value", "Description")
AddProperty("Prop1", "Value1", "Details1")
AddProperty("Prop2", "Value2", "Details2")
Deployment_Node_L(nodeAlias, "Label", "Optional Type", "Optional Description (with custom property header)") {

  WithoutPropertyHeader()
  AddProperty("PropC1", "ValueC1")
  AddProperty("PropC2", "ValueC2")
  Container(containerAlias, "Label", "Technology", "Optional Description (without property header)")
}

System(systemAlias, "Label", "Optional Description (without properties)")

' starting with v.2.5.0 relationships support properties too
WithoutPropertyHeader()
AddProperty("PropC1", "ValueC1")
AddProperty("PropC2", "ValueC2")
Rel(personAlias, containerAlias, "Label", "Optional Technology", "Optional Description")
@enduml
```

![properties sample](https://www.plantuml.com/plantuml/png/XPBHRzCm4CRVyrSSULagbMIhG4WyRUf089MjWW8IBvKN7us5uxFiCrj0_E_OqRfsNRey-Upx-Ok_xtBkMJWEhSvUA5Fh814QPklVLfKJj-L6SHDkWaTNas4qNDRKLh-KgnlFJJL_zNAfXU6ldnOLtiM-H1aFrvTeDNLjuctIpav0uayHD4E3GgA3fIEBZhifV1CwO7OXvVQeoAz4Y_aKylTQ-2QVF6vUkuqmwezWHIP1FuYOh1A7t8f8f_v7m-WCChoxiveSEdXJdaPuYSwJAMo_N6WbV8GNuWRxMzSswGiDb-Xhf_eT5BSnZWSdzlvJzvOcKJFxWhnzmOV-jCYt-toQzrQJ-fxeuRDJTPQO7evLebaexS-6qDa3Ejj3Pn7TpM1zHHBNYyB4vRZHLMTnn7aTF5CxO1p-PXd0zyXGE0nW4ZjFdZtVMOpbCBAp5ik4pCb4ToPgrjlgYPqLreqXJPlkUIyK1WVuBuwmyunjuVjbEAunHOK-YMKdu5d4hTb08k1tEIjVbwVWK8jqqOCFrfBRlmXCb1rBSZJ7qHG_etxyon-DScTrFDCeV8v6XbR_1m00 "properties sample")

## Version information

C4-PlantUML offers version information like PlantUML with its `%version()` call.

* `C4Version()`: Current C4-PlantUML version (e.g. `2.4.0beta1`).
* `C4VersionDetails()`: (Floating) version details with the current PlantUML and C4-PlantUML version. (It can be referenced via the alias `C4VersionDetailsArea`.)

```plantuml
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml

' existing plantuml version as text
%version()

' new C4-Plantuml version as text 
C4Version()

' new C4-Plantuml version details (incl. PlantUML version) as table
C4VersionDetails()

' version functions used in e.g. footer
footer drawn with PlantUML v. %version() and C4-PlantUML v. C4Version()
@enduml
```

![version sample](https://www.plantuml.com/plantuml/png/ZOynJyCm48Nt_8fZGBG3pjA9gL8OGMA15RdsDJxXdYFVcVJdun2iTc3ebEYzTv_VsulQhEKKkpjY5uj72AgJFFLzjhCPIKCv5C7i4Yko6fTE_HTb5qH3F-mUtw9bVNzzwV5SVO--Yfz33LjYp6PQqDq3u9b4YKUObdmLuHkpK6Am0bflk_i_ORDTyempDFe_QUY6tSSjUOzgAGfibdK6MjlcRt-1zX3n0dnUJrPkunmBEwq_0aNG0p6W6GqSKrBCtVe1d-tCC9E6guSCN9Q1PTzgDlTwo1xPr_O_ "version sample")

## Snippets for Visual Studio Code

Because the PlantUML support inside of Visual Studio Code is excellent with the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml), you can also find VS Code snippets for C4-PlantUML at [.vscode/C4.code-snippets](.vscode/C4.code-snippets).

Project level snippets are now supported in [VSCode 1.28](https://code.visualstudio.com/updates/v1_28#_project-level-snippets).
Just include the `C4.code-snippets` file in the `.vscode` folder of your project.

It is possible to save them directly inside VS Code: [Creating your own snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_creating-your-own-snippets).

![C4-PlantUML Snippets Video](images/vscode_c4plantuml_snippets.gif)

## Live Templates for IntelliJ

### Prerequisites

[Graphviz download](https://graphviz.gitlab.io/download/)  
[PlantUML Integration](https://plugins.jetbrains.com/plugin/7017-plantuml-integration)

### Install

1. Download [IntelliJ live template](intellij/c4_live_template.zip).  
2. Select `File | Manage IDE Settings | Import Settings` from the IntelliJ IDEA menu.
3. Specify the path to the downloaded ZIP file: `c4_live_template.zip`.
4. In the Import Settings dialog, select the Live templates checkbox and click OK.
5. Restart IntelliJ.

### Usage

* Create new PlantUML file (.puml).
* Type `c4_` for displaying artifacts templates for C4-PlantUML
* Live template create correct C4 model artifact with stubbed arguments. 
  * E.g. alias, label, type, technology, description
* Replace stubbed arguments with desired values.

![C4-PlantUML Snippets Video](images/intellij_c4plantum_live_template1.gif)
![C4-PlantUML Snippets Video](images/intellij_c4plantum_live_template2.gif)

## Advanced Samples

The following advanced samples are reproductions with C4-PlantUML from official [C4 model samples](https://c4model.com/#examples) created by [Simon Brown](https://simonbrown.je/).

The core diagram samples from [c4model.com](https://c4model.com/#coreDiagrams) are available [here](samples/C4CoreDiagrams.md).

### techtribes.js

Source: [C4_Container Diagram Sample - techtribesjs.puml](samples/C4_Container%20Diagram%20Sample%20-%20techtribesjs.puml)

![techtribesjs](https://www.plantuml.com/plantuml/png/ZLHDR-Cs4BthLqnzMGTGxTsasm0zhHEdoMwTZqPoWvu4IXpBt52aIb9nZAB_lKDAaQsuWEk39Syy3j-RUUClrZ7Zcah2o66nTaRaQB_RKVI3K8LiECBQkTh-CfqQjfcKmgsRlB5e2gqSAZSfT3Lz5gPOMxUUNlxquuDaoYrl5rDyfJn7Ji7iai1CA3IJccwAFa2Zw5n5vy6j4LPQIhqHgWH9862Amo0jZAKt3NGlI5qmARTKeoTuU46qcFrvlqopzFuXczy_tOrFeWzTQ9PaoMzNwUKDnRhGqzVq9bjSNL_TpIaOHGzeh5RPrQiRCwNLjjADpRpc64Qpjm0iAJ0wwS1ZLfO6I-QGzyW-yXxAAw64TOOveLKF7qJVZaJ9rZgiiWlTACxCTbnyYlS7DQ59dVmT0Nt2Lz-7yGRpZDKrePymXrbTIr64qYCAVMClB8QaDhxdjtzSnf3gYj9mFddr-PcVXmLFpVh6lmZSG8swbXX3UtCCdGDYm1TwKE2xpkaRNJ61bT4LpQuR5tZ2CN11zc4opFTh2XOBfxt88VDvFZOeCvuJZqUKWJCTcZF7ScRHqxlT9hyluFFaSyiseJ9e3_Y59rHOvQHYBMgACFbit_FD6Iyz_5gucoO7WxNkL1nG6w-4H1icGjV-IZ-WdS_8_vobPwTxT2mosWeGYkChsl-IgRJzIzA1EqroWa08PuD4hKezlu3JoUb0P6ZiOv9CPuvULeZSmZYNkWIYxUn9QAxR83fxIB-fENF1RSlsxSqBSEvHLalqJXdr00krqK5qt1KTzYdSrla0j086jbWZRoHoe649p-6VtiH-eTn6k9P2shuHOY_T_hzGjhrbcFGoBUKkw1dKHUIFWnNT6Pzso7ejDsdwa12UqCCzFGuVxkhH8-5CdzwpCUFTw7p3DaRurZhjZzBefz_c5xI2jJOEpiu-_ao51dLshXlKUWyBTXeYzeoq4GRzD9qkjEmkEpt_-EcyevqjUtiS8queTeJzeDo0_rCl_W0N11nfr_-LiwkwSzmrkjxG8DHAcogCTRSpVTlwYGvAxTn9q665N3SEwYQNee12SsptGpXj11wf6cpT5UsNgR52bNxH0xb-sOUblDO5ssQF_J_chjMK-eAADvNy5m00 "techtribesjs")

### Message Bus and Microservices

Source: [C4_Container Diagram Sample - message bus.puml](samples/C4_Container%20Diagram%20Sample%20-%20message%20bus.puml)

![messagebus](https://www.plantuml.com/plantuml/png/ZLLVRzis47_tfxXv0-O0RemEUneGeFvZh2sSnBLizD4uKMU924KA9ENK6_RTTvHibMuKD7c8oUFnz-UEf3uuZzRNfHhy8hLGTKPGU5-vloOJYy-tkVH5dTQEh33Qa_QtmfIJ9sb5uNmncV_vRgrG-ztzQaBVU3sZZ8FxEIUZr6Hlgm3zEzIQzvMy7tn1S31AcMUfSr2S1AWpk5gMrl780FE2CWALEZ569_0bmM2QPKj50M6B-MXOIc5DGlOe1Gt7y9ihiAAxfSmBdqZMc8Jvw8PNqdnkbB5tmxcn-i2goCvKtMmwCCTvyRcGleafojdabhtUjIJWMXOOKK075-1lXZS_AdBUMCmZCHjJXshDpBSUCQfH-dHwJGhZ3vAFZr_tw-KcUNpOF-wsgqyFon67rsITqIDHCsD9TWppRZISmYNS09oSft8_2qBGdaRYFQTSik6JFXXRefT63s_Wtm7mNrVr4LPLd3ojAYL5cypnptX49woi_1YcEgyLsX2UXgwxJeCBBIvHSrb2swM5ofg3LEpkcgqpipyNEwRkkjpIZY6fR3XPCsDy26uBWif8xS4S08KWvu2TTIf0HaQvr1vp1tSG7w6NWaf6OTdxj7PCST_EO5QxmBZ1D9N-_al3Rb6xobZVS7Awr4407KbxzmBMKaXbzP7HpIKMEztKwIdypYsX9mSwE53IKGOPUcp8EZ2eQbiPH-xDzh3Ef8yqJCCyvf__EhbzM6x3S6tDKMQimTWSjNHD8TyzSmW2J2FWW48g7hvTmYBztlGiZVkzO7yfkaR6eqMX2Dx_8S8iySQI-sbZsvlOmnYLdodZoiUSzwVaoogYmqln_w4CZcGTqpL7JQcktz-RWXaKHlJsfaTXVrjuDMeApnfTIpvItRHJ5zK0C3MrFnyzy0LwAF18_A-gI5FMh-2_mM13Qh-87fJsxkzQqSEFs-qwuSHpMhFOSrzt5TVWbUv0A5CUmD2Tj1Z3PtxJ9bV0kvuteDMHaCvSvye4bA-K9aOyaUVThssERd07qcch6x4HQ8FJWnAVqQxcJRDb-n0kPlEpXUite--clqr43DFUiBT3NAJqi7UXNYijzGziyN7iThHSxPx12a_xJH_R5TBbMxPQ_hryMF0tx0Exg4lrFm00 "messagebus")

## Background

[PlantUML](https://plantuml.com/) is an open source project that allows you to create UML diagrams.
Diagrams are defined using a simple and intuitive language.
Images can be generated in PNG, in SVG or in LaTeX format.

PlantUML was created to allow the drawing of UML diagrams, using a simple and human readable text description.
Because it does not prevent you from drawing inconsistent diagrams, it is a drawing tool and not a modeling tool.
It is the most used text-based diagram drawing tool with [extensive support into wikis and forums, text editors and IDEs, use by different programming languages and documentation generators](https://plantuml.com/running).

The [C4 model](https://c4model.com/) for software architecture is an "abstraction-first" approach to diagramming, based upon abstractions that reflect how software architects and developers think about and build software.
The small set of abstractions and diagram types makes the C4 model easy to learn and use.
C4 stands for context, containers, components, and code — a set of hierarchical diagrams that you can use to describe your software architecture at different zoom levels, each useful for different audiences.

The C4 model was created as a way to help software development teams describe and communicate software architecture, both during up-front design sessions and when retrospectively documenting an existing codebase.

More information can be found here:

* [The C4 model for software architecture](https://c4model.com/)
* [REAL WORLD PlantUML - Sample Gallery](https://real-world-plantuml.com/)
* [Visualising and documenting software architecture cheat sheets](https://www.codingthearchitecture.com/2017/04/27/visualising_and_documenting_software_architecture_cheat_sheets.html)
* [PlantUML and Structurizr - Create models not diagrams](https://www.codingthearchitecture.com/2016/12/08/plantuml_and_structurizr.html)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
