TABLE NAME

chapters

PURPOSE

Store chapter information for every subject.

A chapter belongs to one subject.

A chapter can contain multiple topics.

FIELDS

chapter_id

subject_id

chapter_code

chapter_name

chapter_description

chapter_objective

estimated_learning_time

difficulty_level

display_order

language

version

status

created_at

updated_at

FIELD DESCRIPTIONS

chapter_id

Unique chapter identifier.

Example:
CH-PHY-001

------------------------------------------------

subject_id

Reference to parent subject.

Example:
SUB-PHY-001

------------------------------------------------

chapter_code

Short code for chapter.

Example:
MOTION001

------------------------------------------------

chapter_name

Official chapter name.

Example:
Motion

------------------------------------------------

chapter_description

Brief explanation of chapter.

------------------------------------------------

chapter_objective

Learning objective for student.

Example:

Understand speed, velocity,
acceleration and motion.

------------------------------------------------

estimated_learning_time

Average time required.

Example:

2 Hours

5 Hours

10 Hours

------------------------------------------------

difficulty_level

Beginner

Intermediate

Advanced

------------------------------------------------

display_order

Chapter sequence inside subject.

Example:

1
2
3
4

------------------------------------------------

language

English

Hindi

Marathi

------------------------------------------------

version

Current content version.

Example:

1.0

------------------------------------------------

status

Draft

Published

Archived

------------------------------------------------

created_at

Record creation date.

------------------------------------------------

updated_at

Last modification date.

RELATIONSHIPS

Subject
↓
Chapter

Chapter
↓
Topics

Chapter
↓
Concepts

Chapter
↓
Questions

DEPENDENCY FLOW

Subject
↓
Chapter
↓
Topic
↓
Concept
↓
Question

EXAMPLE

subject_id

SUB-PHY-001

chapter_id

CH-PHY-001

chapter_name

Motion

difficulty_level

Beginner

display_order

1

status

Published

BKOS RULES

Every chapter must belong to one subject.

A chapter cannot exist without a subject.

Every topic must belong to a chapter.

No orphan chapters allowed.

VERSION

1.0
