# Entity‑Relationship Diagram (ERD) & DDL  
**By: Taran Schlichtmann**
**Date: 11/07/2025**

Data Modeling and Schema Design Using Snowflake Standards

Focused on designing a normalized data model, constructing an ERD using crow’s foot notation, and generating Snowflake‑compatible DDL. The assignment uses crime data from San Francisco and emphasizes clean schema design, proper key structure, and accurate data types.

------------------------------------------------------------
Overview
------------------------------------------------------------

This assignment demonstrates proficiency in:

- Translating raw data files into a structured relational schema  
- Designing an ERD using crow’s foot notation  
- Identifying primary keys and foreign key relationships  
- Applying Snowflake‑compatible data types  
- Generating DDL that accurately reflects the ERD  
- Using Lucidchart to model entities and relationships  

The final deliverables include both the ERD (PDF) and the DDL (text file).

------------------------------------------------------------
Repository Contents
------------------------------------------------------------

GB882_Assignment 7_ERD_Schlichtmann_T.pdf  
    The completed ERD diagram exported from Lucidchart.

GB882_Assignment 7_ERD DDL_Schlichtmann_T.txt  
    The Snowflake DDL used to create the schema.

README.md  
    Documentation and context for the assignment.

------------------------------------------------------------
Data Model Summary
------------------------------------------------------------

The assignment required building an ERD for crime‑related data.  
The final schema includes two core entities:

### **Dates**
Stores calendar‑level attributes for each date.

Key fields:
- `date_id` (PK)  
- `date`  
- `day_of_week`  
- `holiday`  

### **Incidents**
Stores individual crime incidents and links each incident to a date.

Key fields:
- `incident_id` (PK)  
- `category`  
- `description`  
- `resolution`  
- `longitude`  
- `latitude`  
- `timestamp`  
- `date_id` (FK → Dates.date_id)

### **Relationship**
- **One‑to‑Many**: A single date can be associated with many incidents.  
- Represented using crow’s foot notation in the ERD.

------------------------------------------------------------
DDL Summary
------------------------------------------------------------

The DDL includes:

- Table creation statements for `Dates` and `Incidents`  
- Primary key constraints  
- Foreign key constraints  
- Snowflake‑compatible data types (INT, DATE, STRING, BOOLEAN, FLOAT, TIMESTAMP)

Example excerpt:

CREATE TABLE Dates (
date_id INT,
date DATE,
day_of_week STRING,
holiday BOOLEAN,
PRIMARY KEY (date_id)
);

CREATE TABLE Incidents (
incident_id INT,
category STRING,
description STRING,
resolution STRING,
longitude FLOAT,
latitude FLOAT,
timestamp TIMESTAMP,
date_id INT,
PRIMARY KEY (incident_id),
FOREIGN KEY (date_id) REFERENCES Dates(date_id)
);

------------------------------------------------------------
Tools & Technologies
------------------------------------------------------------

- Lucidchart (ERD modeling)  
- Snowflake SQL (DDL creation)  
- PDF export for diagram documentation  

------------------------------------------------------------
Skills Demonstrated
------------------------------------------------------------

- Relational data modeling  
- ERD design using crow’s foot notation  
- Schema normalization  
- Key and constraint definition  
- Translating conceptual models into DDL  
- Professional documentation and reproducible workflow  
