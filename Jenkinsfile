// The id of the Crowdin project.
crowdinproject = 205391

node('deployment') {
    stage('Preparation') {
        // Download the translation helper project and set it up.
        checkout([$class: 'GitSCM', branches: [[name: '*/master']],  userRemoteConfigs: [[credentialsId: repositorykey, name: 'Translations', url: 'git@bitbucket.org:examsys/examsys-translations.git']]])
        // Install composer.
        sh '''php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"'''
        sh '''php composer-setup.php'''
        sh '''php -r "unlink('composer-setup.php');"'''
        // Remove any old zip files.
        sh '''rm -f *.zip'''
        // Add the config file.
        sh '''rm -f config.php'''
        config = "<?php\n\$projectid=getenv('crowdinproject');\n\$branch=getenv('crowdinbranch');\n\$accesstoken=getenv('crowdinkey');\n"
        writeFile file: 'config.php', text: config
        // Install dependencies.
        sh '''php composer.phar install'''
    }
    stage('Generate translations') {
        withCredentials([string(credentialsId: crowdinkey, variable: 'apikey')]) {
            withEnv(
                [
                    'crowdinproject=' + crowdinproject,
                    'crowdinbranch=' + crowdinbranch,
                    'crowdinkey=' + apikey,
                ]
            ) {
                // All languages.
                sh '''php translations.php'''
                // Each individual lang pack.
                sh '''php translations.php  --lang cs'''
                sh '''php translations.php  --lang pl'''
                sh '''php translations.php  --lang sk'''
            }
        }
        // Save the translations for download.
        archiveArtifacts artifacts: '*.zip', onlyIfSuccessful: true
    }
}
