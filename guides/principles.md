# Engineering Principles

## General

- **Do** tackle the difficult things early. Tough tasks left lurking can manifest 
into large blockers!
- **Do** consider testing as early in the engineering process as possible.
- **Do**  focus on the non-functionals
(security/performance/redundancy/scaling/accessibility/supportability) and ensure
 that these are factored into deliverables as required (it’s ok to make it work,
  then make it fast/secure/accessible).
- **Do** ensure an MVP (steel thread) implementation is reached as early in the
 engineering process as possible.
- **Do** try to deliver small incremental changes over large late arriving changesets.
- **Do** ask questions. Never assume an idea is wrong (or right!), or that all
 angles have been covered/considered.
- **Do** look to re-use technology or frameworks used on other Shed projects,
 this will promote portability and common knowledge.
- **Do** ensure local development environment are easy to setup and work on
 everyone’s machine.
- **Do** ensure architectures are documented, especially where a codebase
 contributes to a wider eco-system.
- **Do** embrace YAGNI (“You Ain’t Gonna Need It”). In an effort to steer away
 from over-engineering, build what is needed, not what might be needed.

## Code

- **Do** make use of language specific standards that promote consistency,
 where tooling or guidance is available:
- **Do** ensure code is appropriately documented, ensuring complexity is clarified.
- **Do** ensure code can withstand exceptions. Errors should be handled and
 logged with feedback where suitable.
- **Do** ensure code is maintainable and readable. Strive for clear separation
 of concerns.
- **Do** ensure code is testable. Aim for code that encapsulates single
 responsibilities to enable units of testable logic.
- **Do** make use of integration tests where logic or data outcomes rely
 on more than one code asset or service.
- **Do** include appropriate levels of logging within a codebase, having clear
 outputs saves time and effort when reviewing issues or outputs
  in non-development environments.
- **Do** enforce consistent source control standards. This includes commit
 messages, branch names, merge policies and review criteria.
- **Do** ensure code is committed often with suitable
 checks and guards (Continuous Integration).
- **Do** ensure code is deployed often with suitable
 checks and guards (Continuous Deployment).
- **Do** adhere to DRY principles. If the same logic
 exists in multiple places, it is much harder to maintain.
- **Do** appropriate testing. Strike a balance between
 valuable tests (logic that is subject to change, not boilerplate)
  and end-to-end coverage via integration testing.

## Automation

- **Do** ensure deployment, administration and development tasks
 that happen frequently,
 are automated to save time
 and reduce the likelihood of errors.
- **Do** look to implement automation early in the engineering process
 to enhance output and productivity.
- **Do** ensure that deployments are reliable, safe and repeatable.

## Cloud

- **Do** use cloud services over self-managed or virtual instances e.g.,
 AWS Lambda Services over EC2 Services.
- **Do** take advantage of the cloud scaling capabilities but be wary of cost implications.
- **Do** assume cloud services will fail and ensure such eventualities are
 considered and potentially mitigated.
- **Do** ensure housekeeping is undertaken; cloud costs can spiral if
 unused resources are not disposed.

## Database

- **Do** design your data model up front.
 This includes your entity and attribute naming. 
 It doesn’t have to be perfect but having an entity-relationship (ER) diagram will
  help aide understanding for your fellow developers.
- **Do** adopt (and document) a consistent naming convention
 (lower-case with underscores as separators is preferred).
- **Do** consider performance early, ensure consideration is made around how
 data will be used and include suitable hooks that ensure data access is timely
  e.g., suitable indexing, constraints, views and table structures.
- **Do** ensure deployment and schema migration is automated
 and well proven so it is a simple automated step of a deployment process.
- **Do** consider how a database will scale
 and factor this into costing and potential performance of a service.
- **Do** consider open-source database technologies e.g.,
 Postgres SQL as a datastore. Where we know savings can be made
  commercially by avoiding databases that are tied to license agreements.
- **Do** make use of No-SQL datastores where uses cases are suitable e.g.,
 storing reference data is a great use case for AWS Dynamo DB.

## Source Control

- **Do** ensure any solution is wired into source control.
- **Do** ensure source-controlled assets are protected by
 a suitable branching strategy and
 a clear code promotion path is documented and followed.
- **Do** consider when a separate code repository is required,
 a mono repository is often sufficient for most small projects,
  but multiple repositories maybe required (sensible) where
   autonomy allows for independent changes.






