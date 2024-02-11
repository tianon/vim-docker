node {
	dir('vim-docker') {
		stage('Checkout') {
			checkout([
				$class: 'GitSCM',
				userRemoteConfigs: [
					[
						name: 'origin',
						refspec: '+refs/heads/master:refs/remotes/origin/master',
						url: 'https://github.com/tianon/vim-docker.git',
					],
					[
						name: 'docker',
						refspec: '+refs/heads/master:refs/remotes/docker/master',
						url: 'https://github.com/docker/docker.git',
					],
					[
						name: 'vim',
						refspec: '+refs/heads/master:refs/remotes/vim/master',
						url: 'https://github.com/vim/vim.git',
					],
				],
				branches: [[name: 'origin/master']],
			])
		}

		// "Captain: You know what you doing."
		env.FILTER_BRANCH_SQUELCH_WARNING = '1'

		stage('Filter Docker') {
			sh '''
				git checkout refs/remotes/docker/master
				git filter-branch --force \
					--subdirectory-filter contrib/syntax/vim
			'''
		}
		stage('Push Docker') {
			sh '''
				git push --force git@github.com:tianon/vim-docker.git HEAD:refs/heads/docker
			'''
		}

		stage('Filter Vim') {
			sh '''
				git checkout refs/remotes/vim/master
				git filter-branch --force \
					--subdirectory-filter runtime
				git filter-branch --force \
					--prune-empty \
					--index-filter '
						git rm --cached -r --quiet --ignore-unmatch . &&
						git reset -q $GIT_COMMIT -- \
							ftplugin/dockerfile.vim \
							syntax/dockerfile.vim
					'
			'''
		}
		stage('Push Vim') {
			sh '''
				git push --force git@github.com:tianon/vim-docker.git HEAD:refs/heads/vim
			'''
		}
	}
}
