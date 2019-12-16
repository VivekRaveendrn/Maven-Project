node('') {
    stage('Clone') {
        def url = sh(returnStdout: true, script: 'git config remote.origin.url').trim()
        print url
        print url.tokenize('/') [4].split("\\.") [0]
        reponame=url.tokenize('/') [4].split("\\.") [0]
        branchname="${BRANCH_NAME}"
        print branchname
    }
}
