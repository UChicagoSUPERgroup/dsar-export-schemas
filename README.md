# Data Subject Access Request (DSAR) Export Schemas Repository

This repository contains information about the structure and layout of data
exports from several online platforms. Each export is in a directory under
`schemas/` named after that platform (e.g., `Airbnb` and `Too_Good_To_Go`).

We will use AllTrails's directory to illustrate how to navigate an export schema
in this repository. By navigating to
[`AllTrails/`](https://anonymous.4open.science/r/dsar-export-schemas/schemas/AllTrails/),
you are viewing a simplified and generalized version of what a participant would
see in their data export. With the exceptions described below, the names of the
files and directories are as they appear in a real data export. Rather than
trying to emulate the "average" export in the repository, we instead chose to
prioritize breadth: even if a file was only present for one participant in our
study, as long as we were able to schema-generalize the file, we decided to
include it in the repository.

## Files Without Content

In `AllTrails/` there are seven directories and one file (`remote.html`). That
file has no content, but we still included it in this repository since it
existed in one of the exports we received for AllTrails. It has no content
because we were not able to schema-generalize HTML files due to their more
complex structure, compared to spreadsheet and JSON files (which we did
schema-generalize). We made the decision to include it, though, since it
contains valuable contextual information: that AllTrails has an HTML file that
may provide consumers with an interface for interacting with their data.

## Interpreting Schema-Generalized Files and Records

We took steps to remove participant-specific information from file names and
record names. This was not only to protect participant privacy, but to avoid
communicating redundant information. Consider the lone `<custom_name>.jpg` file
in `AllTrails/User Online Activity/photos/`. Here, `<custom_name>` not only
communicates that the file name does not follow a clear or useful naming
structure that we could identify, but it also means that there can be multiple
of this specific file type in this directory. In fact, **any time a schema
generalization artifact is in a file or record name, it may occur more than once
in that location**.

Below is a comprehensive list of schema generalization artifacts. Unless
otherwise noted, it can apply to directories, files, and records:

- `#`: a digit.
- `YYYY` or `YY`: a four or two digit year.
- `MMM` or `MM`: a month expressed with digits or with by abbreviated name.
- `DD`: a day in a month.
- `HH`, `mm`, `SS`: hour, minute, and second, respectively.
- `<username>`: a username or handle in a platform.
- `<email>`: an email address.
- `<phone number>`: a phone number.
- `<unique_id>`: what is seemingly a randomly generated unique id, such as a
  UUID.
- `<number>`: a specific case with JSON keys and spreadsheet column names (i.e.,
  records) that are numbers.
- `<custom_name>`: the most general of the schema generalization artifacts, this
  is used when there is a consumer or export specific string that did not have a
  discernible pattern.

## Schema Files

Some files in the repository have this additional suffix attached to their name:
`.schema.json`. This can be the case for files of any extension, but for the
platforms in this repository, they appear after JSON, CSV, and XLSX files. When
this is the case, the content of the file contains the structure of the file
represented as a schema following the
[JSON Schema IETF draft standard](https://json-schema.org/draft/2020-12/json-schema-core).
The content of JSON files are described by the schema in the typical way, i.e.,
`properties` list JSON keys and their value types. For CSV files, the schema
`properties` correspond to CSV column names. For XLSX files, top-level
`properties` correspond to sheet names within the file and second-level
`properties` correspond to column names within that sheet.
