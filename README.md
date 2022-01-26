# Codeship running Jenkinsfiles

[![Git](https://app.soluble.cloud/api/v1/public/badges/df1d4e31-4b50-492e-90c4-81f5b931cd2d.svg?orgId=451115019187)](https://app.soluble.cloud/repos/details/github.com/michaelneale/codeship-jenkinsfile-spring?orgId=451115019187)  

<img src='https://wiki.jenkins.io/download/attachments/2916393/logo.png'>

Building on the good work by Kohsuke for one shot execution of Jenkinsfiles, this shows how build a spring boot app with a Jenkinsfile on Codeship. For a more minimal example see: https://github.com/michaelneale/codeship-jenkinsfile

[ ![Codeship Status for michaelneale/codeship-jenkinsfile-spring](https://app.codeship.com/projects/27e405e0-04e0-0136-23bf-26f9c8a90726/status?branch=master)](https://app.codeship.com/projects/280598)

# How to use

Clone this, do what you want. Customise the Dockerfile.build for build time dependencies and/or customise the base Jenkinsfile runner image as per instructions on https://github.com/kohsuke/jenkinsfile-runner/. Make sure to copy both codeship yml files, the Jenkinsfile and the Dockerfile.build into your project.

# How it works

Codeship pro is native docker, so this works by launching the one shot Jenkins, after all the repository is copied into the container. The image used I pre-built with the current Jenkins LTS image and all the "recommended" plugins. If you need more plugins, at this point in time that means customising your own runner image. 

The Jenkinsfile runs the build in the container defined by the Dockerfile.build (so there are some limitations for running on many nodes as one might do in a more complex Jenkinsfile). Obviously all the webhooks, pull requests, triggers and branches are handled by codeship. Jenkins is simply the execution engine.

The Dockerfile.build installs maven and defines the build environment for the app. 

The codeship-steps.yml defines the script that launches the Jenkinsfile runner. 


<img src='https://raw.githubusercontent.com/github/explore/6c6508f34230f0ac0d49e847a326429eefbfc030/topics/spring-boot/spring-boot.png'/>
