Customizing the DSpace 7 Front-End User Interface
=================================================

The DSpace 7 front-end user interface (UI) is a powerful tool that can be customized to fit your organization's needs. 

Installation and Setup
----------------------

Before we begin, make sure you have installed DSpace 7.4 on your Ubuntu 22.04 machine. By default, DSpace is usually installed in the home directory, but in this tutorial, we have installed it in the opt directory.

To follow along with this tutorial, you will need to have Angular installed as the front-end for your DSpace installation. If you're unsure where you have installed DSpace, you can use the locate utility to find the location of the frontend folder.

We have provided a helpful guide in the description of this video that will assist you in customizing the DSpace UI. You can also visit the DSpace documentation website for more extensive guides on designing the front-end using Angular.

Customizing the Background Color
--------------------------------

The first step in customizing the DSpace UI is changing the background color. You can select any color scheme that suits your organization's branding. To do this, open your terminal and navigate to the theme's variable overwrite file, which is usually located in the source folder of your DSpace frontend installation.

    sudo nano /opt/dspace-7/angular/src/app/theme/theme-variables-overwrite.scss

Within this file, locate the line that sets the background color and replace the default color with your chosen color code.

    $background-color: #f0a04b;

Save the file and close the editor. This will change the background color of the DSpace UI to your selected color.

Customizing the Header
----------------------

Next, let's customize the header of the DSpace UI by changing the background color. Open the theme CSS variables overwrite file, which is located in the same directory as the theme variable overwrite file.

    sudo nano /opt/dspace-7/angular/src/app/theme/styles/_variables-overwrite.scss

Add the following line to change the header background color:

    $ds-header-background-color: #e1eedd;

Save the file and close the editor. The header background color will now be updated to your chosen color.

Changing the Logo
-----------------

To replace the DSpace logo with your organization's logo, you will need to have your logo image file ready. Locate the image directory in the assets folder of your DSpace theme installation.

Copy your logo file to the image directory using the `mv` command:

    mv /path/to/your/logo.png /opt/dspace-7/angular/src/assets/images/dspace/logo.png

Replace `/path/to/your/logo.png` with the actual file path of your logo image.

Next, open the `navbar.component.html` file located in the same directory:

    sudo nano /opt/dspace-7/angular/src/app/shared/navbar/navbar.component.html

Find the line that references the DSpace logo image and update it with the path to your logo file:

    <img src="assets/images/dspace/logo.png" alt="DSpace Logo" />

Save the file and close the editor. The DSpace logo will now be replaced with your organization's logo.

Customizing the Footer
----------------------

To customize the footer of the DSpace UI, we will need to copy the custom footer files into the base theme folder. Copy the `footer` folder to the `app` directory of your DSpace theme installation:

    cp -r /path/to/custom/footer /opt/dspace-7/angular/src/app

Replace `/path/to/custom/footer` with the actual path to your custom footer folder.

Next, open the `eager-themes.module.ts` file located in the `app` directory:

    sudo nano /opt/dspace-7/angular/src/app/eager-themes/eager-themes.module.ts

Add the following line to import and declare the footer component:

    import { FooterComponent } from './footer/footer.component';

    entryComponents: [FooterComponent],

Save the file and close the editor. The footer component will now be imported and declared.

Next, open the `eager-themes.module.scss` file located in the same directory:

    sudo nano /opt/dspace-7/angular/src/app/eager-themes/eager-themes.module.scss

Change the font color of the footer in the CSS file to match your desired color:

    .footer { color: #ffffff; }

Save the file and close the editor. The footer font color will now be updated.

Customizing the Favicon
-----------------------

To change the favicon of the DSpace UI, replace the default favicon files with your own. Copy your favicon files to the favicon directory located in the assets/images folder of your DSpace theme installation.

For example, using the `mv` command:

    mv /path/to/your/favicon.ico /opt/dspace-7/angular/src/assets/images/favicon/favicon.ico

    mv /path/to/your/favicon.svg /opt/dspace-7/angular/src/assets/images/favicon/favicon.svg

Replace `/path/to/your/favicon.ico` and `/path/to/your/favicon.svg` with the actual file paths of your favicon files.

Finalizing the Customization
----------------------------

Once you have made all the desired customizations, start all the necessary services for DSpace. This includes starting PostgreSQL, Apache Solr, and the Tomcat server.

Finally, start the Angular development server to see the changes in your DSpace UI:

    cd /opt/dspace-7/angular

    npm start

Wait for the Angular development server to compile and launch the UI. Once it is ready, you can access your customized DSpace UI by opening a web browser and navigating to the local DSpace installation URL.

Congratulations! You have successfully customized the DSpace 7 front-end user interface to match your organization's branding and design preferences.
