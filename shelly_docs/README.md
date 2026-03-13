# Shelly Docs, the TUI/CLI Knowledge Mgmt Application for Agents and Humans
Use Markdown documents to manage various types of documentation Items within a codebase and/or filesystem.

Users can specify type of documentation Item in markdown by using Item Tags in Headers.

## Getting Started
### Install
```bash
pip install --user shelly-docs
```

### Setup Knowledge Base
A Knowledge Base is just a directory that will hold the Markdown documents with your Items, and the `shellydocs.yaml` file.

Pick a Directory to hold your Knowledge Base.

Create a `shellydocs.yaml` file, specifying what `item_tags` you want
```yaml
item_tags:
- DESIGN
```

#### Add Items in a Markdown Document
```md
# DESIGN-1 Access Data
Access data from the system.

# DESIGN-2 Update Data
Write data to the system
```


#### Initialize the Knowledge Base
```bash
shelly-docs kb set --path "mgmt_docs" # set the knowledge base path

shelly-docs kb update # reads/refreshes the items in the knowledge base
```
### Work with Items
#### Get the Items
```bash
shelly-docs items list
```
#### Query Items
If an Item has a codefenced block with an info string of `"yaml (data)"`, the data can then be queried with YAML.

```yaml (data)
# place this code block on an Item.
status: todo 
```

```bash
# get the items that have a 'status' of 'done'
shelly-docs items query --query "status: todo"
```
#### Updating Items
Recommended to directly edit the files, and then run `kb update`. Items will then be recaptured based on the content of the markdown files in the Knowledge base.

Optionally, you can run `items put` and provide an item with the path and markdown.


## Concept
Humans will primarily interact with Shelly Docs via TUI (Terminal User Interface) built in Textual

Agents and scripts will primarily interact with Shelly Docs via CLI, retrieving structured data for use in gathering context for accomplishing tasks or for gathering info about the documentation.

Goal is to provide a more effective way to manage project documentation and knowledge as a source for agentic coding workflows, spec-driven development, context engineering techniques.



## Directory Structure
- `/shelly_docs`
  - source code for the application
- `/mgmt_docs`
  - Knowledge Base of Documentation Items for this project
- `/experiment_code`
  - code snippets for small scale experiments
- `/tests`
  - pytest tests and config
