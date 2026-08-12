TABLE NAME

topics

PURPOSE

Store topics under chapters.

A topic belongs to one chapter.

A topic can contain multiple concepts.

FIELDS

topic_id

subject_id

chapter_id

topic_code

topic_name

topic_description

topic_objective

estimated_learning_time

difficulty_level

display_order

language

version

status

created_at

updated_at

FIELD DESCRIPTIONS

topic_id

Unique topic identifier.

Example:
TOP-PHY-001

------------------------------------------------

subject_id

Reference to parent subject.

Example:
SUB-PHY-001

------------------------------------------------

chapter_id

Reference to parent chapter.

Example:
CH-PHY-001

------------------------------------------------

topic_code

Unique topic code.

Example:
TOP-MOTION-001

------------------------------------------------

topic_name

Official topic name.

Example:
Velocity

------------------------------------------------

topic_description

Brief explanation of topic.

------------------------------------------------

topic_objective

Learning objective.

Example:

Understand velocity,
direction of motion,
and practical applications.

------------------------------------------------

estimated_learning_time

Example:

15 Minutes

30 Minutes

1 Hour

------------------------------------------------

difficulty_level

Beginner

Intermediate

Advanced

------------------------------------------------

display_order

Topic sequence inside chapter.

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

Current topic version.

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

Last updated date.

RELATIONSHIPS

Subject
↓
Chapter
↓
Topic

Topic
↓
Concepts

Topic
↓
Questions

Topic
↓
Practice

Topic
↓
Revision

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

topic_id

TOP-PHY-001

topic_name

Velocity

difficulty_level

Beginner

display_order

2

status

Published

BKOS RULES

Every topic must belong to one chapter.

A topic cannot exist without a chapter.

Every concept must belong to a topic.

No orphan topics allowed.

VERSION

1.0
