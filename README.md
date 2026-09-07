# ExamSys translation download

This is a project that will download translations from ExamSys and make them available on Jenkins.

## Jenkins plugins

This script requires the follow plugins to be installed on Jenkins:

* SSH Agent Plugin

## Runner requirements

* php
* php-curl
* [crowdin](https://crowdin.github.io/crowdin-cli/)

## Environment variables

The following environment variables are used to configure the scripts.

| Variable          | Required     | Explantion                                                                      |
|-------------------|--------------|---------------------------------------------------------------------------------|
| repository        | **required** | The location of the translation tool repository                                 |
| repositorybranch  | **required** | The name of the branch in the repository that should be used                    |
| repositorykey     | **required** | The Jenkins id for the security key used to access the repository.              |
| crowdinbranch     | **required** | The Crowdin translation branch to download (master, develop)                    |
| crowdinkey        | **required** | The Crowdin access token                                                        |
| crowdinproject    | **required** | The id of the crowdin project we will use                                       |

## Related projects

* [examsys-translations](https://github.com/examsys/examsys-translations)
