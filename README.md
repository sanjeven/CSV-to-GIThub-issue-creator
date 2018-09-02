# CSV To Git Hub Issue Creator
A simple package to help convert CSV file entries to GITHub issues via API v3 (Private and Public repositories).
This package helps developers to maintain private repositories who want to keep their code hidden but issues section open to the public.

A platform to collect results can be set up for example via google forms to collect responses and convert these responses to issues which include Assignee, Labels, Title, Description and Date raised.

## How to use:

```
from csvtogitissue import csvtogitissue
```

```
FILE_ID = 'file ID from google drive'
FILE_NAME = 'Name after downloaded'
file1 = csvtogitissue.download_responses_gform(FILE_ID,FILE_NAME)
> Returns 1 for success 0 for fail

FILE_LINK = 'File link from the web'
FILE_NAME = 'Name after downloaded'
file2 = csvtogitissue.download_responses_CSV(FILE_LINK,FILE_NAME)
> Returns 1 for success 0 for fail


FILE_NAME = 'Name after downloaded'
TOKEN = 'GIT hub API token'
REPO_NAME = 'name of repo on git hub (private or public)'
REPO_OWNER = 'Repo owner used as as assignee'
(Column numbers)
TITLE = 'Column number of title'
DESCRIPTION = 'Column number of title'
LABELS = 'Column number of label'
CREATED_DT = 'Column number of label'
EMAIL = 'Column number of email if column does not exist set it to str(NULL)'
file3 = csvtogitissue.create_issues(FILE_NAME,TOKEN,REPO_NAME,REPO_OWNER,TITLE,DESCRIPTION,LABELS,EMAIL,CREATED_DT)
> Returns 1 for success 0 for fail
```

## Alternatively you may want to use a config.ini file:

```
config.ini

[DEFAULT]
TOKEN = xxxxxxxxxxxxxxxxxxxx
REPO_OWNER = Your name here
REPO_NAME = Repo name here
FILE_ID = File ID here
FILE_NAME = File name here
CREATED_DT = 0
DESCRIPTION = 3
TITLE = 2
LABELS = 1
EMAIL = 4

In your python code

TOKEN = config['DEFAULT']['TOKEN']
REPO_OWNER = config['DEFAULT']['REPO_OWNER']
REPO_NAME = config['DEFAULT']['REPO_NAME']
FILE_ID = config['DEFAULT']['FILE_ID']
FILE_NAME = config['DEFAULT']['FILE_NAME']
DESCRIPTION = config['DEFAULT']['DESCRIPTION']
TITLE = config['DEFAULT']['TITLE']
LABELS = config['DEFAULT']['LABELS']
EMAIL = config['DEFAULT']['EMAIL']
CREATED_DT = config['DEFAULT']['CREATED_DT']
```

## Reminder:
- Remember to make sure that the labels defined in the CSV are available in the repository to be tagged.
- Bugs can be reported at https://goo.gl/forms/Vxusa4xJQH4WEqHG3 or at https://github.com/sanjeven/CSV-to-GIThub-issue-creator