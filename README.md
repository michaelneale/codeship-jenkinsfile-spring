# Codeship running Jenkinsfiles

<img src='https://www.cloudbees.com/sites/default/files/codeship-by-cloudbees.png'>
<img src='https://wiki.jenkins.io/download/attachments/2916393/logo.png'>

Building on the good work by Kohsuke for one shot execution of Jenkinsfiles, this shows how build a spring boot app with a Jenkinsfile on Codeship. For a more minimal example see: https://github.com/michaelneale/codeship-jenkinsfile


# How to use

Clone this, do what you want. Customise the Dockerfile.build for build time dependencies and/or customise the base Jenkinsfile runner image as per instructions on https://github.com/kohsuke/jenkinsfile-runner/. 

# How it works

Codeship pro is native docker, so this works by launching the one shot Jenkins, after all the repository is copied into the container. The image used I pre-built with the current Jenkins LTS image and all the "recommended" plugins. If you need more plugins, at this point in time that means customising your own runner image. 

The Jenkinsfile runs the build in the container defined by the Dockerfile.build (so there are some limitations for running on many nodes as one might do in a more complex Jenkinsfile). Obviously all the webhooks, pull requests, triggers and branches are handled by codeship. Jenkins is simply the execution engine.

The Dockerfile.build installs maven and defines the build environment for the app. 

The codeship-steps.yml defines the script that launches the Jenkinsfile runner. 


<img src='https://raw.githubusercontent.com/github/explore/6c6508f34230f0ac0d49e847a326429eefbfc030/topics/spring-boot/spring-boot.png'/>
