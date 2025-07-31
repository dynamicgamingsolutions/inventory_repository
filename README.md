# Asset Database
## Dynamic Gaming Solutions

The Dynamic Gaming Solutions Asset Database Includes - 
- Slot Master (Table)
- Slot Master (View)
- Asset Table (Table)

## *<a>Table of Contents</a>* 
1. [Glossary](#glossary)


## 1) <a>Glossary</a>
[Top](#table-of-contents)

### SQL References
**Q**

*Query* - The basic construct to communicate with any SQL server. Queries can call information, add, uodate, and delete. Queries can also manipulate information using algorithms, and connect references. Queries can be single use or saved for repeated use.

**R**

*Reference Table* - 

**S**

*SDC* - Slowly Changing Dimensions (SDC) are basic but versatile data structures. The goal of these structures is to keep updated information update through one of three main methods.

- Type 1 SDC: Single value keys are updated with their current values. In reference to serials involving Vendor Cabinets, this would be only showing only the current theme, pay structure, and location.

- Type 2 SDC: Logging all stages of a key with a primary time reference key. This allows multiple states of a single asset to be logged. In reference to serials involving Vendor Cabinets, this would show the history of the cabinet over it's lifetime (or available date). This normally is accompanied with an order or current state reference, along with a last date of change.

- Type 3 SDC: This combines Type 1 and Type 2. While there is only one unique entry, the entry contains columns to list previous states. In reference to serials involving Vendor Cabinets, this might include the current theme, pay structure, and location, along with the most recent theme, pay structure, and location.

**T**

*Table* - A data structure containing raw data in the forms of text, numbers, dates, booleans (true/false), and even JSON (secondary data structures). This is where data is directly stored.

**V**

*View* - A structured query that is accessible similarly to a table. Information is not stored in a view, but can be pulled like a table into Excel, Google AppSheet, and other sources. References, algorithems, and root calls can be used in a view, but cannot be changed later.

2) Slot Master (Table)

The Slot Master Table currentl
