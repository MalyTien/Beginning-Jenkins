node {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
        git "https://github.com/MalyTien/Beginning-Jenkins.git"
    }

    dir('Lesson5/ActivityA') {
        stage("Install Requirements") {
            sh 'virtualenv testing'
            sh '. testing/bin/activate'
            sh 'pip install --user -r requirements.txt'
        }

        stage("Run Tests") {
            sh 'testing/bin/nosetests app/ -v'
        }

        stage("Deploy") {
            if (env.BRANCH_NAME == "master") {
                printMessage("deploying master branch")
            } else {
                printMessage("no deployment specified for this branch")
            }
        }
    }

    printMessage("Pipeline End")
}

def printMessage(message) {
    echo "${message}"
}
