



# [ThreeDee](https://threedee.de) UE4 Style Guide()

*Created on basis of the [Gamemakin UE4 Style Guide](https://github.com/Allar/ue5-style-guide)*

## Linter and Style Guide Documentation

More technical documentation regarding Linter and the Style Guide can be found at our [ReadTheDocs](https://ue4-style-guide.readthedocs.io/en/latest/) page.

## Linking To This Document

Every section of this style guide is numbered for both easy reference and easy linking. You can link to any section directly by simply append a hash tag and the section number to the end of https://threedeevr.de/style
For example, if you want to send someone to the first principle of this style guide you would append `#0.1`, resulting in https://threedeevr.de/style#0.1.

## Applicability

The contents of this style guide focus primarily on general project structure and uassets. See the [Blueprints](#bp) section for more context. For C++ coding please refer to [Epic's Coding Standard](https://docs.unrealengine.com/5.0/en-US/epic-cplusplus-coding-standardblueprint-debugging-in-unreal-engine/).

## Table of contents
- [Important Terminology](#important-terminology)
  - [Levels/Maps](#terms-level-map)
  - [Identifiers](#terms-identifiers)
  - [Cases](#terms-cases)
  - [Variables / Properties](#terms-var-prop)
    - [Property](#terms-property)
    - [Variable](#terms-variable)
- [0. Principles](#0)
  - [0.1 If your UE4 project already has a style guide, you should follow it](#0.1)
  - [0.2 All structure, assets, and code in any Unreal Engine 4 project should look like a single person created it, no matter how many people contributed](#0.2)
  - [0.3 Friends do not let friends have bad style](#0.3)
  - [0.4 A team without a style guide is no team of mine](#0.4)
  - [0.5 Don't Break The Law](#0.5)
- [00. Globally Enforced Opinions](#00)
  - [00.1 Forbidden Characters](#00.1)
    - [Identifiers](#identifiers)
- [1. Asset Naming Conventions](#anc)
  - [1.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`](#base-asset-name)
    - [1.1 Examples](#1.1-examples)
  - [1.2 Asset Name Modifiers](#asset-name-modifiers)
    - [1.2.1 Most Common](#anc-common)
    - [1.2.2 Animations](#anc-animations)
  - [1.2.3 Artificial Intelligence](#anc-ai)
  - [1.2.4 Blueprints](#anc-bp)
    - [1.2.4.1 Core Blueprints](#anc-core-blueprints)
  - [1.2.5 Materials](#anc-materials)
  - [1.2.6 Textures](#anc-textures)
    - [1.2.6.1 Texture Packing](#anc-textures-packing)
  - [1.2.7 Miscellaneous](#anc-misc)
  - [1.2.8 Paper 2D](#anc-paper2d)
  - [1.2.9 Physics](#anc-physics)
  - [1.2.10 Sounds](#anc-sounds)
  - [1.2.11 User Interface](#anc-ui)
  - [1.2.12 Effects](#anc-effects)
- [2. Content Directory Structure](#structure)
  - [2e1 Example Project Content Structure](#2e1)
  - [2.1 Folder Names](#structure-folder-names)
    - [2.1.1 Always Use PascalCase](#2.1.1)
    - [2.1.2 Never Use Spaces](#2.1.2)
    - [2.1.3 Never Use Unicode Characters And Other Symbols](#2.1.3)
  - [2.2 Use A Top Level Folder For Project Specific Assets](#structure-top-level)
    - [2.2.1 No Global Assets](#2.2.1)
    - [2.2.2 Reduce Migration Conflicts](#2.2.2)
      - [2.2.2e1 Master Material Example](#2.2.2e1)
    - [2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free](#2.2.3)
    - [2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained](#2.2.4)
  - [2.3 Only Use Developers Folder For Strictly Local Files](#structure-developers)
  - [2.4 All Map<sup>*</sup> Files Belong In A Folder Called Maps](#structure-maps)
  - [2.5 Use A `Core` Folder For Critical Blueprints And Other Assets](#structure-core)
  - [2.6 Do Not Create Folders Called `Assets` or `AssetTypes`](#structure-assettypes)
    - [2.6.1 Creating a folder named `Assets` is redundant](#2.6.1)
    - [2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant](#2.6.2)
  - [2.7 Very Large Asset Sets Get Their Own Folder Layout](#structure-large-sets)
  - [2.8 `MaterialLibrary`](#structure-material-library)
  - [2.9 No Empty Folders](#structure-no-empty-folders)
- [3. Blueprints](#bp)
  - [3.1 Compiling](#bp-compiling)
  - [3.2 Variables](#bp-vars)
    - [3.2.1 Naming](#bp-var-naming)
      - [3.2.1.1 Nouns](#bp-var-naming-nouns)
      - [3.2.1.2 PascalCase](#bp-var-naming-case)
        - [3.2.1.2e Examples](#3.2.1.2e)
      - [3.2.1.3 Boolean `b` Prefix](#bp-var-bool-prefix)
      - [3.2.1.4 Boolean Names](#bp-var-bool-names)
        - [3.2.1.4.1 General And Independent State Information](#3.2.1.4.1)
        - [3.2.1.4.2 Complex States](#3.2.1.4.2)
      - [3.2.1.5 Considered Context](#bp-vars-naming-context)
        - [3.2.1.5e Examples](#3.2.1.5e)
      - [3.2.1.6 Do _Not_ Include Atomic Type Names](#bp-vars-naming-atomic)
      - [3.2.1.7 Do Include Non-Atomic Type Names](#bp-vars-naming-complex)
      - [3.2.1.8 Arrays](#bp-vars-naming-arrays)
    - [3.2.2 Editable Variables](#bp-vars-editable)
      - [3.2.2.1 Tooltips](#bp-vars-editable-tooltips)
      - [3.2.2.2 Slider And Value Ranges](#bp-vars-editable-ranges)
    - [3.2.3 Categories](#bp-vars-categories)
    - [3.2.4 Variable Access Level](#bp-vars-access)
      - [3.2.4.1 Private Variables](#bp-vars-access-private)
      - [3.2.4.2 Components](#bp-vars-access-components)
    - [3.2.5 Advanced Display](#bp-vars-advanced)
    - [3.2.6 Transient Variables](#bp-vars-transient)
    - [3.2.8 Config Variables](#bp-vars-config)
  - [3.3 Functions, Events, and Event Dispatchers](#bp-functions)
    - [3.3.1 Function Naming](#bp-funcs-naming)
    - [3.3.1.0 Always Use PascalCase](#bp-funcs-naming-case)
    - [3.3.1.1 All Functions Should Be Verbs](#bp-funcs-naming-verbs)
    - [3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`](#bp-funcs-naming-onrep)
    - [3.3.1.3 Info Functions Returning Bool Should Ask Questions](#bp-funcs-naming-bool)
    - [3.3.1.4 Event Handlers and Dispatchers Should Start With `On`](#bp-funcs-naming-eventhandlers)
    - [3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target](#bp-funcs-naming-rpcs)
    - [3.3.2 All Functions Must Have Return Nodes](#bp-funcs-return)
    - [3.3.3 No Function Should Have More Than 50 Nodes](#bp-graphs-funcs-node-limit)
    - [3.3.4 All Public Functions Should Have A Description](#bp-graphs-funcs-description)
    - [3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name](#bp-graphs-funcs-plugin-category)
  - [3.4 Blueprint Graphs](#bp-graphs)
    - [3.4.1 Electronic Nodes](#bp-graphs-electronic-nodes)
    - [3.4.2 No Spaghetti](#bp-graphs-spaghetti)
    - [3.4.3 Align Wires Not Nodes](#bp-graphs-align-wires)
    - [3.4.4 White Exec Lines Are Top Priority](#bp-graphs-exec-first-class)
    - [3.4.5 Graphs Should Be Reasonably Commented](#bp-graphs-block-comments)
    - [3.4.6 Graphs Should Handle Casting Errors Where Appropriate](#bp-graphs-cast-error-handling)
    - [3.4.7 Graphs Should Not Have Any Dangling / Loose / Dead Nodes](#bp-graphs-dangling-nodes)
- [4. Asset Creation](#4)
  - [4.1 Static Meshes](#assets-sm)
    - [4.1.1 Static Mesh UVs](#assets-sm-uvs)
      - [4.1.1.1 All Meshes Must Have UVs](#assets-sm-uvs-no-missing)
      - [4.1.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps](#assets-sm-uvs-no-overlapping)
      - [4.1.1.3 All Static Meshes Must Have Their Light Map Resolution Specified Deliberately](#assets-sm-uvs-lightmap-resolution-specified)
      - [4.1.1.4 All Lightmap Island Boundaries Should be snapped to Pixel](#assets-sm-uvs-lightmap-boundaries-snapped)
    - [4.1.2 LODs Should Be Set Up Correctly](#assets-sm-lods)
    - [4.1.3 Modular Socketless Assets Should Snap To The Grid Cleanly](#assets-sm-modular-snapping)
    - [4.1.4 All Meshes Must Have Collision](#assets-sm-collision)
    - [4.1.5 All Meshes Should Be Scaled Correctly](#assets-sm-scaled)
    - [4.1.6 Asset pivots and sockets should be placed according to the asset's final usecase](#assets-sm-pivot)
    - [4.1.7 Use the correct import settings for static meshes](#assets-sm-import)
  - [4.2 VFX](#assets-vfx)
    - [4.2.1 No Spaces, Ever](#assets-vfx-rules)
  - [4.3 Levels / Maps](#assets-levels)
    - [4.3.1 No Errors Or Warnings](#assets-levels-no-errors-or-warnings)
    - [4.3.2 Lighting Should Be Built](#assets-levels-lighting-should-be-built)
    - [4.3.3 No Player Visible Z Fighting](#assets-levels-no-visible-z-fighting)
  - [4.4 Textures](#assets-textures)
    - [4.4.1 Dimensions Are Powers of 2](#assets-textures-dimensions)
    - [4.4.2 Texel Density Should Be Uniform](#assets-textures-density)
    - [4.4.3 Textures Should Be No Bigger than 8192](#assets-textures-max-size)
    - [4.4.4 Textures Should Be Grouped Correctly](#assets-textures-group)
    - [4.4.5 Textures Channels Should Be Merged and Used Correctly](#assets-textures-channels)
    - [4.4.6 Textures Should Not Be Repeating On Itself](#assets-textures-non-repeating)
    - [4.4.7 UI-Textures Should Be Setup Correctly](#assets-textures-ui)
  - [4.5 Materials & Shader](#assets-materials)
    - [4.5.1 Material Instances Should Be Based On The Correct Master Material](#assets-materials-master)
    - [4.5.2 Material Usage Should Conform To The Basic Art Direction Principles](#assets-materials-art-direction)
    - [4.5.3 Materials Should Only Utilize Unique Texture Inputs If They Add Significant Visual Value To The Underlying Asset](#assets-materials-textures)
- [5. Source Control Management](#5)
  - [5.1 Branches](#scm-branches)
    - [5.1.1 Main Branch](#scm-branches-main)
    - [5.1.2 Dev Branch](#scm-branches-dev)
    - [5.1.3 Task Branches](#scm-branches-tasks)
  - [5.2 Checkouts](#scm-checkouts)
  - [5.3 Checkins](#scm-checkins)
    - [5.3.1 Examples](#scm-checkins-examples)
  - [5.4 Merge](#scm-merge)
  - [5.5 Review Process](#scm-review)
  - [5.6 Attributes](#scm-attributes)
    - [5.6.1 Filtering](#scm-attributes-filtering)
  - [5.7 JIRA](#scm-jira)
    - [5.7.1 Setup](#scm-jira-setup)
    - [5.7.2 Workflow](#scm-jira-workflow)
- [6. Miscellaneous](#6)
  - [6.1 Shared Derived Data Cache](#misc-ddc)

## Important Terminology

<a name="terms-level-map"></a>
##### Levels/Maps

The word 'map' generally refers to what the average person calls a 'level' and may be used interchangeably. See this term's history [here](https://en.wikipedia.org/wiki/Level_(video_gaming)).

<a name="terms-identifiers"></a>
##### Identifiers
An `Identifier` is anything that resembles or serves as a "name". For example, the name of an asset, or the name of a material later, or a blueprint property, a variable, or a folder name, or for a data table row name, etc...

<a name="terms-cases"></a>
##### Cases

There are a few different ways you can `CaseWordsWhenNaming`. Here are some common casing types:

> ###### PascalCase
>
> Capitalize every word and remove all spaces, e.g. `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
>
> ###### camelCase
>
> The first letter is always lowercase but every following word starts with uppercase, e.g. `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>
> ###### Snake_case
>
> Words can arbitrarily start upper or lowercase but words are separated by an underscore, e.g. `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

<a name="terms-var-prop"></a>
##### Variables / Properties

The words 'variable' and 'property' in most contexts are interchangable. If they are both used together in the same context however:

<a name="terms-property"></a>
###### Property
Usually refers to a variable defined in a class. For example, if `BP_Barrel` had a variable `bExploded`, `bExploded` may be referred to as a property of `BP_Barrel`.

When in the context of a class, it is often used to imply accessing previously defined data.

<a name="terms-variable"></a>
###### Variable
Usually refers to a variable defined as a function argument or a local variable inside a function.

When in the context of a class, it is often used to convey discussion about its definition and what it will hold.

<a name="0"></a>
## 0. Principles

These principles have been adapted from [idomatic.js style guide](https://github.com/rwaldron/idiomatic.js/).

<a name="0.1"></a>
### 0.1 If your UE4 project already has a style guide, you should follow it

If you are working on a project or with a team that has a pre-existing style guide, it should be respected.  Any inconsistency between an existing style guide and this guide should defer to the existing.

Style guides should be living documents. You should propose style guide changes to an existing style guide as well as this guide if you feel the change benefits all usages.

> #### "Arguments over style are pointless. There should be a style guide, and you should follow it."
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 All structure, assets, and code in any Unreal Engine 4 project should look like a single person created it, no matter how many people contributed

Moving from one project to another should not cause a re-learning of style and structure. Conforming to a style guide removes unneeded guesswork and ambiguities.

It also allows for more productive creation and maintenance as one does not need to think about style. Simply follow the instructions. This style guide is written with best practices in mind, meaning that by following this style guide you will also minimize hard to track issues.

<a name="0.3"></a>
### 0.3 Friends do not let friends have bad style

If you see someone working either against a style guide or no style guide, try to correct them.

When working within a team or discussing within a community such as [Unreal Slackers](http://join.unrealslackers.org/), it is far easier to help and to ask for help when people are consistent. Nobody likes to help untangle someone's Blueprint spaghetti or deal with assets that have names they can't understand.

If you are helping someone whose work conforms to a different but consistent and sane style guide, you should be able to adapt to it. If they do not conform to any style guide, please direct them here.

<a name="0.4"></a>
### 0.4 A team without a style guide is no team of mine

When joining an Unreal Engine 4 team, one of your first questions should be "Do you have a style guide?". If the answer is no, you should be skeptical about their ability to work as a team.

<a name="0.5"></a>
### 0.5 Don't Break The Law

Gamemakin LLC is not a lawyer, but please don't introduce illegal actions and behavior to a project, including but not limited to:

* Don't distribute content you don't have the rights to distribute
* Don't infringe on someone else's copyrighted or trademark material
* Don't steal content
* Follow licensing restrictions on content, e.g. attribute when attributions are needed

<a name="00"></a>
## 00. Globally Enforced Opinions

<a name="00.1"></a>
### 00.1 Forbidden Characters

<a name="identifiers-1"></a>
#### Identifiers

In any `Identifier` of any kind, **never** use the following unless absolutely forced to:

* White space of any kind
* Backward slashes `\`
* Symbols i.e. `#!@$%`
* Any Unicode character

Any `Identifier` should strive to only have the following characters when possible (the RegEx `[A-Za-z0-9_]+`)

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890
* _ (sparingly)

The reasoning for this is this will ensure the greatest compatibility of all data across all platforms across all tools, and help prevent downtime due to potentially bad character handling for identifiers in code you don't control.

<a name="anc"></a>
<a name="1"></a>
## 1. Asset Naming Conventions

Naming conventions should be treated as law. A project that conforms to a naming convention is able to have its assets managed, searched, parsed, and maintained with incredible ease.

Most things are prefixed with prefixes being generally an acronym of the asset type followed by an underscore.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`

All assets should have a _Base Asset Name_. A Base Asset Name represents a logical grouping of related assets. Any asset that is part of this logical group should follow the standard of  `Prefix_BaseAssetName_Variant_Suffix`.

Keeping the pattern `Prefix_BaseAssetName_Variant_Suffix` and in mind and using common sense is generally enough to warrant good asset names. Here are some detailed rules regarding each element.

`Prefix` and `Suffix` are to be determined by the asset type through the following [Asset Name Modifier](#asset-name-modifiers) tables.

`BaseAssetName` should be determined by a short and easily recognizable name related to the context of this group of assets. For example, if you had a character named Bob, all of Bob's assets would have the `BaseAssetName` of `Bob`.

For unique and specific variations of assets, `Variant` is either a short and easily recognizable name that represents logical grouping of assets that are a subset of an asset's base name. For example, if Bob had multiple skins these skins should still use `Bob` as the `BaseAssetName` but include a recognizable `Variant`. An 'Evil' skin would be referred to as `Bob_Evil` and a 'Retro' skin would be referred to as `Bob_Retro`.

For unique but generic variations of assets, `Variant` is a two digit number starting at `01`. For example, if you have an environment artist generating nondescript rocks, they would be named `Rock_01`, `Rock_02`, `Rock_03`, etc. Except for rare exceptions, you should never require a three digit variant number. If you have more than 100 assets, you should consider organizing them with different base names or using multiple variant names.

Depending on how your asset variants are made, you can chain together variant names. For example, if you are creating flooring assets for an Arch Viz project you should use the base name `Flooring` with chained variants such as `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Examples

##### 1.1e1 Bob

| Asset Type              | Asset Name                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks

| Asset Type              | Asset Name                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | SM_Rock_01                                                 |
| Static Mesh (02)        | SM_Rock_02                                                 |
| Static Mesh (03)        | SM_Rock_03                                                 |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Asset Name Modifiers

When naming an asset, use these tables to determine the prefix and suffix to use with an asset's [Base Asset Name](#base-asset-name).

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Most Common

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [Should be in a folder called Maps.](#2.4) |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            | See [Blueprints](#anc-blueprints)|
| Material                | M_         |            |                                  |
| Static Mesh             | SM_        |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Control Rig             | CR_        |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
#### 1.2.3 Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Context    |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
#### 1.2.4 Blueprints

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component     | BP_        | Component  | I.e. BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | Do not use macro libraries if possible. |
| Enumeration             | E_         |            | Underscore is used as distinction between C++ and BP enums |
| Structure               | F_         |            | Underscore is used as distinction between C++ and BP structs |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-core-blueprints"></a>
<a name="1.2.4.1"></a>
##### 1.2.4.1 Core Blueprints
Certain Blueprint classes which are part of the core game framework get their own custom Prefix. Those should always be insdie the [Core Folder](#structure-core).

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| GameInstance            | GI_        |            |                                  |
| GameMode                | GM_        |            |                                  |
| GameState               | GS_        |            | Name should match a specific GM unless they are independant |
| PlayerState             | PS_        |            | Name should match a specific GM unless they are independant |
| PlayerController        | PC_        |            | Name should match a specific GM unless they are independant |
| Pawn                    | PP_        |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
#### 1.2.5 Materials

| Asset Type                    | Prefix     | Suffix     | Notes                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | M_, MI_    | _PostProcess |                                |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
#### 1.2.6 Textures

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | See notes below about [packing](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
##### 1.2.6.1 Texture Packing
It is common practice to pack multiple layers of texture data into one texture. An example of this is packing Emissive, Roughness, Ambient Occlusion together as the Red, Green, and Blue channels of a texture respectively. To determine the suffix, simply stack the given suffix letters from above together, e.g. `_ERO`.

> It is generally acceptable to include an Alpha/Opacity layer in your Diffuse/Albedo's alpha channel and as this is common practice, adding `A` to the `_D` suffix is optional.

Packing 4 channels of data into a texture (RGBA) is not recommended except for an Alpha/Opacity mask in the Diffuse/Albedo's alpha channel as a texture with an alpha channel incurs more overhead than one without.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
#### 1.2.7 Miscellaneous

| Asset Type                 | Prefix     | Suffix     | Notes                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Prefix should be based on class. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| File Media Source          | FMS_       |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | These should be fixed up ASAP.   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
#### 1.2.8 Paper 2D

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
#### 1.2.9 Physics

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset           | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
#### 1.2.10 Sounds

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | No prefix/suffix. Should be put in a folder called SoundClasses |
| Sound Concurrency       |            | _SC        | Should be named after a SoundClass |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
#### 1.2.11 User Interface

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
#### 1.2.12 Effects

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | M_, MI_    | _PostProcess |                                  |

**[⬆ Back to Top](#table-of-contents)**

<a name="2"></a>
<a name="structure"></a>
## 2. Content Directory Structure

Equally important as asset names, the directory structure style of a project should be considered law. Asset naming conventions and content directory structure go hand in hand, and a violation of either causes unneeded chaos.

There are multiple ways to lay out the content of a UE4 project. In this style, we will be using a structure that relies more on filtering and search abilities of the Content Browser for those working with assets to find assets of a specific type instead of another common structure that groups asset types with folders.

> If you are using the prefix [naming convention](#1.2) above, using folders to contain assets of similar types such as `Meshes`, `Textures`, and `Materials` is a redundant practice as asset types are already both sorted by prefix as well as able to be filtered in the content browser.

<a name="2e1"><a>
### 2e1 Example Project Content Structure

<pre>
|-- Content
    |-- <a href="#2.2">GameName</a>
        |-- Audio
        |   |-- Music
        |   |-- SFX
        |   |   |-- Abilities
        |   |   |-- Environment
        |   |   |-- UI
        |   |   |-- MovementSounds
        |-- Art
        |   |-- Modular
        |   |   |-- SetName (ex. “Airport”)
        |   |   |   |-- Texture Assets 
        |   |   |   |-- Static Mesh Asset
        |   |   |   |-- Material Instance Asset
        |   |-- Props
        |   |   |-- AssetName
        |   |   |   |-- Texture Assets
        |   |   |   |-- Static Mesh Asset
        |   |   |   |-- Material Instance Asset 
        |-- <a href="#2.5">Core</a>
        |   |-- Abilities
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Vehicles
        |   |-- Weapons
        |-- Gameplay
        |   |-- Abilities
        |   |-- AssetName (ex. “ChargeStation”)
        |   |   |-- Texture Assets
        |   |   |-- Skeletal Mesh Asset
        |   |   |-- Material Instance Asset
        |   |   |-- Skeleton Asset
        |   |   |-- AnimBP Asset
        |   |   |-- PhysicsAsset
        |   |   |-- Designer BP
        |   |-- Characters
        |   |   |-- Bob
        |   |   |-- Common
        |   |   |   |-- <a href="#2.7">Animations</a>
        |   |   |   |-- Audio
        |   |   |-- Jack
        |   |   |-- Steve
        |   |   |-- <a href="#2.1.3">Zoe</a>
        |   |-- Placeables
        |   |   |-- Pickups
        |   |-- Vehicles
        |   |   |-- FixedWing
        |   |   |-- Ground
        |   |   |   |-- Buggy
        |   |   |   |-- MonsterTruck
        |   |   |-- RotaryWing
        |-- <a href="#2.4">Maps</a>
        |   |-- MapName
        |   |   |-- MapName Asset
        |   |   |-- MapName Builddata
        |   |   |   |-- MapName_sharedassets (autogenerated)
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- VFX
            |-- Electrical
            |-- Fire
            |-- Weather
            |-- WeaponAbilityFX
</pre>

The reasons for this structure are listed in the following sub-sections.

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Folder Names

These are common rules for naming any folder in the content structure.

<a name="2.1.1"></a>
#### 2.1.1 Always Use PascalCase[<sup>*</sup>](#terms-cases)

PascalCase refers to starting a name with a capital letter and then instead of using spaces, every following word also starts with a capital letter. For example, `DesertEagle`, `RocketPistol`, and `ASeriesOfWords`.

See [Cases](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Never Use Spaces

Re-enforcing [2.1.1](#2.1.1), never use spaces. Spaces can cause various engineering tools and batch processes to fail. Ideally, your project's root also contains no spaces and is located somewhere such as `D:\Project` instead of `C:\Users\My Name\My Documents\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Never Use Unicode Characters And Other Symbols

If one of your game characters is named 'Zoë', its folder name should be `Zoe`. Unicode characters can be worse than [Spaces](#2.1.2) for engineering tool and some parts of UE4 don't support Unicode characters in paths either.

Related to this, if your project has [unexplained issues](https://answers.unrealengine.com/questions/101207/undefined.html) and your computer's user name has a Unicode character (i.e. your name is `Zoë`), any project located in your `My Documents` folder will suffer from this issue. Often simply moving your project to something like `D:\Project` will fix these mysterious issues.

Using other characters outside `a-z`, `A-Z`, and `0-9` such as `@`, `-`, `_`, `,`, `*`, and `#` can also lead to unexpected and hard to track issues on other platforms, source control, and weaker engineering tools.

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Use A Top Level Folder For Project Specific Assets

All of a project's assets should exist in a folder named after the project. For example, if your project is named 'Generic Shooter', _all_ of it's content should exist in `Content/GenericShooter`.

> The `Developers` folder is not for assets that your project relies on and therefore is not project specific. See [Developer Folders](#2.3) for details about this.

There are multiple reasons for this approach.

<a name="2.2.1"></a>
#### 2.2.1 No Global Assets

Often in code style guides it is written that you should not pollute the global namespace and this follows the same principle. When assets are allowed to exist outside of a project folder, it often becomes much harder to enforce a strict structure layout as assets not in a folder encourages the bad behavior of not having to organize assets.

Every asset should have a purpose, otherwise it does not belong in a project. If an asset is an experimental test and shouldn't be used by the project it should only ever exist on its respective [task branch](#scm-branches-tasks) and be cleaned up before [merging](#scm-merge).

<a name="2.2.2"></a>
#### 2.2.2 Reduce Migration Conflicts

When working on multiple projects it is common for a team to copy assets from one project to another if they have made something useful for both. When this occurs, the easiest way to perform the copy is to use the Content Browser's Migrate functionality as it will copy over not just the selected asset but all of its dependencies.

These dependencies are what can easily get you into trouble. If two project's assets do not have a top level folder and they happen to have similarly named or already previously migrated assets, a new migration can accidentally wipe any changes to the existing assets.

This is also the primary reason why Epic's Marketplace staff enforces the same policy for submitted assets.

After a migration, safe merging of assets can be done using the 'Replace References' tool in the content browser with the added clarity of assets not belonging to a project's top level folder are clearly pending a merge. Once assets are merged and fully migrated, there shouldn't be another top level folder in your Content tree. This method is _100%_ guaranteed to make any migrations that occur completely safe.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Master Material Example

For example, say you created a master material in one project that you would like to use in another project so you migrated that asset over. If this asset is not in a top level folder, it may have a name like `Content/MaterialLibrary/M_Master`. If the target project doesn't have a master material already, this should work without issue.

As work on one or both projects progress, their respective master materials may change to be tailored for their specific projects due to the course of normal development.

The issue comes when, for example, an artist for one project created a nice generic modular set of static meshes and someone wants to include that set of static meshes in the second project. If the artist who created the assets used material instances based on `Content/MaterialLibrary/M_Master` as they're instructed to, when a migration is performed there is a great chance of conflict for the previously migrated `Content/MaterialLibrary/M_Master` asset.

This issue can be hard to predict and hard to account for. The person migrating the static meshes may not be the same person who is familiar with the development of both project's master material, and they may not be even aware that the static meshes in question rely on material instances which then rely on the master material. The Migrate tool requires the entire chain of dependencies to work however, and so it will be forced to grab `Content/MaterialLibrary/M_Master` when it copies these assets to the other project and it will overwrite the existing asset.

It is at this point where if the master materials for both projects are incompatible in _any way_, you risk breaking possibly the entire material library for a project as well as any other dependencies that may have already been migrated, simply because assets were not stored in a top level folder. The simple migration of static meshes now becomes a very ugly task.

<a name="2.2.3"></a>
#### 2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free

An extension to [2.2.2](#2.2.2), if a team member decides to add sample content, template files, or assets they bought from the marketplace, it is guaranteed, as long your project's top-level folder is uniquely named,that these new assets will not interfere with your project.

You can not trust marketplace content to fully conform to the [top level folder rule](#2.2). There exists many assets that have the majority of their content in a top level folder but also have possibly modified Epic sample content as well as level files polluting the global `Content` folder.

When adhering to [2.2](#2.2), the worst marketplace conflict you can have is if two marketplace assets both have the same Epic sample content. If all your assets are in a project specific folder, including sample content you may have moved into your folder, your project will never break.

<a name="2.2.4"></a>
#### 2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained

If your project plans to release DLC or has multiple sub-projects associated with it that may either be migrated out or simply not cooked in a build, assets relating to these projects should have their own separate top level content folder. This make cooking DLC separate from main project content far easier. Sub-projects can also be migrated in and out with minimal effort. If you need to change a material of an asset or add some very specific asset override behavior in a patch, you can easily put these changes in a patch folder and work safely without the chance of breaking the core project.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Only Use Developers Folder For Strictly Local Files

When properly using source control and [task branches](#scm-branches-tasks) there should be no need to put any project related files in the Developers folder. For this reason the Developers folder should be ignored for every project and never be submitted to source control.

If a team member wishes to put assets under source control which are not yet ready to be integrated into the main project, they can do so safely on the respective task branch. If any such assets are needed repetitively across different branches, e.g. for Debugging/Testing purposes, it should be considered to properly add them to the main project in a secure way. In the meantime the assets in question can be shared between team members and branches by shelving them in source control.

The only way a Developers folder should ever be used is for files that are only required by a specific developer/computer, e.g. a developer's custom Editor Material. When deciding to put assets into the Developers folder it is essential to take extra care there are no dependencies on these assets from within the main project as such dependencies will result in errors for other team members.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 All Map[<sup>*</sup>](#terms-level-map) Files Belong In A Folder Called Maps

Map files are incredibly special and it is common for every project to have its own map naming system, especially if they work with sub-levels or streaming levels. No matter what system of map organization is in place for the specific project, all levels should belong in `/Content/Project/Maps`.

Being able to tell someone to open a specific map without having to explain where it is is a great time saver and general 'quality of life' improvement. It is common for levels to be within sub-folders of `Maps`, such as `Maps/Campaign1/` or `Maps/Arenas`, but the most important thing here is that they all exist within `/Content/Project/Maps`.

This also simplifies the job of cooking for engineers. Wrangling levels for a build process can be extremely frustrating if they have to dig through arbitrary folders for them. If a team's maps are all in one place, it is much harder to accidentally not cook a map in a build. It also simplifies lighting build scripts as well as QA processes.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Use A `Core` Folder For Critical Blueprints And Other Assets

Use `/Content/Project/Core` folder for assets that are absolutely fundamental to a project's workings. For example, base `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState`, and related Blueprints should live here.

This creates a very clear "don't touch these" message for other team members. Non-engineers should have very little reason to enter the `Core` folder. Following good code structure style, designers should be making their gameplay tweaks in child classes that expose functionality. World builders should be using prefab Blueprints in designated folders instead of potentially abusing base classes.

For example, if your project requires pickups that can be placed in a level, there should exist a base Pickup class in `Core/Pickups` that defines base behavior for a pickup. Specific pickups such as a Health or Ammo should exist in a folder such as `/Content/Project/Placeables/Pickups/`. Game designers can define and tweak pickups in this folder however they please, but they should not touch `Core/Pickups` as they may unintentionally break pickups project-wide.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Do Not Create Folders Called `Assets` or `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Creating a folder named `Assets` is redundant

All assets are assets.

<a name="2.6.2"></a>
#### 2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant

All asset names are named with their asset type in mind. These folders offer only redundant information and the use of these folders can easily be replaced with the robust and easy to use filtering system the Content Browser provides.

Want to view only static mesh in `Environment/Rocks/`? Simply turn on the Static Mesh filter. If all assets are named correctly, they will also be sorted in alphabetical order regardless of prefixes. Want to view both static meshes and skeletal meshes? Simply turn on both filters. This eliminates the need to potentially have to `Control-Click` select two folders in the Content Browser's tree view.

> This also extends the full path name of an asset for very little benefit. The `S_` prefix for a static mesh is only two characters, whereas `Meshes/` is seven characters.

Not doing this also prevents the inevitability of someone putting a static mesh or a texture in a `Materials` folder.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Very Large Asset Sets Get Their Own Folder Layout

This can be seen as a pseudo-exception to [2.6](#2.6).

There are certain asset types that have a huge volume of related files where each asset has a unique purpose. The two most common are Animation and Audio assets. If you find yourself having 15+ of these assets that belong together, they should be together.

For example, animations that are shared across multiple characters should lay in `Characters/Common/Animations` and may have sub-folders such as `Locomotion` or `Cinematic`.

> This does not apply to assets like textures and materials. It is common for a `Rocks` folder to have a large amount of textures if there are a large amount of rocks, however these textures are generally only related to a few specific rocks and should be named appropriately. Even if these textures are part of a [Material Library](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

If your project makes use of master materials, layered materials, or any form of reusable materials or textures that do not belong to any subset of assets, these assets should be located in `Content/Project/MaterialLibrary`.

This way all 'global' materials have a place to live and are easily located.

> This also makes it incredibly easy to enforce a 'use material instances only' policy within a project. If all artists and assets should be using material instances, then the only regular material assets that should exist are within this folder. You can easily verify this by searching for base materials in any folder that isn't the `MaterialLibrary`.

The `MaterialLibrary` doesn't have to consist of purely materials. Shared utility textures, material functions, and other things of this nature should be stored here as well within folders that designate their intended purpose. For example, generic noise textures should be located in `MaterialLibrary/Utility`.

Any testing or debug materials should be within `MaterialLibrary/Debug`. This allows debug materials to be easily stripped from a project before shipping and makes it incredibly apparent if production assets are using them if reference errors are shown.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 No Empty Folders

There simply shouldn't be any empty folders. They clutter the content browser.

If you find that the content browser has an empty folder you can't delete, you should perform the following:
1. Be sure you're using source control.
1. Immediately run Fix Up Redirectors on your project.
1. Navigate to the folder on-disk and delete the assets inside.
1. Close the editor.
1. Make sure your source control state is in sync (i.e. if using Perforce, run a Reconcile Offline Work on your content directory)
1. Open the editor. Confirm everything still works as expected. If it doesn't, revert, figure out what went wrong, and try again.
1. Ensure the folder is now gone.
1. Submit changes to source control.

**[⬆ Back to Top](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

This section will focus on Blueprint classes and their internals. When possible, style rules conform to [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Remember: Blueprinting badly bears blunders, beware! (Phrase by [KorkuVeren](http://github.com/KorkuVeren))

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compiling

All blueprints should compile with zero warnings and zero errors. You should fix blueprint warnings and errors immediately as they can quickly cascade into very scary unexpected behavior.

Do *not* submit broken blueprints to source control. If you must store them on source control, shelve them instead.

Broken blueprints can cause problems that manifest in other ways, such as broken references, unexpected behavior, cooking failures, and frequent unneeded recompilation. A broken blueprint has the power to break your entire game.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables

The words `variable` and `property` may be used interchangeably.

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Naming

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Nouns

All non-boolean variable names must be clear, unambiguous, and descriptive nouns.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

All non-boolean variables should be in the form of [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Examples

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Boolean `b` Prefix

All booleans should be named in PascalCase but prefixed with a lowercase `b`.

Example: Use `bDead` and `bEvil`, **not** `Dead` and `Evil`.

UE4 Blueprint editors know not to include the `b` in user-friendly displays of the variable.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Boolean Names

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 General And Independent State Information

All booleans should be named as descriptive adjectives when possible if representing general information. Do not include words that phrase the variable as a question, such as `Is`. This is reserved for functions.

Example: Use `bDead` and `bHostile` **not** `bIsDead` and `bIsHostile`.

Try to not use verbs such as `bRunning`. Verbs tend to lead to complex states.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Complex States

Do not to use booleans to represent complex and/or dependent states. This makes state adding and removing complex and no longer easily readable. Use an enumeration instead.

Example: When defining a weapon, do **not** use `bReloading` and `bEquipping` if a weapon can't be both reloading and equipping. Define an enumeration named `EWeaponState` and use a variable with this type named `WeaponState` instead. This makes it far easier to add new states to weapons.

Example: Do **not** use `bRunning` if you also need `bWalking` or `bSprinting`. This should be defined as an enumeration with clearly defined state names.

If there are multiple states that can occur concurrently they should be implemented as Flags using a [BitMask Enum](https://unrealcommunity.wiki/bitmask-bitflag-enums-kdq2na6w). Consider defining the Enum in C++ (either the parent class or in a dedicated typedef BlueprintFunctionLibrary) with Blueprint exposed comparison functions as handling bitmasks purely in Blueprint can be tricky sometimes.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Considered Context

All variable names must not be redundant with their context as all variable references in Blueprint will always have context.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Examples

Consider a Blueprint called `BP_PlayerCharacter`.

**Bad**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

All of these variables are named redundantly. It is implied that the variable is representative of the `BP_PlayerCharacter` it belongs to because it is `BP_PlayerCharacter` that is defining these variables.

**Good**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 Do _Not_ Include Atomic Type Names

Atomic or primitive variables are variables that represent data in their simplest form, such as booleans, integers, floats, and enumerations.

Strings and vectors are considered atomic in terms of style when working with Blueprints, however they are technically not atomic.

> While vectors consist of three floats, vectors are often able to be manipulated as a whole, same with rotators.

> Do _not_ consider Text variables as atomic, they are secretly hiding localization functionality. The atomic type of a string of characters is `String`, not `Text`.

Atomic variables should not have their type name in their name.

Example: Use `Score`, `Kills`, and `Description` **not** `ScoreFloat`, `FloatKills`, `DescriptionString`.

The only exception to this rule is when a variable represents 'a number of' something to be counted _and_ when using a name without a variable type is not easy to read.

Example: A fence generator needs to generate X number of posts. Store X in `NumPosts` or `PostsCount` instead of `Posts` as `Posts` may potentially read as an Array of a variable type named `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Do Include Non-Atomic Type Names

Non-atomic or complex variables are variables that represent data as a collection of atomic variables. Structs, Classes, Interfaces, and primitives with hidden behavior such as `Text` and `Name` all qualify under this rule.

> While an Array of an atomic variable type is a list of variables, Arrays do not change the 'atomicness' of a variable type.

These variables should include their type name while still considering their context.

If a class owns an instance of a complex variable, i.e. if a `BP_PlayerCharacter` owns a `BP_Hat`, it should be stored as the variable type as without any name modifications.

Example: Use `Hat`, `Flag`, and `Ability` **not** `MyHat`, `MyFlag`, and `PlayerAbility`.

If a class does not own the value a complex variable represents, you should use a noun along with the variable type.

Example: If a `BP_Turret` has the ability to target a `BP_PlayerCharacter`, it should store its target as `TargetPlayer` as when in the context of `BP_Turret` it should be clear that it is a reference to another complex variable type that it does not own.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays

Arrays follow the same naming rules as above, but should be named as a plural noun.

Example: Use `Targets`, `Hats`, and `EnemyPlayers`, **not** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Editable Variables

All variables that are safe to change the value of in order to configure behavior of a blueprint should be marked as `Editable`.

Conversely, all variables that are not safe to change or should not be exposed to designers should _not_ be marked as editable, unless for engineering reasons the variable must be marked as `Expose On Spawn`.

Do not arbitrarily mark variables as `Editable`.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Tooltips

All `Editable` variables, including those marked editable just so they can be marked as `Expose On Spawn`, should have a description in their `Tooltip` fields that explains how changing this value affects the behavior of the blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Slider And Value Ranges

All `Editable` variables should make use of slider and value ranges if there is ever a value that a variable should _not_ be set to.

Example: A blueprint that generates fence posts might have an editable variable named `PostsCount` and a value of -1 would not make any sense. Use the range fields to mark 0 as a minimum.

If an editable variable is used in a Construction Script, it should have a reasonable Slider Range defined so that someone can not accidentally assign it a large value that could crash the editor.

A Value Range only needs to be defined if the bounds of a value are known. While a Slider Range prevents accidental large number inputs, an undefined Value Range allows a user to specify a value outside the Slider Range that may be considered 'dangerous' but still valid.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categories

If a class has only a small number of variables, categories are not required.

If a class has a moderate amount of variables (5-10), all `Editable` variables should have a non-default category assigned. A common category is `Config`.

If a class has a large amount of variables, all `Editable` variables should be categorized into sub-categories using the category `Config` as the base category. Non-editable variables should be categorized into descriptive categories describing their usage.

> You can define sub-categories by using the pipe character `|`, i.e. `Config | Animations`.

Example: A weapon class set of variables might be organized as:

    |-- Config
    |    |-- Animations
    |    |-- Effects
    |    |-- Audio
    |    |-- Recoil
    |    |-- Timings
    |-- Animations
    |-- State
    |-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 Variable Access Level

In C++, variables have a concept of access level. Public means any code outside the class can access the variable. Protected means only the class and any child classes can access this variable internally. Private means only this class and no child classes can access this variable.

Blueprints do not have a defined concept of protected access currently.

Treat `Editable` variables as public variables. Treat non-editable variables as protected variables.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Private Variables

Unless it is known that a variable should only be accessed within the class it is defined and never a child class, do not mark variables as private. Until variables are able to be marked `protected`, reserve private for when you absolutely know you want to restrict child class usage.

<a name="3.2.4.2"></a>
<a name="bp-vars-access-components"></a>
##### 3.2.4.2 Components

Every Actor automatically has each of his Components referenced as a variable. Those variables can not be marked private or Editable and thus should always be treated as protected. This means you should never access an Actor's Component from outside its class!

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Advanced Display

If a variable should be editable but often untouched, mark it as `Advanced Display`. This makes the variable hidden unless the advanced display arrow is clicked.

To find the `Advanced Display` option, it is listed as an advanced displayed variable in the variable details list.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Transient Variables

Transient variables are variables that do not need to have their value saved and loaded and have an initial value of zero or null. This is useful for references to other objects and actors who's value isn't known until run-time. This prevents the editor from ever saving a reference to it, and speeds up saving and loading of the blueprint class.

Because of this, all transient variables should always be initialized as zero or null. To do otherwise would result in hard to debug errors.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Config Variables

Do not use the `Config Variable` flag. This makes it harder for designers to control blueprint behavior. Config variables should only be used in C++ for rarely changed variables. Think of them as `Advanced Advanced Display` variables.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, and Event Dispatchers

This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming

The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* Is it an RPC?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="3.3.1.0"></a>
<a name="bp-funcs-naming-case"></a>
#### 3.3.1.0 Always use PascalCase

As with folder and variable names you should always use [PascalCase](#terms-cases) when naming functions. In particular this means there should never be an underscore in a function name as this can lead to issues when searching for references to this function. The only exception to this rule are functions that are used as a RepNotify, those should be prefixed with "OnRep_" (BP-only RepNotifies ar automatically named this way).

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs

All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should all start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

`OnRep` functions, event handlers, and event dispatchers are an exception to this rule.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

All functions for replicated with notification variables should have the form `OnRep_Variable`. This is forced by the Blueprint editor. If you are writing a C++ `OnRep` function however, it should also follow this convention when exposing it to Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#bp-funcs-naming-verbs).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On`

Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#bp-funcs-naming-verbs). The verb may move to the end however if past-tense reads better.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) of the word `On` are exempt from following the verb rule.

`Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target

Any time an RPC is created, it should be prefixed with either `Server`, `Client`, or `Multicast`. No exceptions.

After the prefix, follow all other rules regarding function naming.

Good examples:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Bad examples:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out.

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

This section covers things that apply to all Blueprint graphs.
  
<a name="3.4.1"></a>
<a name="bp-graphs-electronic-nodes"></a>
#### 3.4.1 Electronic Nodes
  
It is heavily recommended to use the [Electronic Nodes Plugin](https://www.unrealengine.com/marketplace/en-US/product/electronic-nodes). Once configured the plugin settings should be set as default so Unreal saves them to `DefaultEditorPerProjectUserSettings.ini`. This way the settings can be added to source control and will be consistent for everyone working on the project.
  
While Electronic Nodes do a great job at making graphs cleaner and easier to read on their own they should never be treated as a replacement for the following rules.

<a name="3.4.2"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.2 No Spaghetti

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.3"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.3 Align Wires Not Nodes

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/ThreeDeeFlorett/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/ThreeDeeFlorett/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/ThreeDeeFlorett/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.4"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.4 White Exec Lines Are Top Priority

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.5"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.5 Graphs Should Be Reasonably Commented

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.6"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.6 Graphs Should Handle Casting Errors Where Appropriate

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.7"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.7 Graphs Should Not Have Any Dangling / Loose / Dead Nodes

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Asset Creation"></a>
<a name="assets"></a>
## 4. Asset Creation

<a name="4.1"></a>
<a name="asets-sm"></a>
### 4.1 Static Meshes

This section will focus on Static Mesh assets and their internals.

<a name="4.1.1"></a>
<a name="assets-sm-uvs"></a>
#### 4.1.1 Static Mesh UVs

If Linter is reporting bad UVs and you can't seem to track it down, open the resulting `.log` file in your project's `Saved/Logs` folder for exact details as to why it's failing.

<a name="4.1.1.1"></a>
<a name="assets-sm-uvs-no-missing"></a>
##### 4.1.1.1 All Meshes Must Have valid UVs with as few UV-Islands as possible

Pretty simple. All meshes, regardless how they are to be used, should not be missing UVs. Additionally, the UVs should not be folding into each other and no unnecessary UV splits should be present due to the increased vertex count.

<a name="4.1.1.2"></a>
<a name="assets-sm-uvs-no-overlapping"></a>
##### 4.1.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps

Pretty simple. All static meshes, regardless how they are to be used, should have valid non-overlapping UVs on a secondary UV channel. Make sure that the proper UV channel is selected for them in the “Light Map Coordinate Index” setting.

<a name="4.1.1.3"></a>
<a name="assets-sm-uvs-lightmap-resolution-specified"></a>
##### 4.1.1.3 All Static Meshes Must Have Their Light Map Resolution Specified Deliberately

The “Light Map Resolution” setting should account for the scale of the object. Smaller objects (<10x10x10 cm), especially the ones that are expected to repeat often should have their resolution reduced below 64x64 pixels. Larger objects can have their lightmap resolution increased up to a maximum of 512x512.

<a name="4.1.1.4"></a>
<a name="assets-sm-uvs-lightmap-boundaries-snapped"></a>
##### 4.1.1.4 All Lightmap Island Boundaries Should be snapped to Pixel

To increase baking quality all borders of a Lightmap UV-Island should be snapped to a pixel-corner in the corresponding final Lightmap resolution.

<a name="4.1.2"></a>
<a name="assets-sm-lods"></a>
#### 4.1.2 LODs Should Be Set Up Correctly

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.Those LODs should be auto-generated via the available UnrealEngine tools whenever possible to remain time-efficient. LOD-distances should be adjusted in accordance with the specific scale/importance of the object.

<a name="4.1.3"></a>
<a name="assets-sm-modular-snapping"></a>
#### 4.1.3 Modular Socketless Assets Should Snap To The Grid Cleanly

This is a subjective check on a per-asset basis, however any modular assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.1.4"></a>
<a name="assets-sm-collision"></a>
#### 4.1.4 All Meshes Must Have Collision

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.1.5"></a>
<a name="assets-sm-scaled"></a>
#### 4.1.5 All Meshes Should Be Scaled Correctly

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

<a name="4.1.6"></a>
<a name="assets-sm-pivot"></a>
#### 4.1.6 Asset pivots and sockets should be placed according to the asset's final usecase

Always ask for the asset usecase beforehand and in consultation with the programmer or level artist so you can setup pivot and sockets correctly. 

When exporting from 3D modeling software make sure your asset is rotated according to UE4's axis layout:
* x -> Forward
* y -> Right
* z -> Up

<a name="4.1.7"></a>
<a name="assets-sm-import"></a>
#### 4.1.7 Use the correct import settings for static meshes

* uncheck “Import Material”
* uncheck “Import Textures”
* uncheck “generate Lightmap UVs”

<a name="4.2"></a>
<a name="assets-vfx"></a>
### 4.2 VFX

This section will focus on Niagara assets and their internals.

<a name="4.2.1"></a>
<a name="assets-vfx-rules"></a>
#### 4.2.1 No Spaces, Ever

As mentioned in [00.1 Forbidden Identifiers](#00), spaces and all white space characters are forbidden in identifiers. This is especially true for Niagara systems as it makes working with things significantly harder if not impossible when working with HLSL or other means of scripting within Niagara and trying to reference an identifier.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))

<a name="4.3"></a>
<a name="assets-levels"></a>
### 4.3 Levels / Maps

[See Terminology Note](#terms-level-map) regarding "levels" vs "maps".

This section will focus on Level assets and their internals.

<a name="4.3.1"></a>
<a name="assets-levels-no-errors-or-warnings"></a>
#### 4.3.1 No Errors Or Warnings

All levels should load with zero errors or warnings. If a level loads with any errors or warnings, they should be fixed immediately to prevent cascading issues.

You can run a map check on an open level in the editor by using the console command "map check".

Please note: Linter is even more strict on this than the editor is currently, and will catch load errors that the editor will resolve on its own.

<a name="4.3.2"></a>
<a name="assets-levels-lighting-should-be-built"></a>
#### 4.3.2 Lighting Should Be Built

It is normal during development for levels to occasionally not have lighting built. When doing a test/internal/shipping build or any build that is to be distributed however, lighting should always be built.

<a name="4.3.3"></a>
<a name="assets-levels-no-visible-z-fighting"></a>
#### 4.3.3 No Player Visible Z Fighting

Levels should not have any [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) in all areas visible to the player.

<a name="4.4"></a>
<a name="assets-textures"></a>
### 4.4 Textures

This section will focus on Texture assets and their internals.

<a name="4.4.1"></a>
<a name="assets-textures-dimensions"></a>
#### 4.4.1 Dimensions Are Powers of 2

All textures, except for UI textures, must have its dimensions in multiples of powers of 2. Textures do not have to be square.

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="4.4.2"></a>
<a name="assets-textures-density"></a>
#### 4.4.2 Texel Density Should Be Uniform

All textures should be of a size appropriate for their standard use case. Appropriate texel density varies from project to project, but all textures within that project should have a consistent density.

For example, if a project's texel density is 8 pixel per 1 unit, a texture that is meant to be applied to a 100x100 unit cube should be 1024x1024, as that is the closest power of 2 that matches the project's texel density.

<a name="4.4.3"></a>
<a name="assets-textures-max-size"></a>
#### 4.4.3 Textures Should Be No Bigger than 8192

No texture should have a dimension that exceeds 8192 in size, unless you have a very explicit reason to do so. Often, using a texture this big is simply just a waste of resources.

<a name="4.4.4"></a>
<a name="assets-textures-group"></a>
#### 4.4.4 Textures Should Be Grouped Correctly

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.

<a name="4.4.5"></a>
<a name="assets-textures-channels"></a>
#### 4.4.5 Textures Channels Should Be Merged and Used Correctly

Set up the RGB and Alpha channels of your texture according to the Master Material the Texture is intended to be used with. 

<a name="4.4.6"></a>
<a name="assets-textures-non-repeating"></a>
#### 4.4.6 Textures Should Not Be Repeating On Itself

All parts of the texture should contain unique, non-repeating details that warrant the underlying texture resolution. Utilize the “tiling” parameters of a Material Instance, in case that a higher texel density is required.

<a name="4.4.7"></a>
<a name="assets-textures-ui"></a>
#### 4.4.7 UI-Textures Should Be Setup Correctly

Set the texture settings in Unreal:
* Compression: UserInterface 2D
* Texture Group: UI
* Never Stream: true

<a name="4.5"></a>
<a name="assets-materials"></a>
### 4.5 Materials & Shader

Every newly created Material will be created as a Material Instance and derive its available parameters from a pre-existing Master Material.

<a name="4.5.1"></a>
<a name="assets-materials-master"></a>
#### 4.5.1 Material Instances Should Be Based On The Correct Master Material

Each Master Material that a Material Instance can be derived from will be named according to its specific use-case. Make sure

<a name="4.5.2"></a>
<a name="assets-materials-art-direction"></a>
#### 4.5.2 Material Usage Should Conform To The Basic Art Direction Principles

<a name="4.5.3"></a>
<a name="assets-materials-textures"></a>
#### 4.5.3 Materials Should Only Utilize Unique Texture Inputs If They Add Significant Visual Value To The Underlying Asset

Utilize unique textures only if they are absolutely required. Always use pre-existing/tileable textures or a simple parameter if a sufficient visual quality can be achieved that way.


**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="scm"></a>
## 5. Source Control Management

We are using Plastic SCM as our source control management software.

<a name="5.1"></a>
<a name="scm-branches"></a>
### 5.1 Branches

To structure our day to day work and keep the project in a functioning and clean state we use a set of predefined branches and a branch per task workflow.

<pre>
|-- <a href="#scm-branches-main">Main</a>
    |-- <a href="#scm-branches-dev">Dev</a>
        |-- <a href="#scm-branches-tasks">Task001</a>
        |-- <a href="#scm-branches-tasks">Task002</a>
</pre>

<a name="5.1.1"></a>
<a name="scm-branches-main"></a>
#### 5.1.1 Main Branch

Every changeset on the main branch represents a version of the project that has been tested to be stable. Such a version is not necessarily an actual release but should always be polished to a level so it could be shown to external testers, publishers, etc.
There are no direct checkins on the main branch, every changeset is a merge.

<a name="5.1.2"></a>
<a name="scm-branches-dev"></a>
#### 5.1.2 Dev Branch

The Dev branch is a direct child of the main branch. Assets and functionality have to be tested and individually stable before being merged onto this branch. This is the branch that will be tested by QA.
There are no direct checkins on the dev branch, every changeset is a merge. 

<a name="5.1.3"></a>
<a name="scm-branches-tasks"></a>
#### 5.1.3 Task Branches

Task branches are where the actual work is done and checked in. A task can be a bugfix, creating a specific asset or implementing a feature (larger features might be split into several sub-tasks).
Depending on the project task branches can either be created manually or created directly from [JIRA](#scm-jira) issues. Manually created task branches should be prefixed according to the type of work that is done, e.g. feature_, bugfix_, etc.

> When your project uses JIRA or a similar issue tracking software, every task branch should be created from and linked to a tracked issue. This way all necessary informationen about the project's progress is kept in one place.

<a name="5.2"></a>
<a name="scm-checkouts"></a>
### 5.2 Checkouts

To prevent accidentally editing the same file on different branches and thereby creating an unresolvable merge conflict every `.uasset` and `.umap` file is configured for exclusive checkouts. For this to work properly everyone should use the scm plugin built into the engine and make sure to save/checkout every file they want to edit.

> Exclusive checkouts only account for a file's current checkout state and not whether you have the latest revision across branches so some merge conflicts may still happen. For this reason everyone should make sure a map is not being worked on or changed for a different task before editing a umap file.

<a name="5.3"></a>
<a name="scm-checkins"></a>
### 5.3 Checkins

Every checkin must have a descriptive comment. The change resulting from your checkin should be comprehensible from your comment alone without having to look into the list of changed files. Some general hints for writing good comments:

* Avoid using the words `adjusted` or `tweaked` as those are ambiguous. For numeric changes name the direction in which the change occured. For complex adjustments try describing the intended result
* [TODO] need more general hints

You should only change and add files that correlate with your current task and branch. Create or request a new task/branch if refactoring is needed.

Also don't overload checkins. If you changed multiple things which are not related to the same goal you should consider splitting them up into separate checkins.

Checkin comments should start with a 'category', written in CAPS and encapsulated in square [brackets]. Categories allow for a quick distinction. Categories should describe the general type of work you did for this checkin, some common examples can be found in the following table:

| Category        | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| MAPS            | Changes to a level                                          |
| AUDIO           | Changes to audio assets                                     |
| ART             | Changes to any art related assets                           |
| UI              | Widget layouting and UI programming                         |
| DESIGN          | Numbers tweaking and changes to gameplay settings           |
| CODE            | BP and C++ programming                                      |
| PROJECT         | Changes to project settings or other configuration          |
| CLEANUP         | Changes to folder structure, deleting unused files, etc.    |
| MERGE           | See [Merge](#scm-merge)                                     |

If multiple categories match the work you've done and you don't want to split up your checkin either choose the category that fits best or use multiple categories separated by commas.

Should shared plastic credentials be used (such as a freelancer account), add your initials in round brackets after the category. This way every changeset can be mapped to its creator.

<a name="5.3.1"></a>
<a name="scm-checkins-examples"></a>
#### 5.3.1 Examples

Here are some examples of checkin comments and how they could be improved

**Bad**
* [PROJECT] Tweaked settings
* [Code]\(FR) Fixed UserMenu
* [MAPS] Added collision
* [ART] Updated Buggy vehicle

**Good**
* [PROJECT] Increased Reflection Capture Resolution.  Enabled Lumen
* [CODE]\(FR) Fixed runtime errors on dedicated server in UserMenu by adding ded server checks to cosmetic functions
* [MAPS] Fixed missing collision at team2's base in DemoLevel
* [ART] Reimported Buggy vehicle, fixing forward direction

<a name="5.4"></a>
<a name="scm-merge"></a>
### 5.4 Merge

When merging from one branch to another you can add a comment, similar to a checkin comment. For merges these comments should always be formatted `[MERGE] from <source branch name>`.  The destination branch does not need to be mentioned as it is explicitely clear.

**Good**
* `[MERGE] from Dev`
* `[MERGE] from JIRA_CHA-42`

**Bad**
* `[MERGE] Dev to Task`
* `[MERGE] updated`
* `[MERGE] from Dev to JIRA_CHA-69`
* `merged dev`

Merging a task branch to the dev branch should always follow the same procedure:
* The task must have been [reviewed](#scm-review) and approved by the responsible team member.
* Merge the latest changes from dev to the task branch and resolve any pending merge conflicts.
* Make sure the merge didn't break any functionality.
* Merge the task branch to the dev branch

**The dev branch should only ever be merged to the main branch after being validated by an actual playtest.**

<a name="5.5"></a>
<a name="scm-review"></a>
### 5.5 Review Process

Before being merged every task branch has to be reviewed with the following goals in mind:
* The task has been satisfactorily finished
* The result conforms to this styleguide. This primarily means running the linter plugin to check for violations
* The result conforms to project-specific guidelines such as art style or system architecture.

<a name="5.6"></a>
<a name="scm-attributes"></a>
### 5.6 Attributes

To improve readability in branch view and branch explorer we mark task branches with the `Status` attribute to allow filtering out branches that are considered `Done`.  To set the attribute conveniently via a UI action, edit `C:\Users\<User name>\AppData\Local\plastic4\externaltools.conf` and add the following lines:

<pre>
branch | Set branch status to 'Open' | cm | attribute set att:Status @object Open -path="@wkpath"
branch | Set branch status to 'Done' | cm | attribute set att:Status @object Done -path="@wkpath"
</pre>

To set the attribute manually, open a branch's extended information and open the `Attributes` tab. On the bottom, click `Apply Attribute` and select the status attribute and its desired value via dropdown menu in the new window.
![Acceptable](https://github.com/ThreeDeeFlorett/ue5-style-guide/blob/main/images/scm-attributes.png?raw=true "Apply Attribute")

<a name="5.6.1"></a>
<a name="scm-attributes-filtering"></a>
#### 5.6.1 Filtering

To hide done task branches in the branches view edit your query to:

<code>
find branch where not (attribute='Status' and attrvalue='Done')
</code>

In the branch explorer, open `Filters and conditional format`.  Add an exclusion rule with the condition

<code>
attribute = 'Status' and attrvalue = 'Done'
</code>

<a name="5.7"></a>
<a name="scm-jira"></a>
### 5.7 JIRA

This section describes how we integrate our task per branch and reviewing workflows with JIRA.

> Note that the described workflows are somewhat specific for our work on `Charged!` so they might need to be adjusted for other projects.

<a name="5.7.1"></a>
<a name="scm-jira-setup"></a>
#### 5.7.1 Setup

In your Plastic SCM client go to Preferences->Issue Trackers and configure the following settings:
> If you can't find the Issue Trackers settings try switching back to legacy GUI!

 * Bind to this issue tracking system: `Atlassian JIRA`
 * Apply binding to: `Repositories`
 * check `Bind issues to Plastic branches (recommended)`
 * Host: `https://threedee.atlassian.net/`
 * User name: your Atlassian account email address
 * Password: an [API token](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/) you have to create for your Atlassian account
 * Branch prefix: `JIRA_`
 * Project Key: `MULTIPLE_PROJECTS`
 * Custom Field ID: needs to be empty
 * Issue Types: `Bug, Task` (has to match issue types in JIRA)

<a name="5.7.2"></a>
<a name="scm-jira-workflow"></a>
#### 5.7.2 Workflow

This section describes the actual steps and processes necessary for completing a specific task.
Team members involved:
 * `Reporter`: The team lead responsible for the task, e.g. Game Director, Technical Director, Creative Director, etc. 
 * `Assignee`: The team member who is executing the task

1. `Reporter` creates the task in JIRA
2. The task is selected for production, i.e. added to the current/upcoming sprint (Task status = `TO DO`)
3. `Assignee` is either directly assigned to the task by `Reporter` or chooses the task on his own
4. `Assignee` cross-checks specific requirements or creative directions with `Reporter`
5. `Assignee` moves task status -> `In Progress`. JIRA automatically assignes the task to `Assignee`
6. In Plastic, `Assignee` creates a new branch from the task and switches his workspace to the new branch
7. `Assignee` works on his task
8. `Assignee` tests his results to ensure they are working properly. This includes merging in the latest changes from [Dev](#scm-branches-dev)
9. `Assignee` cleans up his task branch
10. `Assignee` moves task status -> `Pending Review`
11. `Reporter` [reviews](#scm-review) the task
12. If the review is rejeced, `Reporter`moves task status -> `In Progress`
13. `Assignee` goes back to 7. and incorporates feedback
14. If the review passes, `Reporter` merges the task branch back to Dev and [marks the branch Done](#scm-attributes)
15. `Reporter` moves task staus -> `Done`

**[⬆ Back to Top](#table-of-contents)**


<a name="6"></a>
<a name="misc"></a>
## 6. Miscellaneous

This section focuses on various topics related to working as a team on Unreal Engine projects.

<a name="6.1"></a>
<a name="misc-ddc"></a>
### 6.1 Shared Derived Data Cache

Many Unreal Engine Assets require additional "derived data" before they can be used, e.g. Shaders have to be compiled for the platform your Editor is running on. Derived data is large, and at times may need regenerating, therefore it is stored in the Derived Data Cache (DDC). As (re)generating takes significant amounts of time, on-site workspaces (LAN/office) should use a so-called Shared Derived Data Cache. This way, only one person needs to build the derived Asset format(s) and they will be automatically available to all other users. There will occasionally be stalls when Assets need to be processed, but the results are stored and shared. Even on a fairly small team, sharing Asset processing work in this way will eliminate most processing time.

To set up Shared DDC:
1. establish NAS connection
2. have "Share" as network drive "T:\\"
3. add system environment variable: "UE-SharedDataCachePath" = "T:\\_SharedResources\UE4DDC"

**[⬆ Back to Top](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**
