# Deploy / Host your React App with cPanel
## react, javascript, cpanel
#


1. Purchase a Domain and Hosting
To host a website, you'll need to purchase a registered domain name and a hosting plan from a hosting provider (both provided through numerous sources like Namecheap or Godaddy). If you buy them together, these providers will typically point the domain to your hosting server automatically. If not, this tutorial can help you out.

2. Next, open up your React App. Open up your package.json file and add a "homepage" attribute like so:
```
 "homepage": "http://yourdomainname.whatever"
 ```

3. Create the build File
In your application's root directory, run yarn install to install the updated dependencies. Once this has finished, the next command you'll run is 
``` 
$ npm run build
 ```

You'll notice this creates a new directory in your project called build. The build folder is essentially a super-compressed version of your program that has everything your browser needs to identify and run your app.

build directory

4. Connect to cPanel
Let's head over to your hosting provider (Namecheap, Godaddy, Bluehost etc.). Once you've logged in, navigate to the cPanel manager for your domain. Typically there is a dropdown menu of some kind that says "Manage" which will direct you to cPanel.
Navigate into the File Manager. There you'll find a dropdown list of directories. The one we're interested in is public_html. Open that up.


5. Add the Build File Contents to public_html
Navigate to the build file in your app's root directory. Open it up and select all the contents inside the build file. If you upload the entire build file itself, the process will not work.


Once you've copied all the contents inside the build file, upload them into public_html.

6. Create and Upload the .htaccess File
In order for the routes to work in your React app, you need to add a .htaccess file. In the public_html folder, at the same level as the build file contents, add a new file and name it .htaccess.

Edit the file and insert the following boilerplate information:

```
<IfModule mod_rewrite.c>

  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-l
  RewriteRule . /index.html [L]

</IfModule>
```

Save the file.

You're Super Done.
That's it! Navigate to your domain address in the browser and you should see your fully functioning web app.
