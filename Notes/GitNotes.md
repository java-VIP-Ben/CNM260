# Benjamin Lukens CNM260 Git and Github introduction notes 

Git and Github:
Tools to enable version control and collaboration.
Manages and track changes to files over time. Share, discuss, edit, and review code 
more easily. Know who made what changes, why, and when. Revert changes to previous versions. 
Git is a software like words tracked changes.
Github is a collaboration tool like dropbox or google drive. 

Why are Git and GitHub useful? 
Internal management
- Code is safely stored in one central location
- All staff have access to the same version of code
External collaboration
- Share code developed for your city for use in others 
- Work together on cross-city projects
Reproducability over time
- Efficiently produce results on a schedule 

How do NNIP partners use Git and GitHub? 
CI:NOW (San Antonio) :
- share code and toolkits from data projects
- reprioritize tasks as developer requests and needs of project evolve over time
MAPC (Boston) : 
- support decision making transparency
- Develop web applications
BNIA (Baltimore) 
- Democratize data by sharing resources with other civic technologists 

Key Terms and Concepts:
Git lets you take a snapshot, or commit, of files in a folder (or repository or repo) 
- you decide when to take a snapshot and which files to include. 
GitHub lets you back up your work in a remote place. 
- To get work on your local computer for the first time, you would clone a repo.
- To send updates to github, you would push changes
- To download updates from GitHub, you would pull changes.
All contributors have a local copy of the Git repository. These stay in sync through 
a central remote repository hosted by Github. 
One contributor makes commits and pushes their updates to the central version on GitHub. 
The other contributor pulls from GitHub to stay up-to-date.
Branches let you and your collaborators update existing code or add new code without 
fear of overwriting each others files. All commits live on a branch, the default branch 
is called the main branch. 
Pull requests let you merge changes from one branch into another. GitHub provides a 
helpful interface to review pull requests. 

Basic workflow: 
Initialize a repository (create or clone), edit files, tell git which files to track (add), 
take a snapshot (commit), and send those snapshots to GitHub (push), and repeat. 

Best practices and tips: 
Always follow your organizations policies and avoid pushing potentially confidential 
information to GitHub. In general, you should only track code on GitHub. Consider whether 
a repository should be private or public. 
Use README files to document your repositories. Write descriptive commit messages to help
your collaborators and future self. Work with your collaborators to develop workflows
to meet your needs. 
