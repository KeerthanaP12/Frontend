A web application for Purdue Students that seamlessly combines exercise and nutrition tracking while offering intelligent, personalized suggestions to guide users' health and fitness journeys 🍎🏋️.

Specialized dining court integration features are included for students @ Purdue.

Workspace Setup
To clone the repository onto your local machine, run git clone https://github.com/youngbryanyu/titan-health-app.git in the directory you want the repository to be cloned into.

We used yarn as the package manager for our application. Install yarn by running npm install yarn. We will be managing the versions of node modules separately for front and backend. Next, navigate to both the /backend and /frontend directories run yarn in both to install all the necessary node module dependencies. If you accidentally ran yarn in the root directory instead of in the /backend and /frontend directories, delete the /node_modules directory and yarn.lock files and make sure to run yarn in the proper directories.

Running the Application
Set up the environment Variables
The environment variables for the backend server will need to be configured before running the application. See the Environment Variables for the Backend Server section for steps on setting up the .env file for environment variables.

Running the Backend (Server)
Navigate to the /backend directory. Before starting the server, run yarn to update existing node modules or install any missing node module dependencies. Then run yarn start to start the backend server.

Running the Frontend (Client)
Navigate to the /frontend directory. Before starting the server, run yarn to update existing node modules or install any missing node module dependencies. Then run yarn start to start the backend server. The default IP address and port number set by the application is http://localhost:3000/.

Development
For more details on how to use yarn as a package manager, see the yarn CLI documentation.

Installing New Modules (Dependencies)
To install a new dependency required, navigate to either the frontend or backend directory, then run yarn add <module_name> to install the new module in its desired location. Use the --dev flag to add a dev dependency instead of a dependency. Make sure to not install dependencies in the project root directory, but rather in either the /frontend or /backend directories. If you accidentally ran installed a dependency in the root directory instead of in the /backend and /frontend directories, delete the /node_modules directory and yarn.lock files and make sure to run yarn add ... in the proper directory.

Pushing New Changes
Before pushing any changes and making a pull request, run the following:

git config --global push.default current: This will allow you to automatically push changes on your local branch to a remote branch of the same name using git push or git push -u. See this stack overflow post for more details if interested. Just make sure that if you are using this feature instead of specifying the remote branch, that there isn't already a remote branch with the same name or else there could be unintended conflicts.
git config --global pull.rebase true: This will set git to default rebase when pulling.
Next, just run the following:

git pull to pull in any changes before committing. If the pull pull and rebase fails due to conflicting local changes run git stash, then git pull, then git stash pop. Fix any conflicts and commit when finished.
git commit -m <message> to commit your changes.
git push to push the changes to the remote branch that will be created by default based on the config set above.
Navigate to Pull requests to create the pull request onto the main branch. Get the necessary approvals then merge and delete the branch.
Make sure not to push anything from node_modules when committing and pushing changes. We don't want tons of dependencies stored in our repository.

Pull Request Rules
The follow requirements must be met before pushing changes onto the main branch:

Must be an invited contributor to the repository
Must have 1 approval from another contributor
Must have 1 approval from the repository owner (youngbryanyu)
Personal Access Tokens
You may need to set up a personal access token for authentication due to GitHub's newer security guidelines. See this documentation for how to do so (create a classic token), or follow the steps below:

Go to the Tokens (classic) in Developer settings.
Click on Generate new token, then Generate new token (classic).
Give the token a name, set the desired expiration, and check every check box for maximum permission access, then at the bottom click Generate token.
Save the access token somewhere safe and local since you will need it to authenticate.
Next time if you are prompted for your username and password when pushing, use your access token as the password. If you don't want to retype your credentials every time, run git config credential.helper store before you run git push, and once you enter your credentials, they will be stored locally (unencrypted) so you don't have to re-enter them repeatedly.

MongoDB Setup (For Database Access)
We have set up a MongoDB cluster though MongoDB Atlas, hosted on AWS. Follow the below steps to make sure you are setup for development. The necessary credentials are contained in the credentials document which is private (must request access).

Setting Up Network Access for your IP Address
Navigate to cloud.mongodb.com and log into the Titan Health App account using the credentials in the credentials document. Select the Titan Health App organization and project.
Under the SECURITY section on the left, go to Quickstart, and scroll down to Add entries to your IP Access List. Simply click Add My Current IP Address, and your device's IP will be granted access to the Database cluster (you may need to repeat this step if you're IP address is dynamically assigned and changes, or you're on a different network). You can also add your IP in to the access list in the Network Access section but it's easier to do it through Quickstart.
Note: currently we have enabled allowing all IP addresses to access the database cluster.

Database Access (Users and Roles)
There already exists two users that each assume 1 default role. They're set up to be authenticated simply through credentials which are contained in the credentials document.

ReadWriteUser - has read and write access to the database cluster. (Stick with this user for development)
AdminUser - has full administrator access to the database cluster.
Connecting to the Database
The URI and credentials to connect to the database cluster are contained in the credentials document. For ease of visualizing the data while working with it, we recommend downloading MongoDB Compass and connecting through Compass to visualize the databases and collections during development.

The collections of data relevant to the application will all be stored under the TitanHealthApp database within the database cluster.

Environment Variables for the Backend Server
Like mentioned earlier in the section about how to run the application locally, the environment variables will need to be set up in the .env file. The file .env.example under /backend is provided as a template for the .env environment variables file. .env will need to be populated with necessary keys and credentials, and is kept empty on the repository because it contains confidential keys and credentials. See this document for the .env file we are using to run and test our application locally (file is private and must request access).

Do not push changes in .env to any remote branch. If you add a new environment variable simply add it to the .env.example template file with a temporary value. To prevent accidental pushes of the .env file, I recommend running git update-index --assume-unchanged **/backend/.env, which tells git to ignore changes in . More about this is in this stackoverflow post.
