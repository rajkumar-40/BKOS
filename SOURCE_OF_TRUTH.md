BKOS ARCHITECTURE GOVERNANCE RULE

Once a file, folder, entity, module, table, API, or architecture path
is officially declared and committed to the repository:

DO NOT:

- Rename files
- Rename folders
- Rename modules
- Rename entities
- Rename APIs
- Change folder hierarchy
- Change database structure
- Change knowledge graph hierarchy
- Change project sequence

UNLESS:

- A documented architecture review is completed
AND
- Version increment is approved

Changes must be:

Documented
Versioned
Traceable

Rule:

Extend Architecture
Do Not Randomly Modify Architecture

Example:

Valid:

BKOS/database/tables/
├── users.md
├── subjects.md

Future additions:
├── careers.md
├── scholarships.md

Invalid:

Rename:
users.md → students.md

Rename:
database/ → db/

Rename:
knowledge/ → learning/

Without Architecture Review

Single Source Of Truth Applies.
