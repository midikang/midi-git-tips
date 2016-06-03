
gem install jekyll

jekyll new personal-website

jekyll serve -P $PORT -H $IP  

It's important to understand Jekyll's default directory structure and contents of your site:

- _config.yml - This is a configuration file that contains many values that need to be edited only once. These values are used across your site, for example, your site's title, your e-mail, and more. Note that this is a .yml file, which you can learn more about here.
- _includes/ - This directory contains all the partials (code templates that keep you from repeating your code over and over) that your site uses to load common components, like the header and the footer.
- _posts/ - This directory is where blog posts are stored. New blog posts can be added and will be rendered with the site's styling, as long as the file name follows Jekyll's standard naming convention.
- _layouts/ - This directory contains templates that are used to style certain types of posts within the site. For example, new blog posts will use the HTML layout defined in post.html.

git remote add origin https://github.com/midikang/midikang.github.io.git

