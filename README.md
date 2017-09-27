java-war-deploy-example
=======================
An example Java application that deploys an already-existing WAR file.

Background
----------
This is an extension of the [Java Tomcat example](https://github.com/daticahealth/java-tomcat-maven-example) with a few minor tweaks to show how to work with WAR and JAR files that require customized build processes which do not fit nicely into the [buildpack model](https://resources.datica.com/compliant-cloud/articles/buildpacks/).

The `simple-jar` and `simple-war` directories under `source-projects` are included here to show the (simplistic) source of the artifacts used by default in this demo. You can safely ignore them; the deployment method used here does _not_ require you to keep the source code of your application in a Git repository.

If you haven't already read Datica's [Java + Maven Guide](https://resources.datica.com/compliant-cloud/articles/guides/java-maven-tomcat/) please check it out. Also, the [Heroku Java documentation](https://devcenter.heroku.com/categories/java) and [Heroku Java Buildpack project](https://github.com/heroku/heroku-buildpack-java) and are also good references which are mostly relevant when running Java applications on Datica.

Getting Started
---------------
1. Clone this repository.
2. Customize the `.datica/post-build` script to pull down your pre-built software artifacts. We recommend using S3 in conjunction with access keys credentials if you need to protect those artifacts from public access.
3. Update the `Procfile` command as appropriate. By default it uses the [webapp runner](https://github.com/jsimone/webapp-runner) to start up a Tomcat instance for serving up a WAR file.
4. Commit your customizations to your local Git repository.
5. Use the [datica git-remote add](https://resources.datica.com/compliant-cloud/cli-reference/#git-remote) command to associate your customized repo to a service in your Datica environment.
6. Push your modified branch to your service using the `git` command (usually `git push datica master`).
7. Grab some coffee while your build finishes and your new application is deployed for you automatically.

As always, feel free to reach out to [Datica's support team](https://datica.com/support/) if you run into any trouble.
