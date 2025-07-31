# Asset Database
## Dynamic Gaming Solutions

The Dynamic Gaming Solutions Asset Database Includes - 
- Slot Master (Table)
- Slot Master (View)

## *<a>Table of Contents</a>* 
1. [Glossary](#1-glossary)
2. [Slot Master (Table)](#2-slot-master-table)
3. [Slot Master (View)](#3-slot-master-view)
4. [Slot Master (References)](#4-slot-master-references)
5. [Slot Master (Features)](#5-slot-master-features)


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

#### *View (MSSQL)*
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
 - Filtered versions of [data sets](#data) using formulas. When a slice is created, restrictions can be applied to the data coming through, along with filtering out entire columns as well. Slices can be applied to views exactly like datasets, including having auto generated [reference views](#references). If a data set is removed and a slice was attached, the slice will not automatically be removed. 

**V**

#### *View (AppSheet)*
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

The Slot Master Table stores the historical Slot Master with data spanning back to January 6th, 2023. It exists as a [Type 2 SDC](#sdc) with an "active" column that acts as a binary switch. The way the Slot Master Table is updated is through a custom program that reads the "Confirmed Work Performed" page from the Field Service Report, ***FSR***, after the work is complete and the project information has been updated. 

The program, ***Dynamic Analysis***, looks for the sheet listed as Confirmed Work Performed and determines the layout of the project form, what work was performed, where the work was, and the associated serial numbers. Any work performed that would remove the current entry, such as Convert From, Removal, Bank Move From, or Reconfigure From, finds the serial number associated with the entry and changes it from "Active" to "Inactive". Work that would add a new row, such as Convert To, Install, Bank Move To, or Reconfigure To, takes the information in each row, runs it through a fuzzy match to make sure the information is correct, and inserts it into the Slot Master Table as "Active", with incrementing [key values](#key).

Since the Slot Master Table holds direct information, as opposed to using a [referenced table](#reference-table), updating themes, cabinet, vendors, or any other repeating information has to be done in bulk. Depending on access permissions, some users do have access to the direct Slot Master Table through AppSheets. Editing the Slot Master Table should be done carefully, as the [Slot Master View](#3-slot-master-view) relies on the data in the Slot Master Table to be exact. A single character off in a Theme, Cabinet, or Vendor will result in that entry not being referenced.

## 3) <a>Slot Master (View)</a>
[Top](#table-of-contents)

The Slot Master View, as the name suggests, is a built out [MSSQL View](#view-mssql). Slot Master View is made by passing the [Slot Master Tabe](#2-slot-master-table) through reference tables, matching on the reference table output, rather than the reference key. When joined this way, Slot Master View returns a pre-reference version of the Slot Master Table. This is done to connect references for Themes, Cabinets, Vendors, Casinos, Tribes, States, Bill Validators, Printers, and Player Tracking Systems in AppSheets, and giving the user the ability to see other entries related to what they are looking at. The goal is to connect as many different data sources together, allowing the user to get a bigger picture and a more rounded understanding of where everything is.

## 4) <a>Slot Master (References)</a>
[Top](#table-of-contents)

The Slot Master AppSheet View pulls from the [Slot Master View](#3-slot-master-view), and uses the [Reference IDs](#references) to connect different tables. In the back end, the Reference IDs will be labeled with a relevant name, followed by "_id". 
> *e.g. The unique reference key for **Casinos** in a table calling it will be **casino_id**.* 

The casino_id in the Slot Master AppSheet View can pull any information from the casinos data set. As mentioned in the [glossary](#1-glossary), this is done by setting unique IDs for each casino, labeled **reference_key**. The reference_key is set as the [key](#key) in AppSheets, and the same key is what is passed through with Slot Master View.

> *e.g, 4 Bears Casino & Lodge has the reference_key "CT-00139", along with all information that pertains to 4 Bears Casino & Lodge as a property. The cabinet with the serial number BB-10725 has CT-00139 set as the casino_id. When casino_id is set as a reference to Casinos, casino_id searches Casinos to find the key that matches, and returns the label, which is the casino's name.*

Because of this, if a user wished to update the information of a single reference, Theme for example, instead of searching for every instance of that theme within Slot Master, the user could simply update the Theme in the Theme data set. This also means that any data related to the Theme data set can also be referenced.

***Slot Master Reference List***</br>
*The numbers next to each header is the call number for the list. Clicking on the superscript number matching it next to a value ending in "ID" will jump you back to the list it represents. This is how references work. From Slot Master at the bottom, you could jump to any table and all the table's data without scrolling.*

- #### *Tribes [1]*
    - Tribe Name
    - Master Revenue Reference
    - State ID <sup>[5](#states-5)</sup>

- #### *Vendors [2]*
    - Vendor Name

- #### *Cabinets [3]*
    - Cabinet Name
    - Vendor ID <sup>[2](#vendors-2)</sup>

- #### *Themes [4]*
    - Theme Name
    - Vendor ID <sup>[2](#vendors-2)</sup>
    - Cabinet ID <sup>[3](#cabinets-3)</sup>

- #### *States [5]*
    - State Name
    - State Abbreviation

- #### *Bill Validators [6]*
    - Bill Validator

- #### *Printers [7]*
    - Printer

- #### *Player Tracking [8]*
    - Player Tracker

- #### *Casinos [9]*
    - Casino Name
    - Tribe ID <sup>[1](#tribes-1)</sup>
    - State ID <sup>[5](#states-5)</sup>
    - Theme ID <sup>[4](#themes-4)</sup>
    - Cabinet ID <sup>[3](#cabinets-3)</sup>
    - Vendor ID <sup>[2](#vendors-2)</sup>
    - Legal Entity
    - Master Revenue Reference
    - Project abbreviation
    - House Average
    - Number of Machines
    - Address
    - Sales Rep
    - Bill Validator ID <sup>[6](#bill-validators-6)</sup>
    - Printer ID <sup>[7](#printers-7)</sup>
    - Player Tracker ID <sup>[8](#player-tracking-8)</sup>
    - Available Vendors <sup>[2](#vendors-2)</sup>


## Slot Master List
- Casino ID <sup>[9](#casinos-9)</sup>
- Tribe ID <sup>[1](#tribes-1)</sup>
- State ID <sup>[5](#states-5)</sup>
- Theme ID <sup>[4](#themes-4)</sup>
- Cabinet ID <sup>[3](#cabinets-3)</sup>
- Vendor ID <sup>[2](#vendors-2)</sup>
- Bill Validator ID <sup>[6](#bill-validators-6)</sup>
- Printer ID <sup>[7](#printers-7)</sup>
- Player Tracker ID <sup>[8](#player-tracking-8)</sup>
- Denom
- Hold
- Program Media
- Boot bios
- Operating System
- Conversion/Install dates

## 5) <a>Slot Master (Features)</a>
[Top](#table-of-contents)

There are two ways to get to the Slot Master in AppSheets. First is a Slot Master button on the menu that gets the user to a full list of all active machines. This view is used for total counts of vendors, cabinets, and themes. The second is through the casino view. Clicking on a casino with active machines will open the casino detail view on the right hand side of the screen. The top section will have casino specific information, the bottom will have a [reference list](#references) from Slot Master with a button that says "Expand" underneath. Clicking "Expand" will take the user to a version of Slot Master, but filtered for only active themes in the casino selected. 
