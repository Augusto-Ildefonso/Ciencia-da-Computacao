# What is Vite?
Vite is a JavaScript build tool that helps developers build web applications quickly.
# How to use it?
First of all, we need to install vite as a dependency to our project. For this, we use the following command.
```
$ npm install --save-dev vite
```
To check if *Vite* was installed, check the `package.json` file and see if you see the following line.
~~~json
{
	"devDependencies": {
		"vite": "version"
	}
}
~~~
Now that we already installed vite, we can create a HTML file and begging to run our develoment server. In order to do it, we need to access the `package.json` file and add the following lines to create a script that runs our server.
~~~json
{
	"scripts": {
		"dev": "vite dev"
	}
}
~~~
Now you need to run the following command to start the server:
```
$ npm run dev
```
# Creating a project from a Template with Vite
To start with, we need to run the following command so we can began to create our project.
```
$ npm create vite
```
After running the command above, it's going to ask you to put the project name. If you put a *.* as the name, it is going to create the project in the directory you already are, but if you put any other name it's going to create a new directory. Then it is going to ask you a package name and to choose a framework, now if you won't use any framework choose vanilla, if not, choose the one that you will use. After that keep answering the questions so it can create your project.

After the project was created, you need to install vite in order for it to work. For that you can run this command:
```
$ npm install
```
Another way to create a project with a template is to run the following command:
```
$ npm create vite project-name --template template-name
```
Depending on the version of npm you are using, you will need to put an extra *--* before the *--template*.
# Deploying with Vite
To build the application, you can use the command:
```
$ npm run build
```
And to check the built application you can use:
```
$ npm run preview
```
Now let's explore some modifications we can make to our `package.json` file. First of all, we can determine the port that the *preview* command will use to emulate the server. For this, we add the following to the `package.json` file:
~~~json
{
	"scripts": {
		"preview": "vite preview --port PORT"
	}
}
~~~