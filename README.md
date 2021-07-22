# Training Workshop Kit

> [Docker ](Dockerfile) : Open platform for developers and sysadmins to build, ship, and run distributed applications as containers, whether on laptops, data center VMs, or the cloud.

> [CircleCI ](https://circleci.foc.zone/gh/Servicing/dolphin-api) : Continuous Integration (CI) and Continuous Deployments (CD) tool

> [AWS Elastic Container Service (ECS) ](https://aws.amazon.com/ecs/) : Orchestration of Docker containers on EC2 instances. This runs the code, auto-scales containers and the EC2's they run on up and down, as well as handling the infrastructure side of deploying new code.

> [HAL9000 ](https://hal.zone/applications/933/dashboard) : QL in-house application that handles deployments and releases to various environments (including AWS). It also handles a lot of the encrypted configuration values which are passed to the code as Environment Variables.

> [Terraform ](https://www.terraform.io/) : Terraform is Infrastructure-As-Code (IAC) that can build out highly QL-specific infrastructure components in a repeatable way. Instead of a lot of click-and-configure, we can run terraform scripts to create approved infrastructure stacks on-demand in minutes.

# Prerequisites

**These are the prereqs which are needed prior to coming to a workshop. The following should be completed and ready to go:**

- Docker installed locally ( **Install through Software Center (PC) or Self Service (Mac)** - If you install from the Docker web site, you will be missing key network policies needed )
    * If using a Windows PC, make sure right-click the Docker icon in your system tray and make sure it's set to use LINUX containers. In other words, it should set "Switch to Windows containers", which means it's currently on Linux containers.
    * Once the above steps are complete (regardless of operating system), open a command prompt/terminal window, enter the following command, and wait for it to complete: "docker pull microsoft/dotnet:2.1-sdk". **Verify this steps works prior to the class**
- VSCode or similar file editor ( https://code.visualstudio.com/download )
- AWSCLI installed ( https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html )
    * Go to a command prompt, type in **aws configure**. Hit enter for the first 2 lines, enter "us-east-2" for the region, then enter again. This will create an **.aws** folder under your user folder with configuration files for the cli.
    * Due to our network firewall, you need to add the QL certs into the certificate chain so the awscli can properly communicate with AWS. Go here: https://git.rockfin.com/raw/sudoers/ssm-instance-connect/master/files/qlcerts.pem, download that file to your **~/.aws/** folder. Add the following "ca_bundle" line to your ~/.aws/config file:
        ```
        [default]
        region = us-east-2
        ca_bundle = ~/.aws/qlcerts.pem
        ```

- Request AWS account access to Training Lab Account (418023852230). Navigate to myaccess/ in your browser, click "Add/Remove Access", and search for `AWS-SSO-TrainingIAC-NonProd-ServerEngineer`. Click the checkbox and request it for your **dash account**. Then click "Review and Submit", then "Submit".
- Terraform ( https://www.terraform.io/ )
    * If using a Windows PC, wherever you download Terraform to, make sure to add that path to your PATH variable. See here for how: https://helpdeskgeek.com/windows-10/add-windows-path-environment-variable/
    * If Mac, see here: https://osxdaily.com/2014/08/14/add-new-path-to-path-command-line/
    * Effectively, you want to be in any folder on your computer and be able to call that binary. To test, go to the command line of your OS and type "terraform version": you should get the version back. If not, see someone from IT Team Sudo.
- Create demo repository under your personal QL GIT org ( https://git.rockfin.com/YOURNAME/999999-YOURNAME-iac )
- If you've never used HAL before, go to https://hal.zone/ in your browser and login with your dash account. This will create your account in HAL.
- Clone example GIT project locally ( see below )

## Setting up GIT

1. Clone this repo locally to your laptop ( https://git.rockfin.com/training-iac/training-starter-kit.git )

2. Rename the folder to this naming standard: **999999-YOURNAME-iac**, where YOURNAME is your AD network login (first initial, last name). Then, delete the **.git** folder at the root; this allows you to associate this folder with a different git repo. This will become the base for the Git repo for your application's infrastructure.

3. Make a repo with the same name as what you called the folder in step 2 under your personal Git organization. https://git.rockfin.com/YOUR-NAME/999999-YOURNAME-iac. For example, https://git.rockfin.com/jsmith/999999-jsmith-iac

4. Follow the instructions given to you post-creation in your browser to upload your modified clone of the starter-kit to your applications new IAC repo. The one difference is instead of "git add README.md", type "git add -A" instead to add everything.

You are all set if you have a custom-named version of the starter kit uploaded and ready to go in your personal (QL-owned) GIT org.
