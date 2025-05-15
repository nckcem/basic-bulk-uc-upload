<!-- omit in toc -->
# Autodesk $\rightarrow$ Credo AI: Use Case Bulk Upload
This tool converts a *CSV of use cases* into a *formatted JSON array* for Credo AI's bulk upload feature, according to *Autodesk's personal context* for AI use cases.

<!-- omit in toc -->
## 🗂️ Table of Contents
[TOC]

## 🗺️ Overview
- Each row in the input CSV represents a *single* use case (to be transformed into a *single* JSON dict).
- The script generates a JSON file (a *list of dicts*) of use cases formatted to the schema defined [here](./docs/use-case-schema.json).
- Optional *metadata* like Jira tickets and prompts are embedded in each use case's *description*.

## 🔁 Mapping Rules
| CSV Column            | JSON Field          | Notes                                   |
| --------------------- | ------------------- | --------------------------------------- |
| `generative_ai_tool`  | `name`              | Name of the use case                    |
| `purpose_of_use`      | `description`       | Appended under "Purpose of Use"         |
| `response_to_request` | `description`       | Appended under "Response to Request"    |
| `Prompts`             | `description`       | Appended under "Prompts"                |
| `ticket_number`       | `description`       | Appended at the end                     |
| `jira_ticket`         | `description`       | Appended at the end                     |
| `status`              | `governance_status` | Mapped to integer (e.g. "Approved" → 1) |

## 🧰 Requirements
- Python `>= 3.8`
- Install required packages with: `pip install -r requirements.txt`
- See [`requirements.txt`](./requirements.txt) for specifics.

## 🛠️ Support
- ***Coordinate with your Credo AI technical contact*** before running a bulk upload.
- Review the [official Credo AI bulk upload docs](https://knowledge.credo.ai/bulk-use-case-upload).
  - *Pay special attention to the **"Things to note"** section.*