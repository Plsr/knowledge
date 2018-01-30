# Heroku
This living document provides a list of useful snippets reagarding working with [Heroku](heroku.com) as well as so guidance for problems I faced myself and and want to be able to solve faster the next time I encounter them.

## Content
* [Basic Resources](#basic-resources)
* [Situations](#situations)

## Basic Resources
* **[Heroku DevCenter](https://devcenter.heroku.com/categories/reference)** The Heroku DevCenter provides guidance to basically everything that can be done with Heroku.
* **[Heroku CLI Commands](https://devcenter.heroku.com/articles/heroku-cli-commands)** or `heroku help`

## Situations
### Deploying a rails app with pending migrations
Remember that heroku does not run database migration for raisl applications automatically whil deploying (at least, not by default). You might encounter errors in the deployed version that are due to missing database migrations.  
To run migrations from the CLI: `heroku run rails db:migrate --app your-heroku-application-name`<sup>[1](#footnote1)</sup>  
Afterwards, you app still might be not functioning correct, because it is in a transient state, database-wise. Usually, a restart of the app should fix this. To restart the app, go to the web interface or run `heroku ps:restart --app your-heroku-application-name`.

### Deploying to heroku with an existing app and soruce code cloned from github
It really is as simple as adding heroku to the repositories remotes: `heroku git:remote --app your-heroku-application-name`. You can verify this by running `git remote -v`:
```
heroku	https://git.heroku.com/your-heroku-application-name.git (fetch)
heroku	https://git.heroku.com/your-heroku-application-name.git (push)
origin	git@github.com:user/repository.git (fetch)
origin	git@github.com:user/repository.git (push)
```

#### Resources
* [This](https://stackoverflow.com/questions/5129598/how-to-link-a-folder-with-an-existing-heroku-app) Stack Overlow Question

---------
<a name="footnote1">1</a>: Make sure you use the Heroku name of your application, not the one that you ight have used on your local filesystem. If you are not sure what the app name is, check the Heroku Web-Interface or run `heroku apps`
