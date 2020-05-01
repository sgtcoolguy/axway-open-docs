{"title":"Creating a Custom Preview Server","weight":"40"} 

You can customize the URLs used during previewing to accommodate the case where the web root of your site does not match your project structure, or you can't use the internal server.

*   [Using a Local Web Server](#UsingaLocalWebServer)
    
*   [Using a Remote Web Server](#UsingaRemoteWebServer)
    

## Using a Local Web Server

As an example, we consider a set of web sites like the following, where we wish to preview files in .../project1/public:

![folder](/Images/appc/download/attachments/30083125/folder.png) Documents  
![folder](/Images/appc/download/attachments/30083125/folder.png) workspace  
![folder](/Images/appc/download/attachments/30083125/folder.png) project1  
![folder](/Images/appc/download/attachments/30083125/folder.png) private  
![folder](/Images/appc/download/attachments/30083125/folder.png) public  
![page](/Images/appc/download/attachments/30083125/page.png) index.html  
![folder](/Images/appc/download/attachments/30083125/folder.png) project2  
![folder](/Images/appc/download/attachments/30083125/folder.png) ...

*   **Base URL:** http://localhost:2020/
    
*   **Document Root:** /Documents/workspace/project1/public/
    
*   **Studio Project Root (optional):** /Documents/workspace/project1/
    

The goal is that http://locahost:2020/index.html serves the file located at /Documents/workspace/project1/public/index.html.

The files in question do not have to be part of a Studio project, but we illustrate the case above for additional clarity.

1.  Right-click on a project in the "Project Explorer" view, and select **Properties**.
    
2.  Select "Preview Settings". Click **Use Specific Server** and **New**.
    
3.  Select **Simple Web server**.
    
4.  Fill out the form shown below:  
    ![Screen_shot_2011-04-22_at_2.29.43_PM](/Images/appc/download/attachments/30083125/Screen_shot_2011-04-22_at_2.29.43_PM.png)
    
    *   **Name:** Choose a descriptive name that describes the server uniquely
        
    *   **Base URL:** The URL of the server up to the document root (e.g. http://localhost:2020/ from above)
        
    *   **Document Root:** The path to the public root of the web site (e.g. /Documents/workspace/project1/public/ from above)
        
    
5.  Click **OK** and **OK**.
    

The above configuration does not copy files between the Studio project and the web root - it is a direct link with both items mapping to the same place. Thus, when you save index.html inside Studio, you are editing the same file served by the web server listed above. If you instead need to preview against a remote web server, you can use a similar setting as above, but you will want to set up a deployment option to "upload on save". See below.

Pressing the preview button will now preview a file against the selected server.

## Using a Remote Web Server

The process for previewing against a remote web server is much the same--the only difference is setting up the files to be transferred on save if you wish to make the process as transparent as possible. Again, we start with the following setup:

*   **Base URL:** http://www.mywebsite.com/[](http://www.mywebsite.com/)
    
*   **Document Root:** /Documents/workspace/project1/public/
    

The goal is that http://www.mywebsite.com/index.html serves the file located at /Documents/workspace/project1/public/index.html.

1.  Right-click on a project in the "Project Explorer" view, and select **Properties**.
    
2.  Select "Preview Settings". Click **Use Specific Server** and **New**.
    
3.  Select **Simple Web server**.
    
4.  Fill out the form shown below:  
    ![Screen_shot_2011-04-22_at_2.29.43_PM](/Images/appc/download/attachments/30083125/Screen_shot_2011-04-22_at_2.29.43_PM.png)
    
    *   **Name:** Choose a descriptive name that describes the server uniquely
        
    *   **Base URL:** The URL of the server up to the document root (e.g. http://www.mywebsite.com/ from above)
        
    *   **Document Root:** The path to the public root of the web site (e.g. /Documents/workspace/project1/public/ from above). This is actually ignored in this case, but we must fill in a value, so we use the local path.
        
    
5.  Click **OK** and **OK**.
    

Now, set up the deployment options:

1.  Follow the deployment instructions here: [FTP SFTP and FTPS Deployment](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/Publishing/FTP_SFTP_and_FTPS_Deployment/).
    
2.  When setting up the site, you may wish to choose "Automatically sync my changes...".
    
3.  Save and close the dialog.
    

Pressing the preview button will now preview a file against the remote server. Now, when you save and upload a file (or upload automatically on save if you have chosen that option), you can refresh the preview and see your changes.