# NuGet Packages

[NuGet](https://www.nuget.org/) can be used to automatically add files and references to your Visual Studio projects. You can use the Syncfusion ASP.NET Core NuGet packages without installing the Essential Studio or ASP.NET Core platform installation to implement the Syncfusion ASP.NET Core controls.

From v16.2.0.46 (2018 Volume 2 Service Pack 1) onwards, all the Syncfusion components are available as NuGet packages at [nuget.org](https://www.nuget.org/).

Starting with v16.2.0.x, if you reference Syncfusion assemblies from trial setup or from the NuGet package, you must include a license key in your projects. Refer to this [link](https://help.syncfusion.com/common/essential-studio/licensing/license-key) to learn about registering Syncfusion license key in your ASP.NET Core application to use Syncfusion controls.

> Starting from v17.1.0.32 (2018 Volume 1), Syncfusion will no longer publish NuGet packages at [nuget.syncfusion.com](https://nuget.syncfusion.com/).

## Installing NuGet Packages

### Using NuGet Package Manager

The NuGet Package Manager can be used to search and install NuGet packages in the Visual Studio solution or project.

1. Right-click the project/solution in the Solution Explorer tab, and choose **Manage NuGet Packages…**

    ![manage nuget packages](images/manage-nuget.png)

    Alternatively, click **Tools**, menu, **NuGet Package Manager | Manage NuGet Packages for Solution...**

2. Select the NuGet.org from the **Package source** drop-down.

    ![package source](images/package-source.png)

3. All the Syncfusion NuGet Packages are listed and available. Search and install the required packages in your application by clicking the **Install** button.

> The Syncfusion NuGet packages are published in public [NuGet.org](https://www.nuget.org/) from v16.2.0.46 . To install earlier version of 16.2.0.46 Syncfusion NuGet packages, [configure Syncfusion private feed URL.](https://help.syncfusion.com/extension/syncfusion-nuget-packages/nuget-packages#syncfusion-nuget-feed-url-configuration)

## Using Package Manager Console

To reference the Syncfusion ASP.NET Core UI Control using the Package Manager Console as NuGet packages, follow the below steps:

1. On the **Tools** menu, select **NuGet Package Manager** and then **Package Manager Console**.

2. Run the following NuGet installation commands.

    ```cmd
    #install specified package in default project
    Install-Package <Package Name>

    #install specified package in specified project
    Install-Package <Package Name> - ProjectName <Project Name>
    ```

    **For Example**

    ```cmd
    # install specified package in default project
    Install-Package Syncfusion.EJ2.AspNet.Core

    #install specified package in specified project
    Install-Package Syncfusion.EJ2.AspNet.Core -ProjectName SyncfusionDemoApplication
    ```

## Using Visual Studio for macOS

1. Add packages can be used to search and install NuGet packages to the Visual Studio project in macOS.

2. Right-click the folder in the project, and then select **Add Packages…**

    ![add packages](images/add-packages.png)

3. The Syncfusion ASP.NET Core NuGet Packages available in the package source location will be listed. Search and install the required packages in your application, by clicking **Add Package** button.

## Managing NuGet package using NuGet CLI

The NuGet Command Line Interface (CLI), `nuget.exe`, provides the full extent of NuGet functionality to install, create, publish, and manage packages without making any change to the project files.

1. Download the latest NuGet CLI [here](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe).

    > To update the existing nuget.exe to latest version, use the following command.

    ```cmd
    nuget update -self

    ```

2. Open the downloaded executable location in the command window and run the following commands to download and install the required NuGet packages to a project specified in the package.config.

    ```cmd
    #install specified package in default project from specified package source for Windows Platform
    nuget.exe install <Package name | ConfigFilePath > <Options>

    #install specified package in default project from specified package source for MAC/Linux Platform
    mono nuget.exe install <Package name | ConfigFilePath > <Options>
    ```

    > configPath is optional. This identifies the package.config or solutions file that lists the packages utilized in the project.

    **For Example**

    ```cmd
    #install specific package for Windows
    nuget.exe install “Syncfusion.EJ2.AspNet.Core”

    #install all package which mention in package.config path for Windows
    nuget.exe install “C:\Users\SyncfusionApplication\package.config”

    #install specific Syncfusion NuGet package for Windows
    nuget.exe install “Syncfusion.EJ2.AspNet.Core”

    #install all package which mention in package.config path for Mac and Linux
    mono nuget.exe install “C:\Users\SyncfusionApplication\package.config”
    ```

## Upgrading NuGet packages

### Using NuGet Package Manager

1. NuGet packages can be updated to their specific version or latest version available in the Visual Studio solution or project:

2. Right-click the project/solution in the Solution Explorer tab, and choose **Manage NuGet Packages…** Alternatively, click **Tools** menu, **NuGet Package Manager | Manage NuGet Packages for Solution…**

3. Select the **Updates** tab to see the packages available for update. Select the required packages and the specific version from the dropdown and click the **Update** button.

### Using Visual Studio for macOS

1. Using **Update** context menu from Visual Studio for Mac application, NuGet packages can be updated.

2. Right-click the Packages folder in the project and select **Update**.

3. This will update the NuGet package to the latest version. You can double-click the Add packages and choose the specific version.

> To update all the projects from solution, use an update option in the solution level.

### Using Package Manger Console

To update the installed Syncfusion ASP.NET Core NuGet packages using the Package Manager Console, follow the below steps:

1. On the **Tools** menu, select **NuGet Package Manager**, and then **Package Manager Console**.

2. Run the following NuGet installation commands.

    ```cmd

    #Update specific NuGet package in default project
    Update-Package <Package Name>

    #Update all the packages in default project
    Update-Package

    #Update specified package in specified project
    Update-Package <Package Name> - ProjectName <Project Name>
    ```

    **For Example**

    ```cmd
    #Update specified Syncfusion ASP.NET Core NuGet package
    Update-Package Syncfusion.EJ2.AspNet.Core

    #Update specified package in specified project
    Update-Package Syncfusion.EJ2.AspNet.Core -ProjectName SyncfusionDemoApplication
    ```

### Using NuGet CLI

Using the NuGet CLI, all the NuGet packages in the project can be updated to the available latest version.

1. Download the latest NuGet CLI from [here](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe).

    > To update the existing nuget.exe to latest version, use the following command.

    ```cmd
    nuget update -self
    ```

2. Open the downloaded executable location in the command window. Run the following `update commands` to update the Syncfusion ASP.NET Core NuGet packages.

    ```cmd
    #update all NuGet packages from config file
    nuget update <configPath> [options]

    #update all NuGet packages
    nuget update
    ```

    > configPath is optional. This identifies the package.config or solutions file lists the packages utilized in the project.

    **For Example**:

    ```cmd
    #Update all NuGet packages from config file
    nuget update “C:\Users\SyncfusionApplication\package.config”
    ```

> Update command is not working as expected in Mono (Mac and Linux) and projects using PackageReference format.

## Syncfusion NuGet feed URL Configuration

### Get the Syncfusion NuGet feed URL

To get the URL from Syncfusion website, use the following steps:

1. Navigate to [nuget.syncfusion.com](https://nuget.syncfusion.com/), and select **WEB** tab.

2. Navigate to **WEB(Essential JS 2)**, click the **Copy URL** label under **ASP.NET Core** platform to copy the Syncfusion ASP.NET Core platform NuGet feed to clipboard or directly use the following URL: <http://nuget.syncfusion.com/nuget_aspnetcore-js2/nuget/getsyncfusionpackages/aspnetcore-js2>

    ![nuget](images/nuget-url.png)

3. Now, use this NuGet feed URL to access the Syncfusion NuGet Packages in Visual Studio.

## Add the Syncfusion NuGet feed URL

### Windows

1. Open your Visual Studio application.
2. On the **Tools** menu, select **Options**.
3. Expand the **NuGet Package Manager** and select **Package Sources**.
4. Click the **Add** button (green plus) and enter the ‘Package Name’ and ‘Package Source URL’ of the Syncfusion ASP.NET Core NuGet packages.

    **Name**: Name of the package listed in the available package sources.

    **Source**: Syncfusion ASP.NET Core NuGet Feed URL <http://nuget.syncfusion.com/nuget_aspnetcore-js2/nuget/getsyncfusionpackages/aspnetcore-js2>

5. Click the **Update** button to add the name and source details to package sources.

![update button](images/update-button.png)

## MacOs

1. Open your Visual Studio application.
2. Right-click the Packages folder in the project, and then select **Add Packages…**

    ![add packages](images/macos-addpackages.png)

3. Choose the **Configure Sources…** from the dropdown that appears in the left corner of the Add Packages dialog.

    ![configure sources](images/configure-sources.png)

4. At the bottom right corner of the dialog, click the **Add** button to enter the feed name and the URL.

    **Name**: Enter the name (For e.g., Syncfusion ASP.NET Core Packages).

    **Location**: Enter the following URL – <http://nuget.syncfusion.com/nuget_aspnetcore-js2/nuget/getsyncfusionpackages/aspnetcore-js2>.

5. Now, click **Add Source** and then click **OK**.

## Nuget CLI

1. Download the latest Nuget CLI [here](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe).

    > To update the existing nuget.exe to latest version use the following command:

    ```cmd
    nuget update -self
    ```

2. Open the downloaded executable location in the command window, and run the following commands to configure the Syncfusion NuGet packages:

    ```cmd
    #Add specified package source in NuGet.config file for Windows platform
    nuget.exe Sources Add –Name <Source name> –Source <Source location>

    #Add specified Package Source in Nuget.config file for MAC/Linux platform
    mono nuget.exe Sources Add –Name <Source name> –Source <Source location>
    ```

    **For Example**

    ```cmd
    #For Windows platform
    nuget.exe Sources Add –Name “Syncfusion Source” –Source “http://nuget.syncfusion.com/nuget_aspnetcore-js2/nuget/getsyncfusionpackages/aspnetcore-js2”

    #For MAC/Linux platform mono
    nuget.exe Sources Add –Name “Syncfusion Source” –Source “http://nuget.syncfusion.com/nuget_aspnetcore-js2/nuget/getsyncfusionpackages/aspnetcore-js2”
    ```
