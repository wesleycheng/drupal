转载自https://gist.github.com/Greg-Boggs/8a2661b70c4e293db585

Better Drupal Building
* Custom glue should be accomplished with configuration first and PHP code second.

Configuration Management and Dependencies
* Use Composer (or Drush Make) to build your project and it's depencies.
  ```
  composer create-project drupal-composer/drupal-project:8.x-dev my_site_name_dir --stability dev --no-interaction --no-install
  composer update
  ```
* Store your work in files.
* Set your config directory above the webroot.
* Sync UUIDs across all developers.

Theming
* Frontend automation should use Gulp to automate tasks like livereload and sass.
* Yeoman should be used to generate project themes.
* SCSS syntax SASS should be used to generate CSS.
* Themes should apply to Drupal without using #id,content-type, block-id, or view-id in the source.
* Each theme should have reusable patterns rather than top down pages.
* Themes should use Blockify rather than hard coding blocks into templates.
* Single field, node, block, view PHP Templates should be avoided.

Editor Experience
* Content should be editable by the site editor without modifying code, css or complex configuration. 
* Content should have an edit in place contextual gear.
* Content should not be defined in code.
* It should not require admin access to figure out how to edit content.
* The editor user should have links or a dashboard that links to “hidden” editor pages.
* Editors should be given the Clear Cache permission.
* CKeditor should be the JavaScript editor. 
* Editors should be able to apply custom CSS via a drop down menu.
* Taxonomy can be used to apply additional page styles

Content
* Content should be a node.
* Taxonomy should categorize nodes. It should not store content.
* A site should have as few content types as reasonable (4 - 6 is a good goal).
* Content types should be singular
* Taxonomy vocabulary should be plural
* Field names should be singular or plural based on the number of values in the field.
* Fields should be reused when possible.

Blocks
* Context should be used to place blocks.
* Blocks should only be used sparingly. Consider creating a block view of a node marked by taxonomy instead.

Lists
* Lists should render the teaser view mode of content
* Custom displays should be accomplished by adding additional view modes.
* Content should be listed with views.
* Views should use the rendered entity format unless it’s impossible to do so.
* List should be ordered with draggable views.

Search
* Search boxes should not be labeled and they should contain HTML5 placeholder text.
* Search API should power site search. Core search should not be used.
* Search API should be powered by Solr or Elastic Search backend.
* Facets should be avoided in favor of views filters.
* All fields should be indexed including category names.
* Search should allow stemming, spelling correction and related searches.
* Current Search should not be used.

Breadcrumbs
* Breadcrumbs that don't match URL structure should be avoided.
* Easy Breadcrumbs module should be used to map URLs to breadcrumbs.

Permissions and Roles
* Editors should have permissions limited to the set of tasks they perform 80% of the time.
* Testing should be done as the editor user.

Caching
* Varnish should be used.
* Block Caching must be enabled.
* If users log in, then modules that disable block caching should not be used.
* Page cache should be on.
* Views Content Cache should be added and used on all views except random views.
* Random Views should be avoided. If used, they should be set to 30 minute time cache.
* Views Cache should be set to not expire.
* System cron should be run weekly to avoid resetting HTML page cache.

JavaScript
* JavaScript should be non-blocking and loaded in the footer.
* JQuery can be loaded from Google.
* Javascript should not write inline CSS.
* Yeoman and Gulp should be used to construct the primary frontend toolsets

CSS
* CSS should be loaded in the header in external files.
* CSS should be preprocessed from SCSS.
* A Classless asymmetric grid system should be used to create responsive columns.

Images
* Transparent pngs should be avoided.
* Images should always be compressed as well as possible.
* Larger images should be resized to fit the size of the device.

Fonts
* FOUT should be dealt with using the responsive typography method championed by Jason Pamental.
* Google webfont loader should not be used.
* Custom fonts should be used in limited amounts.
* Custom fonts should be less than 50kb each.

Responsive Features
* Responsive customizations should be accomplished in JavaScript and be fully cachable by Varnish.

Code
* Code should never go into the database inside eval functions.
* Code should be separated into discrete modules based on function, not content type.
* There should be more than one feature.
* All source code should follow Drupal coding standards.
* TODOs should be marked with TODO.

Source Control
* Remote hosted git should be used to manage all source code.
* Gitflow should be used to manage git branches.
* Production sites should run off of a different branch than development.

Cookies
* LocalStorage should be used instead of cookies.

Deploying
* Development servers should deploy automatically on a push to the master branch.
* Production servers should be deployed from the production branch using git pull or a deployment tool.
* Database changes should be deployed with Features.

Performance
* Sites should load in under 1 second from the nearest data center on Pingdom performance test.
* Pages should not exceed 1 MB.
* Pages should not exceed 100 requests.

Web Hosting
* Web hosting should make use of a globally distributed CDN.
* PHP 5.5 should be used.
* OPcache should be enabled for PHP with at least 64 MB of memory.
* A cache should be used such as APCu for single web servers or memcache for multiple.
* All websites should be behind a Varnish server.
* Solr should be hosted on a dedicated Tomcat server
* The latest stable MariaDB should be used as a database server. 
* If apache is used, it should use mod-php and have AllowOverrides off.
* Drupal should only have permission to write to /tmp/* and sites/default/files/*
* Servers will be monitored for uptime and load.
* All servers will have image backups daily and weekly.
