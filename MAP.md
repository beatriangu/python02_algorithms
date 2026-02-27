🧭 MAP.md — Python Garden · Data Guard
python02_data_guard — Error Handling & Resilient Systems

This document is my learning and design map.
It explains how my understanding of error handling evolves throughout the python02_data_guard module.

It does not only describe what the code does —
it explains why it is designed that way.

🌱 Core Idea

Move from:

❌ “My program crashes when something fails”
to
✅ “My program anticipates failures and manages them”

A professional system:

detects errors

classifies them

communicates them clearly

cleans resources

continues running

The goal is not to avoid errors.
The goal is to make them manageable.

🟢 ex0 — Agricultural Data Validation Pipeline
🎯 Focus

→ First real contact with runtime errors.

🧠 I Learn

try / except

Implicit ValueError

Validation of external data (sensors / input)

🧩 Mental Model

External data is not reliable.

🔗 Prepares For

Not trusting input() blindly

Treating failure as normal, not exceptional

🟢 ex1 — Different Types of Problems
🎯 Focus

→ Not all errors are the same.

🧠 I Learn

ValueError

ZeroDivisionError

FileNotFoundError

KeyError

Multiple exception handling

🧩 Mental Model

Python classifies errors by nature.
Catching correctly means understanding the problem.

🔗 Depends On

Basic try / except (ex0)

🔗 Prepares For

Designing meaningful domain errors

🟢 ex2 — Creating Custom Error Types
🎯 Focus

→ Domain-specific error meaning.

🧠 I Learn

Creating custom exception classes

Inheritance between exceptions

Catching by hierarchy

🧩 Mental Model

Not every error is technical.
Some errors belong to the domain.

GardenError
 ├── PlantError
 └── WaterError
🔗 Depends On

Understanding built-in exception types (ex1)

🔗 Prepares For

Large, structured systems

🟢 ex3 — The Finally Block: Always Clean Up
🎯 Focus

→ Cleanup must always happen.

🧠 I Learn

finally

Guaranteed cleanup

Conscious resource management

🧩 Mental Model

Errors may happen.
Cleanup must not fail.

try
 ├── operation
except
 ├── error handling
finally
 └── cleanup ALWAYS
🔗 Depends On

Solid try / except understanding (ex0–ex2)

🔗 Prepares For

Systems that leave no broken state

🟢 ex4 — Raising Your Own Errors
🎯 Focus

→ Intentionally detecting invalid states.

🧠 I Learn

raise

Separating:

error detection

error handling

Writing clear and useful error messages

🧩 Mental Model

Not all errors come from Python.
Sometimes your program decides something is wrong.

🔗 Depends On

Custom exceptions (ex2)

🔗 Prepares For

Systems with explicit and enforceable rules

🟢 ex5 — Garden Management System
🎯 Focus

→ Building a complete resilient system.

🧠 Integrates

try / except

Custom exceptions

raise

finally

System recovery

🧩 Final Insight

The system:

fails

informs

recovers

continues

📐 Mental Architecture
GardenManager
 ├── add_plant()
 ├── water_plants()
 │    └── try / except / finally
 ├── check_plant_health()
 │    └── raise ValueError
 └── global handling of GardenError
🧠 Global Module Evolution
ex0 → detect errors
ex1 → classify them
ex2 → name them
ex3 → always clean up
ex4 → raise intentionally
ex5 → integrate everything

These are not isolated exercises.
They are training in resilience.

🎯 Final Objective

Be able to explain:

what can fail

how it is detected

how it is communicated

how resources are cleaned

how the system stays alive

This MAP reflects my mental architecture of the module
and how I design defensive systems in Python.
