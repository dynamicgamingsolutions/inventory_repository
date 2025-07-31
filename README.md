# Asset Database
## Dynamic Gaming Solutions

The Dynamic Gaming Solutions Asset Database Includes - 
- Slot Master (Table)
- Slot Master (View)
- Asset Table (Table)

## *<a>Table of Contents</a>* 
1. [Glossary](#1-glossary)
1. [Slot Master (Table)](#2-slot-master-table)


## 1) <a>Glossary</a>
[Top](#table-of-contents)

### SQL References
**Q**

#### *Query*
 - The basic construct to communicate with any SQL server. Queries can call information, add, uodate, and delete. Queries can also manipulate information using algorithms, and connect references. Queries can be single use or saved for repeated use.

**R**

#### *Reference Table*
 - A reference table may also be called a Type 0 SDC. These table are not ment to change (to an extent). While changes may be needed as new information comes out, the changes affect all other tables that use the reference table. For instance, if DGS was working with a casino called "Golden Eagle" in Oklahoma for several years, then comes across another "Golden Eagle" in Kansas, updating the casino reference table entry of Golden Eagle in Oklahoma to "Golden Eagle OK" would change all references of the casino, allowing another "Golden Eagle" to be entered, without having to hunt down all instances of the original.

**S**

#### *SDC*
 - Slowly Changing Dimensions (SDC) are basic but versatile data structures. The goal of these structures is to keep updated information update through one of three main methods.

    - Type 1 SDC: Single value keys are updated with their current values. In reference to serials involving Vendor Cabinets, this would be only showing only the current theme, pay structure, and location.

    - Type 2 SDC: Logging all stages of a key with a primary time reference key. This allows multiple states of a single asset to be logged. In reference to serials involving Vendor Cabinets, this would show the history of the cabinet over it's lifetime (or available date). This normally is accompanied with an order or current state reference, along with a last date of change.

    - Type 3 SDC: This combines Type 1 and Type 2. While there is only one unique entry, the entry contains columns to list previous states. In reference to serials involving Vendor Cabinets, this might include the current theme, pay structure, and location, along with the most recent theme, pay structure, and location.

**T**

#### *<a>Table</a>*
 - A data structure containing raw data in the forms of text, numbers, dates, booleans (true/false), and even JSON (secondary data structures). This is where data is directly stored.

#### *Trigger*
 - A process that acts automatically upon `INSERT`, `UPDATE`, or `DELETE`, without the need for user intervention. Triggers can run calculations to fill in related columns, update information on other rows, insert rows into other tables, and  many other processes. 

**V**

#### *View*
 - A structured query that is accessible similarly to a [table](#table). Information is not stored in a view, but can be pulled like a table into Excel, Google AppSheet, and other sources. References, algorithems, and root calls can be used in a view, but cannot be changed later.

#### Google AppSheet References

**A**

#### *<a>Actions</a>* 
- A single click button that initiates some action. Actions can include going to a different view within the app, going to a different AppSheet app, go to an external website, auto-setting column values, exporting/importing views as a CSV file, or stringing together multiple actions. Unlike [bots](#bots), actions require the user to initiate the action directly.

**B**

#### *Bots*
 - Bots can run everything actions do, along with calling actions, adding conditional and branching logic, send emails and chats, and call Google App Scripts. Bots are not triggered manually like [actions](#actions), but are set to run when certain conditions are met.

**D**

#### *Data*
 - This is any source that Google AppSheet pulls from. There are several different sources that can be used.
    - Google Sheets - Simple to work with, but easy to mess up. Google AppSheet requires its data structures to be a stable and consistent as possible. While Google Sheets is something that many people are capable of using on a basic level, that can lead to the temptation to interact with it and belief that AppSheets runs as simply as Sheets. This can cause massive errors, and corrupt column formulas and references.

    - SQL - While SQL comes in many different "flavors", they still share many roots. Unless a dedicated GUI (Graphic User Interface) is applied, most interactions with any SQL database is going to be through a IDE (Integrated Development Environment). This is where you might see an entry similar to the following - 

        ```sql
        USE analytics
        GO
        SELECT * FROM slot_master
        ```
        AppSheets works as a GUI, allowing common users to interact with the data, while protecting it by simple "barrier to entry" principles. The harder it is to change something, the harder it is to breake it. The data that comes in can be fully edited through AppSheets, and filtered using [slices](#slice).

**K**

#### *<a>Key</a>*
 - A single column that contains unique identifiers for each row. Keys exist for both reference and standard data sets. The default key is the row number, but should be replaced with another column. **Note:** *Duplicate key entries can result in broken references and mismatched data.*

**L**

#### *<a>Label</a>*
 - Columns displayed for quick reference and used as headers for the information. Data can have one non-image label and one image label. The best labels are the ones that most users would recognize as what the entry is. 

**R**

#### *<a>References</a>*
 - Connections between tables and related information. The most common way to use references is to call a row's [key](#key), rather than inserting the information directly. References allow users to update an individual row, and have all references be updated simultaneously. When a reference is used to display values from another column, the value displayed is the label. References can also be applied as `ref_row()`, which can call a table view of the referenced data within either a detail or deck view. Columns using `ref_row()` are [virtual columns](#virtual-column) where the data within cannot be edited.

**S**

#### *<a>Slice</a>*
 - Filtered versions of data sets using formulas. When a slice is created, restrictions can be applied to the data coming through, along with filtering out entire columns as well. Slices can be applied to views exactly like datasets, including having auto generated [reference views](#references). If a data set is removed and a slice was attached, the slice will not automatically be removed. 

**V**

#### *View*
 - Any area that displays data is a view, and multiple views can be seen at once. Views come in several types and positions.
    1) Types:
        - Table - Simple rows and columns to display data, similar to an Excel table setup.
        - Deck - Similar to a Table, Decks come in row formats, but only show basic information. Unlike a table, a Deck can store reference links and reference tables directly, rather than requiring a detail view to hold that information.
        - Gallery - Like a Deck, it only shows limited information. The information is limited to the "[Label](#label)" and an image. All other information is pulled from a Detail view.
        - Map - If addressed or longitude & latitude columns are available, then a map can show the location of entries on an integrated Google Maps view.
        - Calendar - If date information is available, then a calendar is available with both start and end dates as options. If time is also available, then start and end times are also available. **Time options cannot be applied without a date.**
        - Chart - Gives multiple chart options to plot numerical data. The non-image "[Label](#label)" column is used to mark the data, and multiple number columns can be used to display data and relations for comparisons. 
        - Card - Gives both simple information and image options that can be in a single view, along with options for up to four actions.
        - Onboarding - Takes data and prompts the individual to run through each row individually. This is useful for basic instructions, or for introducing new views or features.
        - Dashboard - This can host multiple views that would not normally be viewable together in one view. All the above mentioned view types can be shown in a dashboard, and accessed independently from it.
        - Detail - A reference view based on the information in the data set of the view currently displayed. This allows users to drill down to show as much information as needed for each row. Detail views cannot be opened in Dashboards, but are one of the view that can be shown concurrently in other views. Detail views will appear on the right side of the screen when an entry is selected. Detail views can also link and display [references](#references) for the data within the view, including detail drill downs and reference row tables.
        - Form - Same as Detail, but for either adding or editing rows. If adding a row, and blank form will generate, while editing generated a form with the current row's information on it. Columns can be restricted from editing, required, have its information auto-generated, or hidden. [Virtual Columns](#virtual-column) cannot be edited.
    2) Positions:
        - Primary - These positions are reserved for the top few spots on desktop, or the persistent buttons at the bottom for mobil. These positions are always visible.
        - Menu - These positions fall below the Primary on desktop, and are hidden behind the menu button on mobil.
        - <a>Reference</a> - These positions are hidden from menu navigation, but can be accessed through [actions](#actions). Form and Detail views are common reference views, but specific filtered views from [slices](#slice) can be set as references.

#### *<a>Virtual Column</a>*
 - Columns that can be generated using other columns from the data set or other data sets within the application. Virtual columns are often used for basic math operations, connecting groups of text, or referencing other data sets. Virtual columns do not store data, and are not editable in form views.


## 2) <a>Slot Master (Table)</a>
[Top](#table-of-contents)

The Slot Master Table
