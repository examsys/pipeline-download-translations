# ExamSys translation download

This is a project that will download translations from ExamSys and make them available on Jenkins.

## Jenkins plugins

This script requires the follow plugins to be installed on Jenkins:

* SSH Agent Plugin

## Environment variables

The following environment variables are used to configure the scripts.

| Variable          | Required     | Explantion                                                                      |
|-------------------|--------------|---------------------------------------------------------------------------------|
| repositorykey     | **required** | The Jenkins id for the security key used to access the repository.              |
| crowdinbranch     | **required** | The Crowdin translation branch to download (master, develop)                    |
| crowdinkey        | **required** | The Crowdin access token                                                        |

## Related projects

* [examsys-translations](https://bitbucket.org/examsys/examsys-translations/)
