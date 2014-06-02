Creating an Express App With Heroku
====

https://devcenter.heroku.com/articles/getting-started-with-nodejs


Heroku will automatically add remote repositories to git when you create a new heroku app for your project.

Create a directory for you 

	$ mkdir node-app
	$ cd node-app
	
...

Generate an express application

	$ express
	
...

Install application dependencies

	$ npm install
	
...

Start the application

	$ npm start

View it in a web browser at.

	http://localhost:3000/

Kill the node app with Control-C (^C)

Set up what Heroku calls the Procfile, which tells it how to start the application. Use the `touch` command and `echo` with *redirection* to create the file and add a line of text to it.

	$ touch Procfile
	$ echo "web: node ./bin/www" >> Profile
	
View the application using `foreman`, a utility used by Heroku to start a  web application. Foreman can also be used to start an application locally.

	$ foreman start
	
Foreman uses a slightly different URL to view the application:

	http://localhost:5000/
	
**On Windows: ** Foreman may not work. If foreman does not work, continue starting the app with `npm start`, and continue using the original URL in your web browser.

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

Use Control-C (^C) again to stop foreman or node.

Heroku uses git to upload applications to its servers. Create an empty git repository:

	mbp-phil:heroku-test node-app$ git init
	Initialized empty Git repository in /Users/okcoders/Documents/OK-Coders/1-bash-heroku/heroku-test/.git/
	
Add and commit the project's files to the git repository:

	git add .
	git commit -m "Initial Commit"
	
Create a heroku application:

	mbp-phil:heroku-test node-app$ heroku create
	Creating desolate-brook-2377... done, stack is cedar
	http://desolate-brook-2377.herokuapp.com/ | git@heroku.com:desolate-brook-2377.git
	Git remote heroku added
	
Upload, or *push*, the project to Heroku:

	$ git push heroku master
	
Confirm that the application is running on Heroku with the `heroku ps` command:

	mbp-phil:heroku-test okcoders$ heroku ps
	=== web (1X): `node ./bin/www`
	web.1: up 2014/06/02 13:41:03 (~ 1m ago)
	
And view the application on Heroku:

	$ heroku open
	
