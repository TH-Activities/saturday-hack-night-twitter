# Saturday Hack Night Template

TinkerHub saturday hack night submission repository template. 

### Getting started
This project is only intended to be used by the TinkerHub HQ Staff who organises the hackday.
- Click on [Use this template](https://github.com/tinkerhub/saturday-hack-night-template/generate) button and generate your own version of the project. 
- Update the readme about the project submission process. You can use any data collection tools like airtable to collect the repo URLs from the participants. Use the **Add Project** github action to add a project to the hackday repo.
- Start the hackdday.

### How to use
This repository contains the following GitHub Action workflows:
- Add Project - This will allow organizer to add a new project to the GitHub repository as a submodule so that the project can be evaluated. This contains the following params:
    - Repository URL: URL of the project's repo (HTTPS)
    - Folder Name: You can specify a folder name to keep the submodule (eg: project name)

- You can also trigger the above workflow using the following CURL, replace username and repo with your own username and repo name, also replace the request body with the actual repo and folder name to add:
```bash
export TOKEN="" # get it from https://github.com/settings/tokens
curl --location --request POST 'https://api.github.com/repos/{username}/{repo}/actions/workflows/add-project.yml/dispatches' \
--header 'Authorization: Bearer $TOKEN' \
--header 'Accept: application/vnd.github.v3+json' \
--header 'Content-Type: application/json' \
--data-raw '{
    "ref": "main",
    "inputs": {
        "repo_url": "https://github.com/gautamkrishnar/homebrew-socli.git",
        "folder_name": "homebrew"
    }
}'
```
- Update Projects - This workflow will run every hour updating the submodules to its latest state. It can be also triggered manually from actions tab.
