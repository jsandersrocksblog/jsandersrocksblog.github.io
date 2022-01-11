A quick blog for search and replace text in a group of files using Linux Ubuntu.  I needed to migrate Wordpress to a github pages blog that was using Jekyll and ran into trouble replacing text in the markdown.

# Overview
I first downloaded a zip file of my Wordpress blog in the Jekyll format.  The plugin had issues but the command line version worked great!
This is the plugin:  https://wordpress.org/plugins/jekyll-exporter/  .  I used ssh to get to the directory the plugin was installed and issued this command: wp jekyll-export > export.zip
I am developing using WSL and VS Code remote on my Windows 11 machine so simply did a drag and drop of the files into VS Code in the appropriate directories.  One thing I notices is that the images links were still the old site.  I needed a way to search and replace the old site info and move to relative paths for many of the MD files.

# Solution
I navigated to the _posts directory and executed this sed command: sed -i -r 's|http://jsandersblog.azurewebsites.net/wp-content/uploads|/assets/images|g' *.md

## Breakdown
- sed -i -r  (-i = inplace modify the file  -r = extended regex)

- 's\| (set separator for regex to '\|' - necessary to choose something other than / since the URL contains these)

 - http://jsandersblog.azurewebsites.net/wp-content/uploads\| (what to search for and separator)

- /assets/images\| (what to replace the former string with and separator)

- g (replace globally-all occurences)

- *.md (the files to search filtered to and markdown file which is .md for my posts)

# Another useful script
To remove the Metadata inserted by Wordpress I used this command which removes the separators '---' and all the data between:

sed  -i "/---/,/---/d" *.md

To remove all leading whitespace in a file:

sed -i '/\S/,$!d' *.md
