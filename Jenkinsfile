node {

    stage('Select') {

      // Get input for OS type

      def OS = input message: 'What OS would you like to test?', \
               parameters: [choice(choices: 'AIX\nRHEL5\nRHEL6\nRHEL7\nWindows', \
               description: '', \
               name: 'OS')]

      // Set the Jenkins credentials that hold our Puppet Enterprise RBAC token

      puppet.credentials 'pe-access-token'

      // start job 

      echo "You have selected: ${OS}"

        if (OS == 'RHEL5') {
            git branch: 'RHEL5', url: 'https://github.com/olmectech/control-repo.git'
        }
        
        if (OS == 'RHEL6') {
            git branch: 'RHEL6', url: 'https://github.com/olmectech/control-repo.git'
        }

        if (OS == 'RHEL7') {
            git branch: 'RHEL7', url: 'https://github.com/olmectech/control-repo.git'
        }

        if (OS == 'Windows') {
            git branch: 'Windows', url: 'https://github.com/olmectech/control-repo.git'
        }

        if (OS == 'AIX') {
            git branch: 'AIX', url: 'https://github.com/olmectech/control-repo.git'
        }

        stage ("$OS") {
           'Deploy to "$OS"'
           puppet.codeDeploy "$OS"
           puppet.job "$OS"
        }
   }
}
