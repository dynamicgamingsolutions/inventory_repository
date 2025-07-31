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

*Query* - The basic construct to communicate with any SQL server. Queries can call information, add, uodate, and delete. Queries can also manipulate information using algorithms, and connect references. Queries can be single use or saved for repeated use.

**R**

*Reference Table* - A reference table may also be called a Type 0 SDC. These table are not ment to change (to an extent). While changes may be needed as new information comes out, the changes affect all other tables that use the reference table. For instance, if DGS was working with a casino called "Golden Eagle" in Oklahoma for several years, then comes across another "Golden Eagle" in Kansas, updating the casino reference table entry of Golden Eagle in Oklahoma to "Golden Eagle OK" would change all references of the casino, allowing another "Golden Eagle" to be entered, without having to hunt down all instances of the original.

**S**

*SDC* - Slowly Changing Dimensions (SDC) are basic but versatile data structures. The goal of these structures is to keep updated information update through one of three main methods.

- Type 1 SDC: Single value keys are updated with their current values. In reference to serials involving Vendor Cabinets, this would be only showing only the current theme, pay structure, and location.

- Type 2 SDC: Logging all stages of a key with a primary time reference key. This allows multiple states of a single asset to be logged. In reference to serials involving Vendor Cabinets, this would show the history of the cabinet over it's lifetime (or available date). This normally is accompanied with an order or current state reference, along with a last date of change.

- Type 3 SDC: This combines Type 1 and Type 2. While there is only one unique entry, the entry contains columns to list previous states. In reference to serials involving Vendor Cabinets, this might include the current theme, pay structure, and location, along with the most recent theme, pay structure, and location.

**T**

*Table* - A data structure containing raw data in the forms of text, numbers, dates, booleans (true/false), and even JSON (secondary data structures). This is where data is directly stored.

**V**

*View* - A structured query that is accessible similarly to a table. Information is not stored in a view, but can be pulled like a table into Excel, Google AppSheet, and other sources. References, algorithems, and root calls can be used in a view, but cannot be changed later.

### Google AppSheet References

**D*

*Data* - This is any source that Google AppSheet pulls from. There are several different sources that can be used.
- Google Sheets - Simple to work with, but easy to mess up. Google AppSheet requires its data structures to be a stable and inmoving as possible. While Google Sheets is something that may people are capable of using on a basic level, that can lead to the temptation to interact and belief that AppSheets runs as simply as Sheets. This can caues massive errors, and lose column formulas and references.

- SQL - While SQL comes in many different "flavors", they still share many roots. Unless a dedicated GUI (Graphic User Interface) is applied, most interations with any SQL database is going to be through a IDE (Integrated Development Environment). This is where you might see an entry similar to the following - 

    ```sql
    USE analytics
    GO
    SELECT * FROM slot_master
    ```
    AppSheets works as a GUI, allowing common users to interact with the data, while protecting it by simple "barrier to entry" principles. The harder it is to change something, the harder it is to breake it. 


## 2) <a>Slot Master (Table)</a>
[Top](#table-of-contents)

The Slot Master Table
