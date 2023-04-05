# Usealan API Docs

API Docs uses **Ruby >= 2.6**, this project uses a framework called Slate which is a Ruby tool that generates clean and responsive API documentation.

[Slate Official Repo](https://github.com/slatedocs/slate)

## Installing and Configuring API Docs

The official documentation indicates how to setup and start a Slate project, check it here.

[Requirements and Installation](https://github.com/slatedocs/slate/wiki/Using-Slate-Natively)

Once the project setup is completed, you are ready to run Slate. You can run it in two ways, either as a server process for development, or just build html files.

To do the first option, run:

```sh
bundle exec middleman server
```

and you should see your docs at http://localhost:4567. Wow! That was fast!

The second option (building html files), run:

```sh
bundle exec middleman build
```

## Deployment

Built HTML files are hosted in **GitHub Pages** at this URL.

https://docs.usealan.com

To deploy changes to this site, update the main branch with as many changes as you require and once you are done, run the following script at the project root.

```sh
./deploy.sh
```

This script will take your changes, build the HTML files and will push it to a branch called **gh-pages** which the hosting service is listening to, then just commit the changes to this branch and your new updates will be reflected almost immediately.

Voilà!
