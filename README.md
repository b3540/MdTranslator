# MdTranslator

Translate markdown document on your repository.

[![Build Status](https://simplearchitect.visualstudio.com/MdTranslator/_apis/build/status/MdTranslator.CI)](https://simplearchitect.visualstudio.com/MdTranslator/_build/latest?definitionId=5)

# Motivation

When I run the international event in Japan, we made a lot of effort to translate the contents into Japanese. 
I'd like to automate this effort by the power of the Durable Functions. 

# Outcome 

* Create a new branch 
* Translate all `.md` document into the target language

# Configration

Create `local.settings.json` with adding GitHubAccessToken and Cognitive Service Translator key here. For the FunctionApp, You need to add `GitHubToken` and `TranslatorKey` on your AppSettings on your FunctionApp.

This app use "CommitName" and "CommitEmail" when it updates the md files. It records as commit logs.

```
{
    "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "dotnet",
    "GitHubToken": "YOUR_GITHUB_PERSONAL_ACCESS_TOKEN_HERE",
    "TranslatorKey": "YOUR_COGNITIVE_SERVICE_TRANSLATOR_KEY_HERE"
    "CommitName": "UPDATE_GITHUB_ACCOUNT_NAME",
    "CommitEmail": "UPDATE_GITHUB_ACCOUNT_EMAIL"
  }
}
```

# Usage

You can send an request with `POST` to `http://localhost:7071/api/MdTranslator_Start` or your address. Message body is

```
{"owner": "TsuyoshiUshio",
 "repo": "TranslationTarget",
 "sourceBranch": "master",
 "language": "ja"
}
```


