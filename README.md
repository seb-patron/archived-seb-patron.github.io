# Welcome to my blog!

Hey there! Welcome to my blog's source code. In here, you'll find all the code, assets, and settings that make my blog what it is.

#### A few things to note

First, the folder _site is where all the rendered files that make my website. These are the final html, css, and javascript files that make my website when you visit [sebastianpatron.com][sebastianpatron.com].

_posts, _projects, _pages, and _news are folders filled with markup files that make up the individual pages of my website. These files get rerendered by Jekyll into the html files found in the _site folder. I write my posts in markdown first, then let jekyll handle everything else.

_includes and _layouts are the templates that make up my pages. The markdown files use these templates and fill out the "missing" sections of them like {{content}}.

The rest of the folders help support my website and take care of some more details. _sass contains my sass files, assets contains images, _data contains some additional data that fills out certain pages, etc.

This blog is based on **al-folio**, which is based on the [\*folio theme](https://github.com/bogoli/-folio) (published by [Lia Bogoev](http://liabogoev.com) and under the MIT license).
Over time, I gave the theme a couple of re-writes and added many additional cool features. For example, on the [photography page](http://sebastianpatron.com/skills/3_photography/) I created a custom javascript script and css that allows a user to click on an image to make it larger and give it a white background (you can see that code [here](https://github.com/seb-patron/seb-patron.github.io/blob/master/_skills/3_photography.markdown)).

Another example is making the theme more mobile friendly by resizing the skills and projects thumbnails depending on the user's view size ([code over here](https://github.com/seb-patron/seb-patron.github.io/blob/master/_sass/_projects.scss)).



## Contributing

Feel free to contribute new features and theme improvements by sending a pull request.
Style improvements and bug fixes are especially welcome.

## License

MIT

[sebastianpatron.com]: http://sebastianpatron.com
[photography-page]: http://sebastianpatron.com/skills/3_photography/
