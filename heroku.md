Creating an Node.js + Express App With Heroku
====

[Heroku](https://www.heroku.com/)  

# References

The following instructions are based on Heroku's [Getting started with nodejs](https://devcenter.heroku.com/articles/getting-started-with-nodejs) tutorial.

Additional material on Node.js and Express may be found at:

- Node: [nodejs.org](http://nodejs.org/)
- Express: [expressjs.com](http://expressjs.com/)

# Basic Express Application with Heroku

Ensure you are familiar with the command line and git before refering to this material.

Create a new directory for the project where all the express application code will reside and `cd` into it so that it is now the working directory:

	$ mkdir node-app
	$ cd node-app

Generate an express application with the `express` command, which generates a template for the new application:

	$ express

Applications often have *dependency requirements*. A dependency is additional, 3rd party code which an application uses. Rather than writing new code, a programmer uses code which someone else has already written.

A new express application is dependent upon additional code. Install the code into the application with `npm install`:

	$ npm install
	
A new express application is ready to be run out of the box. The application uses node.js to start a web server on your computer, which you can then access in a web browser.

Start the application:

	$ npm start

View it in a web browser at:

	http://localhost:3000/

Web applications that are runningly *locally*, that is, on your machine, are accessed with a special URL: **http://localhost**.

Additionally, express runs the application on a different *port*, specifically port 3000. The web browser must know to connect to the web server on port 3000, which is why **:3000** appears at the end of the URL.

A node express web application will continue to run until it crashes or is terminated from the command line. Terminate the application by typing Control-C (^C) into the terminal window (hold down the *control* key and press the *C* key.):

	$ ^C

The application is now working locally, but we also want to upload it to Heroku's servers. Before doing that, Heroku requires additional information about the application. Specifically, Heroku uses a *Procfile* that tells it how to start the application.

Use the `touch` command and `echo` with *redirection* to create the file and add a line of text to it.

	$ touch Procfile
	$ echo "web: node ./bin/www" >> Profile

By itself, `node ./bin/www` is the command that starts the web application and is the same command that is used by `npm start`.

View the application using `foreman`, a utility used by Heroku to start a  web application. Foreman can also be used to start an application locally.

	$ foreman start
	
Foreman uses a slightly different URL to view the application:

	http://localhost:5000/

Node that foreman runs the web server on port 5000.

**On Windows**, foreman may not work. If foreman does not work, continue starting the app with `npm start`, and continue using the original URL with port 3000 in your web browser.

<!--
The command may not work becuase Heroku does not set up the foreman program correctly. If foreman doesn't work on Windows, modify the *PATH variable* to let Git Bash know where foreman is.

Follow the instructions here to modify your *System Path* variable: [how-to-set-the-windows-path-in-windows-7](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx)

You need to add the following text to your path variable: `;C:\Program Files (x86)\Heroku\ruby-1.9.2\bin`, including that semicolon at the beginning.

Restart Git Bash for the changes to your path to take effect. The terminal should now be able to find foreman:

	$ which foreman
	/c/Program Files (x86)/Heroku/ruby-1.9.2/bin/foreman

It's possible that foreman will still not work. Execute `foreman` in the console. If there is an error about a *bad interpreter*, install an older version of foreman. The error looks like:

	$ foreman start
	sh.exe": /c/Program Files (x86)/Heroku/ruby-1.9.2/bin/foreman: "c:/Program: bad interpreter: No such file or directory
	
Install an older version of foreman with:

	$ gem uninstall foreman
	$ gem install foreman -v 0.61

Type `Y` and press enter when asked if you want to remove the executable.

If you cannot get foreman working on Windows, continue to start the web application with `npm start`.
-->

Use Control-C (^C) again to stop foreman or node:

	$ ^C

Heroku uses git to upload applications to its servers. Create an empty git repository for the web application:

	$ git init
	Initialized empty Git repository in /Users/okcoders/Documents/OK-Coders/1-bash-heroku/heroku-test/.git/
	
Add and commit the project's files to the git repository:

	$ git add .
	$ git commit -m "Initial Commit"
	
You are now ready to use git to upload, or *push*, your application to Heroku's servers. Use Heroku's command line utility to first create a new Heroku application:

	$ mbp-phil:heroku-test node-app$ heroku create
	Creating desolate-brook-2377... done, stack is cedar
	http://desolate-brook-2377.herokuapp.com/ | git@heroku.com:desolate-brook-2377.git
	Git remote heroku added

Notice that Heroku automatically added a remote repository named *heroku* to the git project when you created the new Heroku app.

Push the project to Heroku's server using `git push` and the *heroku* name provided. Push the *master* branch:

	$ git push heroku master
	
Confirm that the application is running on Heroku with the `heroku ps` command:

	$ heroku ps
	=== web (1X): `node ./bin/www`
	web.1: up 2014/06/02 13:41:03 (~ 1m ago)

*Web.1* corresponds to the web command that was set up in the Procfile, and Heroku confirms that it is up and running. 

View the application on the public internet:

	$ heroku open
	
You just created a web application and put it on the internet!

Any additional changes you make to the application should be tracked and committed to the git repository. You can then push them to Heroku again. So when you're ready to save and upload your changes, type:
	
	$ git add .
	$ git commit -m "Your new commit message - change this"
	$ git push heroku master
