node('') {
    stage('Clone') {
        def url = sh(returnStdout: true, script: 'git config remote.origin.url').trim()
        print url
        branchname="${BRANCH_NAME}"
        print branchname
        if (branchname.contains("Db"))
        {
            stage('Trigger')
            {
                build job: 'SampleProject/Test'
            }
        }
    }
}
