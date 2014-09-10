.. metadata-placeholder

:DC.Title:
   Selection of the Questionnaire Management System
:DC.Creator:
   Nery, Fernanda
:DC.Date:
   2013-10-01
:DC.Description:
   Information on the selection of the Questionnaire Management System.
   Based on previous R&D projects.
:DC.Language:
   en
:DC.Format:
   text/x-rst
:DC.Rights:

:DC.RightsHolder:
   Fernanda Néry 2009-2013 © CC BY-SA 3.0 http://creativecommons.org/licenses/by-sa/3.0/


.. _sw-questionnaire-ref:

Questionnaire Management System
*******************************

Requirements
============

Questionnaire management systems

A review of the functionality available
in Blaise 4.5, the Survey Processing System developed by Statistics Netherlands,
was made in order to try and guarantee that
the fundamental requirements where duly identified.

Data model basics
=================

Field definition
   A field definition includes a field name and a field type that defines valid values.
   Usually it will have question text. It can have a description to document the field,
   a field tag, and special attributes.

Rules
   There are four types of rules: routing instructions, edit checks (hard and soft),
   computations, and layout instructions.

   *  Routing instructions describe the data entry order of the fields and the
      conditions under which they will be eligible.

      For computer-assisted interviewing,
      the route specifies the order and conditions in which the fields are asked.

   *  Edit checks determine
      whether a specified statement is true for the values of the fields involved.
      If it is false, the instruction will generate an error.
      What will be done with the error depends on the application at hand.
      Two kinds of edits are supported.
      The CHECK instruction defines a hard error,
      something that must be fixed before the form can be considered clean.
      The SIGNAL instruction defines a soft error, which is a possible problem.
      It can be suppressed or the values of the involved fields may be changed.
      A CHECK is the default.

   *  Computations determine proper routes to process fields,
      carry out complex checks, or derive values.

   *  Layout instructions determine the placement of data entry fields displayed in
      the Data Entry Program.

Fields
------

A field is the basic element of the data set in Blaise.
Fields can have specific types of definitions.
Examples of definition types include strings, numbers, or dates.
You can create your own user-defined types of fields.

You specify fields in the FIELDS section::

   DATAMODEL Commute1 "The National Commuter Survey, first example."
   FIELDS 
       Name "What is your name?" : STRING[20] 
       Town "In which town do you live?" : STRING[20] 
       Gender "Are you male or female?" : 
         (Male, Female) 
       MarStat "What is your marital status?" : 
         (NevMarr "Never married", 
         Married "Married", 
         Divorced "Divorced", 
         Widowed "Widowed") 
       Children "How many children have you given birth to?" : 0..10 
       Age "What is your age?" : 0..120 

In its most simple form, each field definition consists of an identifying name and a specification of the valid values.
A longer text between double quotes will usually be inserted between the name and the value definition.
This text may serve to state a question, as description, or to document the field.

The example above shows string, numeric and enumerated data variables.

Rules
-----

::

   DATAMODEL Commute1 "The National Commuter Survey, first example."
   FIELDS
      <--see example above-->
   RULES
      Name
      Town
      Gender
      MarStat
      Age

The five fields will be processed in this order.
Field names can also be asked, subject to a condition::

   IF (Gender = Female) AND (Age > 12) THEN 
      Children 
   ENDIF

This means that the field Children will only be processed
if the field Gender has the value Female and Age is greater than 12.

Checking
--------

Checks are conditions that have to be satisfied.
You can state the check in terms of what the correct relationship between fields should be:: 

   MarStat = NevMarr "he/she is too young to be married!" 

The specification instructs the system to check
whether the field MarStat has the value NevMarr.
If not, then the edit is invoked.
You can attach text between double quotes to a condition.
Such a text will be used as an error message if the condition is not satisfied.

Checks can be subject to conditions:: 

   IF (Age < 15) 
      "If age of respondent is less than 15" THEN 
      MarStat = NevMarr 
      "then he/she is too young to be married!" 
   ENDIF 
   
The check MarStat = NevMarrwill only be carried out
if the field Age has a value less than 15.
The application will reject entries in which people younger than 15 years are married.

Blocks
------

The following specification contains two block definitions:
the block BPerson and the block BWork::

   DATAMODEL Commute2 "The National Commuter Survey, example 2." 
      BLOCK BPerson "Demographic data of respondent" 
         FIELDS 
            <-- see example above -->  
         RULES 
            <-- see example above -->  
      ENDBLOCK 
      
      BLOCK BWork "Data about work and commuting" 
         FIELDS 
            Working "Do you have a paid job?" : (Yes, No) 
            Descrip "Short description of your job" : STRING[40] 
            Distance "What is the distance to your work (in km)?" : 0..300 
            Travel "How do you travel to your work?" : SET [3] OF 
               (NoTravel "Do not travel, work at home", 
               PubTrans "Public bus, tram or metro", 
               Train "Train", 
               Car "Car or motor cycle", 
               Bicycle "Bicycle", 
               Walk "Walk", 
               Other "Other means of transportation") 
            Commuter "Are you a commuter?" : (Yes, No) 
      RULES 
         Working 
         IF Working = Yes THEN 
            Descrip Distance Travel 
         ENDIF 
         
         IF (Working = Yes) and (Distance > 10) THEN 
            Commuter := Yes 
         ELSE 
            Commuter := No 
         ENDIF 
      ENDBLOCK
       
      FIELDS 
         Person : BPerson 
         Work : BWork; 
      RULES 
         Person 
         Work 
   ENDMODEL 

A block is like a sub-data model with fields and rules.
A block is a special kind of field type. You define a field with the block name as field type::

   FIELDS 
      Person: BPerson


Field tags
----------

Questions on paper questionnaires are often identified using numbers.
A field tag is specified between parentheses after the field name and before the first text::
 
   FieldName (FieldTag) "Text" / "Description" : FieldType 

A field tag may consist of letters and digits,
although usually only digits will be used (to represent question numbers).
The following example illustrates the use of field tags::
 
   Working (101) "Do you have a paid job?" : (Yes, No) 
   Descrip (102) "What is your job description" : STRING[40] 

Field types
-----------

String type
^^^^^^^^^^^

A string field accepts any text as value,
provided the length of the text does not exceed the specified maximum length.
An example::
   
   Name "What is your name? " : STRING[30]

You can test the contents of, or make an assignment to,
a string field using single quote marks::
 
   IF SectionName = 'Household' THEN 
      Label1 := 'Household Roster' 
   ENDIF

It is common to test or assign values between string fields:: 

   IF Name1 <> Name2 THEN 
      Name1 := Name2 
   ENDIF 

To test for an empty string you can use either the word EMPTY or two single quote
marks with no space between them:: 

   IF Name = EMPTY THEN... 
   IF Name = '' THEN 

OPEN type
^^^^^^^^^

For long, open-ended text responses of variable length you can use the OPEN type.
OPEN type fields are useful when the interviewer must record verbatim answers
from respondents.

Integer type
^^^^^^^^^^^^

Integer fields can be defined in several ways:: 

   Age1 "What is your age?" "Age of respondent" : 0..120 
   Age2 "What is your age?" "Age of respondent" : INTEGER[3] 

Decimal or real type
^^^^^^^^^^^^^^^^^^^^

To define a field that accepts decimal numbers,
you can use the following type declarations::
 
   Ticket1 "How much did you pay for your train ticket?" : 0.00..10.00 
   Ticket2 "How much did you pay for your train ticket?" : REAL[5, 2] 
   Ticket3 "How much did you pay for your train ticket?" : REAL[5] 

Enumerated type or precode
^^^^^^^^^^^^^^^^^^^^^^^^^^

An enumerated field can take as a value one of the items in a list of items.
The item is known as a category identifier. A simple example is:: 

   Gender "What is your gender?" : (Male, Female) 

Set type
^^^^^^^^

To allow a respondent to choose more than one item from a list of answers,
use a SET field. A SET field may also be known as a multiple precode or code-all-that-apply.
Consider the following example:: 

   Travel "How do you travel to your work?" : SET [3] OF 
      (NoTravel "Do not travel, work at home", 
      PubTrans "Public bus, tram or metro", 
      Train "Train", 
      Car "Car or motor cycle", 
      Bicycle "Bicycle", 
      Walk "Walk", 
      Other "Other means of transport")
       
The format is the same as that of an enumerated field
with the addition of the reserved words SET [3] OF.
This indicates that, at most, three different category values can be selected.
By specifying SET OF without a number between brackets,
you allow all items to be picked from the list.

Stored values of enumerated and set fields
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The values in enumerated fields and SET fields are stored as code numbers.
The first item in the list is assigned code 1, the second gets code 2, and so on.
You can specify your own code numbers to overrule this coding scheme.
You do that by adding numbers in parentheses between category names and category texts.
Consider the following example:: 

   Travel "How do you travel to your work?" : SET [3] OF 
      (NoTravel (0) "Do not travel, work at home" 
      PubTrans "Public bus, tram or metro", 
      Train "Train", 
      Car (4) "Car or motorcycle", 
      Bicycle "Bicycle", 
      Walk "Walk", 
      Other (9) "Other means of transport") 

This means that NoTravel is coded as 0.
Subsequent values are coded in ascending order until a new code is encountered.
Here PubTrans is coded as 1 and Train as 2.
The codes of the other values are 4 for Car, 5 for Bicycle, 6 for Walk, and 9 for Other.

Date and time type
^^^^^^^^^^^^^^^^^^

A date field is a special field type that only accepts dates as values. For example:: 

   Birth "What is your date of birth?" : DATETYPE 
   TimeTravel "At what time do you start work?" : TIMETYPE 
   
Classification type
^^^^^^^^^^^^^^^^^^^

To perform hierarchical coding, a classification type is needed.

Arrayed fields
^^^^^^^^^^^^^^

An arrayed field defines a series of fields of the same type.

TYPE section
------------

With the TYPE section,
you can define reusable type definitions (or just types),
then use them in later sections::

   TYPE 
      TTravel = SET [3] OF 
            (NoTravel "Do not travel, work at home", 
            PubTrans "Public bus, tram or metro", 
            Train "Train", 
             Car "Car or motor cycle", 
            Bicycle "Bicycle", 
            Walk "Walk", 
            Other "Other means of transport") 
   FIELDS 
      TravelNow "How do you travel to your work at the moment?" : TTravel 
      TravelThen "How did you travel to your work one year ago?" : TTravel 
   RULES 
      TravelNow 
      TravelThen 

A Block may be considered a FieldType.

Type libraries
^^^^^^^^^^^^^^

Survey organisations will find it profitable
to standardise the types that are used in two or more surveys.
This will make programming quicker and make it easier to compare survey results.
Interviewers and data editors will also appreciate the common standards between surveys.
Types can be shared by many applications in two different ways.

They can be incorporated with an INCLUDE statement or they can be stored in a pre-compiled type library.

The type library is prepared just like a data model except that the first key word is
LIBRARY. A very simple type library:: 

   LIBRARY MyLib 
   TYPE 
      TYesNo = (Yes, No) 
      TMarStat = (Single, Married, Divorced) 
   ENDLIBRARY

To use the type library from a data model, name the type library in a LIBRARIES
section. Then, for any field in the data model, refer to any type in the usual
manner. For example:: 

   DATAMODEL UsesLib 
   LIBRARIES MyLib 
   FIELDS 
      WillYou : TYesNo 
      Married : TMarStat 
   ENDMODEL 

Languages
---------

Blaise supports the use of different languages.
This is particularly important if you want to interview people speaking different languages.
During interviewing, the interviewer can change to a different language with a function key.
This requires you to specify the question texts in all languages you might intend to use.
The format for a field definition for two languages is as follows:: 

   FieldName   "Text1" "Text2" / 
               "Description1" "Description2" : FieldType 

You specify the question texts (Text1 and Text2) in different languages, and
specify the descriptions after the slash in the same order.
Here is a concrete example::

   Name  "What is your name?" "Wat is uw naam?" / 
         "Name of respondent" "Naam van de respondent" : STRING[30] 

Enhancing texts
---------------

Hard spacing and line breaking, font, font size, colour, bold, and underline.
Variable text fills.
Auxiliary fields (screen labels, etc.)

Routing rules
-------------

Route field methods
^^^^^^^^^^^^^^^^^^^

Blaise has four methods: CLASSIFY, ASK, SHOW and KEEP. ASK is the default.

CLASSIFY
   The CLASSIFY routing method puts a classification type field on the route,
   to show and edit it.
ASK
   The method ASK shows the field on the screen so the user can enter a value.
SHOW
   The method SHOW shows the field and its value on the screen.
   In the FormPane (page), the user will not be able to land on it
   and will not have the opportunity to change the value.
   You typically SHOW a field to give information to the user, as with a label in the page.
   It is possible to use the mouse to land on a show field,
   but you can not change its value.
KEEP
   The method KEEP means that the field is not shown on the screen.
   The user will not be aware that this field exists.
   The value of the field will be stored in the Blaise data file
   if the field is defined in the FIELDS section,
   but the KEEP is considered to be at the end of the RULES section.

If you SHOW or KEEP a field, its value must be computed.
If a field is computed but otherwise not mentioned in the RULES,
the KEEP method will automatically be applied at the point of computation.

Preventing return to some questions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can use the KEEP method to prevent users from returning to some questions
after they have been answered. This is called a wall. This might be done for
reasons of confidentiality.

Rationale
=========

Analysis of alternatives
========================


