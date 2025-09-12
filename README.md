<!-- omit in toc -->
# Credo AI: Use Case Bulk Upload
This tool converts a *CSV of use cases* into *formatted JSON* for Credo AI's Bulk Upload feature, according to ***personal context*** for AI use cases.
- From the app homepage, the bulk upload feature is found via:
  - **AI registry > Use cases > ${\underline{\uparrow}}$**.
    - $\underline{\uparrow}$ is the button for bulk upload (left of the `+ Add use case` button).

<!-- omit in toc -->
## 🗂️ Table of Contents
<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [🗺️ 1. Overview](#️-1-overview)
- [🔁 2. Mapping Rules](#-2-mapping-rules)
- [🐣 3. Simple Example](#-3-simple-example)
- [🕹️ 4. Usage](#️-4-usage)
  - [🧰 4.1 Requirements](#-41-requirements)
  - [🛠️ 4.2 Support](#️-42-support)

<!-- TOC end -->

<!-- TOC --><a name="-1-overview"></a>
## 🗺️ 1. Overview
- Each *row* in the input CSV represents a *single* use case, to be transformed into a *single* JSON dict, which is then added to a running list.
- Once all JSON dicts are appended, they're wrapped in a properly formatted payload for Credo AI’s Bulk Upload feature (per the [defined schema](./docs/use-case-schema.json)).
- Optional *metadata* like Jira tickets and prompts are embedded in each use case's *description*.
- The formatted payload is then dumped to a JSON file.

<!-- TOC --><a name="-2-mapping-rules"></a>
## 🔁 2. Mapping Rules
| CSV Column            | JSON Field          | Notes                                   |
| --------------------- | ------------------- | --------------------------------------- |
| `use_case_name`       | `name`              | Name of the use case                    |
| `purpose_of_use`      | `description`       | Appended under "Purpose of Use"         |
| `response_to_request` | `description`       | Appended under "Response to Request"    |
| `prompts`             | `description`       | Appended under "Prompts"                |
| `product`             | `description`       | Appended under "Product"                |
| `ticket_number`       | `description`       | Appended under "Ticket Number"          |
| `jira_ticket`         | `description`       | Appended under "JIRA Ticket"            |

<!-- TOC --><a name="-3-simple-example"></a>
## 🐣 3. Simple Example
The JSON below is formatted for Credo AI's Bulk Upload and represents *two* use cases. In this small example, for each use case, optional metadata in the description field is *not* included.
```json
{
   "data":{
      "items":[
         {
            "name":"Customer Use Case Demo #1",
            "description":"The very first Customer AI use case to be uploaded into Credo AI."
         },
         {
            "name":"Customer Use Case Demo #2",
            "description":"The second Customer AI use case."
         }
      ]
   }
}
```
<!-- TOC --><a name="-4-usage"></a>
## 🕹️ 4. Usage
***This script only generates a JSON file.*** Bulk upload must be performed *manually* through the UI by a user with the appropriate access level.

<p align="center">
  <img src="img/20250515-bulk-upload-ui.png" alt="bulk_upload_ui" width="616"/>
</p>

<!-- TOC --><a name="-41-requirements"></a>
### 🧰 4.1 Requirements
- Python `>= 3.8`
- Install required packages with: `pip install -r requirements.txt`
- See [`requirements.txt`](./requirements.txt) for specifics.

<!-- TOC --><a name="-42-support"></a>
### 🛠️ 4.2 Support
- ***Coordinate with your Credo AI technical contact*** before running a bulk upload.
- Review the [official Credo AI bulk upload docs](https://knowledge.credo.ai/bulk-use-case-upload).
  - *Pay special attention to the **"Things to note"** section.*
