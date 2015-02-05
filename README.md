# Innomatic Platform application skeleton

This is a project structure tree that you can use as the skeleton for your new Innomatic Platform application.

This skeleton provides a basic project structure and a build system based on Apache Ant (tm).

The source folder is the base directory for your Innomatic application.

## How to use this skeleton

To initialize your application development tree using this skeleton, you should:

- download a copy of this project (e.g. using the GitHub “Download ZIP” button and not a git clone in order to use your own git repository);
- remove (or customize) this README.md file;
- edit the source/setup/application.xml file (especially the idname field and the release and components sections);
- customize the CHANGES and LICENSE files in source/setup folder;
- customize the name and version properties in build.xml file;
- start application development inside the source folder.

## Building your application

To build your application you can use ant with the provided build.xml file.

The build file defines three targets:

- package (default target): builds a distributable application archive inside the build folder.
- source: builds a source archive inside the build folder.
- deploy-to-vagrant: builds the application archive and deploy it to a local Innomatic Platform Vagrant installation (see next chapter).

## Deploying to a Vagrant machine

A custom Vagrant file for Innomatic Platform projects is available at https://github.com/innomatic/innomatic-vagrant (already included in Innomatic Platform when cloning the public GitHub project).

The “deploy-to-vagrant” ant target provides a fast method to deploy the current application in development to a local Vagrant machine configured with the above mentioned Vagrant file.

You must have a ssh host named “innomatic-vagrant” inside your SSH configuration file (e.g. ~/.ssh/config), e.g.:

<pre><code>
Host innomatic-vagrant
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/currentuser/.vagrant.d/insecure_private_key
  IdentitiesOnly yes
  LogLevel FATAL
</code></pre>

You can get the exact configuration for your setup by running “vagrant ssh-config” from the console while in the Vagrantfile directory and renaming “default” host to “innomatic-vagrant”.

Since Innomatic Platform is a container (like an application server) you should do not include the platform source inside your project code, so it is likely you have a single Innomatic Platform Vagrant installation named “innomatic-vagrant” for all your Innomatic projects.

You can change the ssh host name for your Innomatic Platform Vagrant machine (e.g. if you need multiple Innomatic installations in different Vagrant machines). In this case you must update the “vagrant-hostname” property in the build.xml file.

