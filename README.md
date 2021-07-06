# Extended C4-PlantUML

This branch is basically https://github.com/plantuml-stdlib/C4-PlantUML/tree/master
extended with my open PRs.

**Old master branch**

The [old master branch](https://github.com/kirchsth/C4-PlantUML/blob/master/README.md) is still working. But it will not be updated anymore.

# C4-PlantUML

![Container diagram for Internet Banking System](https://www.plantuml.com/plantuml/png/hLPDR-Cs4BtxLqozUt009KQntKk10ElOQZSBEtOjfzkRCQB64X6A54Wg7oZwtpja52jojjW2xSKGXpFlFJqEH_xaF5hVrchqWzH2jGL1vNtZVfvEBJvSbD9NRTuwii9eJzfV25DFxwGLbVFLTFxJ-KQXzhUhvPGUUR-WWeFxEIUZr6GlcW0zoZwll-utwJPRt-pNjxlbzKqwEHlDYY9LL3Fg3il9E4TnnmWWNeh72Rm_y69kbB6NxzDbkaflTljVrlmpNo_NMzxFo-VTyRiF7pukPXz3ZQkmeSjKbfNF92lAmdfo5Wctf28PkYSjGh9dtHt1RBjbcI_8YYNyuqRcdnHTBj1LL2obFaKFuDF_Xy9utrEClFIAu6Wl519BYpKSZ8LhxSbgyd25-axg4h8dvwaUZJPadT4JqJflQh89p8zFuncyXC4Sm5S4ELSdy21z1KqiH1LZW4AOLditPXtFqFih3XHedoRYHyOw5J0-Wpz70D3hdJnGliUcuUIlbCEiQPGKwANHOmvzmNjC86ji4B_wVHvY2rBodcL4QSvphe2k5G5r4SD7tlpbnJSp5ZbaTWqoNCRRYiutM59WVs7DX9MDJs2corQX3U6DDVUo80UerBTP3gqMGJegwP_06tOo6kdWNc8eaHRuVI6tvi6HVQEeDhbKrDcn2ekZflcx1Fx06jc9eHPGifQU2d1jxiZpcVrhRUwDk6S1KD2z57GgRv5F2lIOewDm3DrZK9FzjeJ1sXlBsiAG04kbTDx68mMfkIth-9n05UyAOEih49OAqbwYSabeAt8Eb2bvGLvSl36g6mpib0mTkxd-TkCi3AVPlcxWt7SS2gOmSBojMBhBjyE8LVrrxFlqqK-eHgdsBWQOAJrVyRgxSu5wLn78o8eALb9Ouyp1G_eeAjGbmNCbmxx2xCJrg8of3nPhEhdKlU-nFxis41o03kEr-u2vQNtV0ydnBYVWBMg7qOhU_z6MrAjvqT_QMqSkS7_UxJOP9mxpN8FVpUcwleVhwFOtn0CxD_sCY73z1EYGOd3G4KV2E70J-C9VcMaaxuypRdK8lOB_1hI_uk9UTdzRXg1RmiB1mPew3gm7Apqvy2OGTJoBgpb37Z5VkNNIP1d3Eg3p48qOlP1XFmuqdDQrZlkZfyzMkmq33SvWK7xIbRrF_MUEnzLgUUfLlytmp_y1bkclwSs2l_sV6BsjrTy0 "Container diagram for Internet Banking System")

C4-PlantUML combines the benefits of [PlantUML](https://plantuml.com/) and the [C4 model](https://c4model.com/) for providing a simple way of describing and communicate software architectures – especially during up-front design sessions – with an intuitive language using open source and platform independent tools.

C4-PlantUML includes macros, stereotypes, and other goodies (like VSCode Snippets) for creating C4 diagrams with PlantUML.

* [Getting Started](#getting-started)
* [Supported Diagram Types](#supported-diagram-types)
* [Snippets for Visual Studio Code](#snippets-for-visual-studio-code)
* [Layout Options](#layout-options)
* [Samples](#advanced-samples)
* [Background](#background)
* [License](#license)

## Getting Started

At the top of your C4 PlantUML `.puml` file, you need to include the `C4_Context.puml`, `C4_Container.puml` or `C4_Component.puml` file found in the `root` of this repo.

To be independent of any internet connectivity, you can also download the files found in the `root` and activate the local conversion with additional command line argument `-DRELATIVE_INCLUDE="."` (that the local files are included)

```csharp
java -jar plantuml.jar -DRELATIVE_INCLUDE="."  ...
```

If you want to use the always up-to-date version in this repo, use the following:

```csharp
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml
```

Now let's create a C4 Container diagram:

\(If you don't want run PlantUML locally you can use e.g. the [PlantUML Web Server](https://www.plantuml.com/plantuml/uml/ZOxDIWGn48JlUOeufn5qSjcJfvNHsugBFsV99iqcsEc4T0VTjpSCE2AYUAeAgVwgjYosIakevytBBK824bPdaHms3pg85BuofjgtwHWbj4DZg2wJzDpaSZAliRh04ioykToZ9Nc-snbux_yUlEdGkOTj9AXJwJLAxQ5ofh4iSetHyeKUTlO0E7HpNoHcigXlW5sDosiuLojaT9_kn-aJk40Py_7q1-Znn09fv4N-swuU0ByFNbVyZlYQqmbR8DyIVW00) too.)

After you have included `C4_Container.puml` you can use the defined macro definitions for the C4 elements: `Person`, `Person_Ext`, `System`, `System_Ext`, `Container`, `Relationship`, `Boundary`, and `System_Boundary`

```csharp
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

```csharp
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

```csharp
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

```csharp
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

Elements and relations can be decorated with tags and explained via a calculated legend, for example:

```csharp
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

Diagram types 

* System Context & System Landscape diagrams
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Context.puml`
  * Macros: 
    * `Person(alias, label, ?description, ?sprite, ?tags, $link)`
    * `Person_Ext`
    * `System(alias, label, ?description, ?sprite, ?tags, $link)`
    * `SystemDb`
    * `SystemQueue`
    * `System_Ext`
    * `SystemDb_Ext`
    * `SystemQueue_Ext`
    * `Boundary(alias, label, ?type, ?tags, $link)`
    * `Enterprise_Boundary(alias, label, ?tags, $link)`
    * `System_Boundary` 
* Container diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Container.puml`
  * Additional Macros: 
    * `Container(alias, label, technology, ?description, ?sprite, ?tags, $link)`
    * `ContainerDb`
    * `ContainerQueue`
    * `Container_Ext`
    * `ContainerDb_Ext`
    * `ContainerQueue_Ext`
    * `Container_Boundary(alias, label, ?tags, $link)`
* Component diagram
  * Import: `!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml`
  * Additional Macros: 
    * `Component(alias, label, technology, ?description, ?sprite, ?tags, $link)`
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
    * `Deployment_Node(alias, label, ?type, ?description, ?sprite, ?tags, $link)`
    * `Node(alias, label, ?type, ?description, ?sprite, ?tags, $link)`: short name of Deployment_Node()
    * `Node_L(alias, label, ?type, ?description, ?sprite, ?tags, $link)`: left aligned Node()
    * `Node_R(alias, label, ?type, ?description, ?sprite, ?tags, $link)`: right aligned Node()

Take a look at each of the [C4 Model Diagram Samples](samples/C4CoreDiagrams.md).

## Relationship Types

* `Rel(from, to, label, ?technology, ?description, ?sprite, ?tags, $link)`
* `BiRel` (bidirectional relationship)

You can force the direction of a relationship by using:

* `Rel_U`, `Rel_Up`
* `Rel_D`, `Rel_Down`
* `Rel_L`, `Rel_Left`
* `Rel_R`, `Rel_Right`

Relationship specific sprites are typically smaller and therefore following options are possible:
* use smaller icons (like the $triangle in the following sample)
* use an additional scale factor (direct as part of the argument, or via a variable)
* if sprite argument starts with `&` an OpenIconic name can be used too (details see https://useiconic.com/open)

```csharp
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

![Relation with sprite or OpenIconic](https://www.plantuml.com/plantuml/png/bLJVQzim47xtNt4reMl1ZTDa6sGGAEimZ7MqjFIvAD8b5f4bJvANbR7_VVfXDSaQ3telydsdk--xu-GhOucsNIEo4owfw1X2RMrhFfMb9jlncjkwMtO6DLNIehHZgffompMjZQtBw_SNTu98-_ZzfiHVBiwGEV3fsbrs_hZrXRCxr4R9Cr-bWFpH7VdvFdZPet1vY4yJFZt4PmcVEJnxU3OMcpCJ3XU9le-y0wbqGmIOLdEB1eX6i4h1agyXkqVnTDEBIcnShbo6oTqdLPtcgFtdS1KN7KLuaRT1u3GI6qe4ieCKjGcKztkKiq7A8_cttuwm5U7YOZB-47cfQfPSOfy8HB8enGa60XAtVIGx6VLNsSDWnJVeJSM65V_3vzJwCRL8kH-jcwz0_P9DYOGbUawMHGn6LdCYrmBXTmRE9ZlR-TMXNtsk_kTNy_cy6lQhZzwg8R-QHQk6_6IJLth_fCd6vNzPNQKPwZ1Q_mRz6GQJnbA0u1i4MoD4F8raVp4I5lU1hz8gX7TkOCjj3QT5GXckk4G316vRb5-fafmM3hM42mC6Tty3fvM7SFW3A7Ux35ryIVlHFsIDFpeqDdH1pBEaqA0nP8qU69J3xL4fiU5Jb3zHECeBAfH1jciN5f2_YfvdLoXPruY_ "Relation with sprite or OpenIconic")

In rare cases, you can force the layout of objects which have no relationships by using:

* `Lay_U(from, to)`
* `Lay_D(from, to)`
* `Lay_L(from, to)`
* `Lay_R(from, to)`

In following sample a person uses different systems, and group of persons which have no relations

```csharp
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

![Relation versus Layout](https://www.plantuml.com/plantuml/png/LSrHQxCm5CRnUpz5trufl5EgNksgcmeRE2PQORkIc1ocJ6D9JbZxxNTY6R5tv_yZF3bgP0hDF7d_Hiad8s0t89xrOnGfzXD-ZJYOtcXGV9484aE-pD7tgFYWSOYozA6QcCJshOpWWY052C8keyTibA32ivr-USsBhZaLTV5--gmAF_2y2fHUfC_-x_PF--0lUyfdbvmoSoaeSvT0ML1w9RjshPtgW_MkxSrlTsvlSRjBUuFx_4837pJGN3N2xEi3TNFOG6mXta1Y8Tb0QY4by6gOkjPEhZD6WoQrMAyOtsE-OdAFvOgfmoD8OURf5m00 "Relation versus Layout")

(In combination with [SHOW_FLOATING_LEGEND()](LayoutOptions.md#show_floating_legend)) a greater distance between an element and the
e.g. floating legend could be required that all e.g. corners of the drawing area can be reached.

* `Lay_Distance(from, to, ?distance)`: Sets the distance between `from` and `to` with down alignment (Lay_Distance(from,to,0) equals Lay_D(from, to)). The default alias of the floating legend is LEGEND().

In following sample the floating legend should be in the left bottom corner of the drawing are.
(The normal SHOW_LEGEND() call requires no extra Lay_Distance() call and the legend is automatically drawn below the diagram on the right side)

```
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

## Layout Options

C4-PlantUML also comes with some layout options to make it easy and reusable to create nice and useful diagrams:

* [LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT()](LayoutOptions.md#layout_top_down-or-layout_left_right)
* [LAYOUT_WITH_LEGEND() or SHOW_LEGEND(?hideStereotype)](LayoutOptions.md#layout_with_legend-or-show_legend)
* [SHOW_FLOATING_LEGEND(?alias, ?hideStereotype) and LEGEND()](LayoutOptions.md#show_floating_legendalias-hidestereotype-and-legend)
* [LAYOUT_AS_SKETCH()](LayoutOptions.md#layout_as_sketch)
* [HIDE_STEREOTYPE()](LayoutOptions.md#hide_stereotype)

C4-PlantUML also comes with some person sprite/portrait options:

* [HIDE_PERSON_SPRITE()](LayoutOptions.md#hide_person_sprite)
* [SHOW_PERSON_SPRITE(?sprite)](LayoutOptions.md#show_person_sprite)
* [SHOW_PERSON_PORTRAIT()](LayoutOptions.md#show_person_portrait)
* [SHOW_PERSON_OUTLINE()](LayoutOptions.md#show_person_outline) (requires PlantUML version >= 1.2021.4)

## Custom tags/stereotypes support and skinparam updates

Additional tags/stereotypes can be added to the existing element stereotypes (component, ...) and highlight,... specific aspects:

* `AddElementTag(tagStereo, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape)`:
  Introduces a new element tag. The styles of the tagged elements are updated and the tag is displayed in the calculated legend.
* `AddRelTag(tagStereo, ?textColor, ?lineColor, ?lineStyle)`:
  Introduces a new relation tag. The styles of the tagged relations are updated and the tag is displayed in the calculated legend.
* `UpdateElementStyle(elementName, ?bgColor, ?fontColor, ?borderColor, ?shadowing, ?shape)`:
  This call updates the default style of the elements (component, ...) and creates no additional legend entry.
* `UpdateRelStyle(textColor, lineColor)`:
  This call updates the default relationship colors and creates no additional legend entry.
* `RoundedBoxShape()`: This call returns the name of the rounded box shape and can be used as ?shape argument.
* `EightSidedShape()`: This call returns the name of the eight sided shape and can be used as ?shape argument.
* `DashedLine()`: This call returns the name of the dashed line and can be used as ?lineStyle argument.
* `DottedLine()`: This call returns the name of the dotted line and can be used as ?lineStyle argument.
* `BoldLine()`: This call returns the name of the bold line and can be used as ?lineStyle argument.

Each element can be extended with one or multiple custom tags via the keyword argument `$tags="..."`, like `Container(spaAdmin, "Admin SPA", $tags="v1.1")`.
Multiple tags can be combined with `+`, like `Container(api, "API", $tags="v1.0+v1.1")`.

**Comments**

* `SHOW_LEGEND()` supports the customized stereotypes
      (`LAYOUT_WITH_LEGEND()` cannot be used, if the custom tags/stereotypes should be displayed in the legend).
* `SHOW_LEGEND()` has to be last line in diagram.
* Don't use space between `$tags` and `=` (PlantUML does not support it).
* Don't use `,` as part of the tag names (PlantUML does not support it in combination with keyword arguments).
* If 2 tags defines the same skinparam, the first definition is used.
* If specific skinparams have to be merged (e.g. 2 tags change the font color) an additional combined tag has to be defined. Use `&` as part of combined tag names.

* Colors of relationship tags cannot be automatically merged (PlantUML does not support it).
  If one tag modifies the line color and the other the text color, an additional combined tag has to be defined and used.

```csharp
@startuml
!include https://raw.githubusercontent.com/kirchsth/C4-PlantUML/extended/C4_Component.puml

UpdateElementStyle(person, $fontColor="green")
AddElementTag("v1.0", $fontColor="#d73027", $borderColor="#d73027")
AddElementTag("v1.1", $fontColor="#ffffbf", $borderColor="#ffffbf")
AddElementTag("v1.0&v1.1", $fontColor="#fdae61", $borderColor="#fdae61")
AddElementTag("fallback", $bgColor="#444444")

AddElementTag("micro service", $shape=EightSidedShape())
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

Container(services, "Services", "techn", $tags="micro service")
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

![merged tags](https://www.plantuml.com/plantuml/png/jLHHRzCm47xlhp01JQqwsZLCJ4AQjD4LXZHWMZVnE5sJIsBcs97jTEFVSuxhaZQ1YOVbnVRTTz-TFz_bp5ZGjYx5u1MNYQXJP8MrbVamdMfudEJS5lMgDgWJ9IrAEqbKENtWEYcCBQRpuxVN0gIz-ternIVofvYIyNwkoaf91wySzU2kIi7YGc19jgNz9N1OeJPA7h8t6H7FbL3wDCereen6W_CqtM1l8Hz6wzdaADf5lavFtXt59ywwKZf5lMllvPZjSsJqhR8kXxVtrt7GIvG2lfzrYRozIvI142j87fg8FA2Fcu_G-_2I9renWthD4tGnfe0AJnSyB-oIa-HBTnwEEdcCLHhoLiYDgYNXFwgd41BUvWQ5VvULeC8EMRCqXEJnP3v_SqsBJ-7o6jEe3nSxdE0Idy7D3a90bxYNOZ0dvO6iUcWgE6JHyleyeWLaNWlGRdjR82i9mhYqg3D8aDa2BBDaJsfIfKJjVP1OmnwvBTYQ0mkDPY4tfxxjHhlfpjEIIyhGhAm_CpWVDrO3oV-_9KXyPBx5McNCTig0YhiAhh-uX3zX3Mwz19aAD0o4O3Il13I62PNpX0tTO4-spAmPLCELDADMbj3ROxSRkzt-tMElTVnYOe_3NFIg7hTbZrzUzr1CqA9TakzOumJPR5qH5fD2RWdsnhPzfOmBNFhPfB1FT6B67tjeWeSgeD7nFUzRuCxulCqFc_pUxTNw1-R-ofDidjJFVmTqqw8Akx_06_o5xykMD3Mb3kTP8x8jk649wTgwtSPFDC-pnC-mn5kMFmIxMg-KBRRiZUYqz9DsVr3ZO1ctyWsMbzz_t5yjFY--NGmp40P7WpEKQLsAtm00 "merged tags")

**Custom schema definition**

If the custom (color) schema is defined via `UpdateElementStyle()` then the legend of existing elements is updated too.

```csharp
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
UpdateRelStyle($lineColor=$COLOR_REL_LINE, &textColor=$COLOR_REL_TEXT)

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

## Element properties

A model can be extended with (a table of) properties that concrete deployments or more detailed concepts can be documented:

* `SetPropertyHeader(col1Name, col2Name, ?col3Name, ?col4Name)`:
  The properties table can have up to 4 columns. The default header uses the column names "Name", "Description".
* `WithoutPropertyHeader()`
  If no header is used, then the second column is bold.
* `AddProperty(col1, col2, ?col3, `?col4)`
  (All columns of) a property which will be added to the next element.

Following sample uses all 3 different property definitions (and the aligned deployment node).

```csharp
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

Rel(personAlias, containerAlias, "Label", "Optional Technology")
@enduml
```

![properties sample](https://www.plantuml.com/plantuml/png/ZPB1RXCn48Rl-nHcBsoaaAKH4XAdLYa8fD16443Y4hdh8RRmUYnxh7P1l3jZg-csQG8zUUpvycU-jKyZoK2fjzKpupgR50XDvEERjWtoUhOrfDDLYX0wT0IEPXtsxKyJEXr9jujNBrPMElhoSTd23VSLA3xSd8EtEFIPzpcxUYuK_939aj0W5GIn2kWXq30LNwLDK9qfjJjgwWlPGpqLzJihewud3vkNOIkT-IN9eClGTqH2R-G-jqQqkV_14GG79DxUy501WdWzUydm2a94r_Yod5aZ8yDBUGNbLvS-vqihpY5smPITQAuDwJiJV_jNjqeJpgm-0-qcU5zEctgthwTrKStfzqBtnyxLIMOAd2kcIHeRJmwXypjqVW-TCphUmUO25MoMZUFbkEXwyF0Vyov5mlw0kFXTLK9yOmRJ_WUOSEVHs8jHaSl3oAZ6PKOMwDZESMQtgnxfhA7J3YrkXt-xO3fuWN_u2eT8q3UnBFlvJqiq4Cjh-0JsuViQvpwQEmfmmYaubNhx5m00 "properties sample")

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
4. Restart IntelliJ.

### Usage

* Create new PlantUML file (.puml).
* Type `c4_` for displaying artifacts templates for C4-PlantUML
* Live template create correct C4 model artifact with stubbed arguments. 
    * E.g. alias, label, type, technology, description
* Replace stubbed arguments with desired values.

![C4-PlantUML Snippets Video](images/intellij_c4plantum_live_template1.gif)
![C4-PlantUML Snippets Video](images/intellij_c4plantum_live_template2.gif)

## Layout Options

C4-PlantUML also comes with some layout options to make it easy and reuseable to create nice and useful diagrams:

* [LAYOUT_TOP_DOWN or LAYOUT_LEFT_RIGHT](LayoutOptions.md#layout_top_down-or-layout_left_right)
* [LAYOUT_WITH_LEGEND](LayoutOptions.md#layout_with_legend)
* [LAYOUT_AS_SKETCH](LayoutOptions.md#layout_as_sketch)

## Advanced Samples

The following advanced samples are reproductions with C4-PlantUML from official [C4 model samples](https://c4model.com/#examples) created by [Simon Brown](https://simonbrown.je/).

The core diagram samples from [c4model.com](https://c4model.com/#coreDiagrams) are available [here](samples/C4CoreDiagrams.md).

### techtribes.js

Source: [C4_Container Diagram Sample - techtribesjs.puml](samples/C4_Container%20Diagram%20Sample%20-%20techtribesjs.puml)

![techtribesjs](https://www.plantuml.com/plantuml/png/ZLHDR-Cs4BthLqnzMGTGxTsasm0zhHEdoMwTZqPoWvu4IXpBt52aIb9nZAB_lKDAaQsuWEk39Syy3j-RUUClrZ7Zcah2o66nTaRaQB_RKVI3K8LiECBQkTh-CfqQjfcKmgsRlB5e2gqSAZSfT3Lz5gPOMxUUNlxquuDaoYrl5rDyfJn7Ji7iai1CA3IJccwAFa2Zw5n5vy6j4LPQIhqHgWH9862Amo0jZAKt3NGlI5qmARTKeoTuU46qcFrvlqopzFuXczy_tOrFeWzTQ9PaoMzNwUKDnRhGqzVq9bjSNL_TpIaOHGzeh5RPrQiRCwNLjjADpRpc64Qpjm0iAJ0wwS1ZLfO6I-QGzyW-yXxAAw64TOOveLKF7qJVZaJ9rZgiiWlTACxCTbnyYlS7DQ59dVmT0Nt2Lz-7yGRpZDKrePymXrbTIr64qYCAVMClB8QaDhxdjtzSnf3gYj9mFddr-PcVXmLFpVh6lmZSG8swbXX3UtCCdGDYm1TwKE2xpkaRNJ61bT4LpQuR5tZ2CN11zc4opFTh2XOBfxt88VDvFZOeCvuJZqUKWJCTcZF7ScRHqxlT9hyluFFaSyiseJ9e3_Y59rHOvQHYBMgACFbit_FD6Iyz_5gucoO7WxNkL1nG6w-4H1icGjV-IZ-WdS_8_vobPwTxT2mosWeGYkChsl-IgRJzIzA1EqroWa08PuD4hKezlu3JoUb0P6ZiOv9CPuvULeZSmZYNkWIYxUn9QAxR83fxIB-fENF1RSlsxSqBSEvHLalqJXdr00krqK5qt1KTzYdSrla0j086jbWZRoHoe649p-6VtiH-eTn6k9P2shuHOY_T_hzGjhrbcFGoBUKkw1dKHUIFWnNT6Pzso7ejDsdwa12UqCCzFGuVxkhH8-5CdzwpCUFTw7p3DaRurZhjZzBefz_c5xI2jJOEpiu-_ao51dLshXlKUWyBTXeYzeoq4GRzD9qkjEmkEpt_-EcyevqjUtiS8queTeJzeDo0_rCl_W0N11nfr_-LiwkwSzmrkjxG8DHAcogCTRSpVTlwYGvAxTn9q665N3SEwYQNee12SsptGpXj11wf6cpT5UsNgR52bNxH0xb-sOUblDO5ssQF_J_chjMK-eAADvNy5m00 "techtribesjs")


### Message Bus and Microservices

Source: [C4_Container Diagram Sample - message bus.puml](samples/C4_Container%20Diagram%20Sample%20-%20message%20bus.puml)

![messagebus](https://www.plantuml.com/plantuml/png/bLNVRzis47xtNt7J1im1t1WTzZGWGFt3M5iuYMlPwADneiuI4PeKICgfD-n_tr6oLSPLjoOFCNcy-xxlVf1wvpnQNnyK90To3WlAQfSCVf9Qg3edABslt1_ZiSNdsqBwikPZii9eJzhV2dCOFqahIkVByUptDok5sc_lbsFwmkSvvMpSpTWPfIPxMp7Fu5UeDSSTE1vyIR0tIfbdgGjGx0IeStXnBAtZbG7c1MK4AdLYZ4xWjmI3IPul50M43HR3v225DS2gZr9GCe9VN8aLtIraKVfKiiWqx8StV98LCwEClKjcnkezoo8xLNKJj6UIy-5pAJqbDzSypXkBHSImDdMemTHywM5G3VtJwJ_m1-dxny-xrMATFZxi7hURvOU7nP3DAxBEwA6ecV50TWIpRfLCu69k04xEqs4t3KBGdeRYBRjSlE63tXjxG2-DJcxWxm7mNrVB8LPLx3ofAYL5wypsZtX49woi_0WckgWLsYJGXrwwJeCBZJkWne92CwM5ofgzL9pT5TibOdVkKqoTjgOBxGZIoePvcHhZWt5J4bH6QWzc3oW4EGUSMQS2P9GebzfZuU0EhWRZMj7vEknuu9dZljt1j7Q1SerP9ltzfuRUedQLiRuXPNUfWm8walRk6rXBmPNbHvckBxOurNMTdSBlp19wSg132aewoY57ZmrP1mPLRIlZoFruVbZdqaSY9c4V2vZzFBvzM6p2ScNDKUOimjW2jNHDATyyima2JADWZq8gNhv2mppxslSyYri-HuyPkaR7eqMX2Dx-9i8kzSQI-z_UjfUnXp5g05F6jOyvxq_ffsL4XvVo_qKv7CawfckcJQckur_RWZcKHlHsfqTXVr_uDEeAxnfT2nwgRjkfYse0c9dQduSFV8aUIZmI_wigqfJtA_XdC5YJsisZDwMz_jjMTF9-ircbx7XsQmvxhkosoj5_fpiGobG4C7GdBKRmaP-ryGlWRSypqEf8IUUkoye4bC-KfKOyaUVexmL7TxW3wRJLZTW8jC7fGObdjAjvqspPleNpwUoSmijNe-Uk_w286AQzOg-2Q31ws3jJRoejzHLRD8vTn8MhYHaiyRHRzx6zGBfypfQBFnSFS_wClUCimkVwNm00 "messagebus")


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
