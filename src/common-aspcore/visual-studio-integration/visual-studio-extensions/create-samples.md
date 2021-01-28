# Create Sample

The Syncfusion Sample Creator is a utility that allows you to create the Syncfusion ASP.NET Core (Essential JS 2) Projects with sample code of required Syncfusion component features and configuration of Syncfusion controls.

## IMPORTANT

The Syncfusion ASP.NET Core (Essential JS 2) Sample Creator utility is available from v16.3.0.17.

The following steps is used to create the Syncfusion ASP.NET Core (Essential JS 2) Application via the Sample Creator utility:

1. To launch ASP.NET Core (Essential JS 2) Sample Creator application, follow either one of the options below:

    **Option 1:**

    Click **Syncfusion Menu** and choose **Essential Studio for ASP.NET Core (EJ2) > Launch Sample Creator…** in **Visual Studio.**

    ![sample creator](../images/sample-creator.png)

    **Option 2:**

    Launch the Syncfusion ASP.NET Core (Essential JS 2) Control Panel. Select the Sample Creator button to launch the ASP.NET Core (Essential JS 2) Sample Creator application. Refer to the following screenshot for more information.

    ![control-panel](../images/sample-creator-control-panel.png)

2. ASP.NET Core (Essential JS 2) Sample Creator list the Syncfusion controls and its features.

![controls-list](../images/controls-list.png)

**Controls Selection:** Choose the required controls. The controls are grouped with Syncfusion products.

![control selection](../images/controls-selection.png)

**Feature Selection:** Based on the controls, the feature is enabled to choose the features of the corresponding controls.

![feature selection](../images/feature-selection.png)

## Project Configuration

1. You can configure the project with following details.

    **VS Version**: Choose the Visual Studio version and Framework.
    **Project Type**: Select the type of ASP.NET Core Project.
    **ASP.NET Core Version**: Select the version of ASP.NET Core Project.

    ![aspnet core version](../images/Aspnet-core-version.png)

    > The ASP.NET Core version 2.2 and 3.0 option will be listed only when the corresponding Dotnet Core version setup has been installed in VS2019.

    **Assets From**: Choose the Syncfusion Essential JS 2 assets to ASP.NET Core Project, either NuGet, CDN, or Installed Location.

    > Installed location option will be available only when the Syncfusion Essential JavaScript 2 setup has been installed.

    **Name**: Name your Syncfusion ASP.NET Core (Essential JS 2) Application.

    **Location**: Choose the target location of your project.

    **Theme Selection**: Choose the required theme. This section shows the controls preview before creating the Syncfusion project.

    ![theme selection](../images/theme-selection.png)

2. Click **Create** button. After creating the project, open the project by clicking **Yes**. If you click **No**, the corresponding location of the project will be opened. Refer to the following screenshot for more information.

    ![create](../images/create-button.png)

3. The new Syncfusion ASP.NET Core (Essential JS 2) project is created with the resources.

    * Added the required Controllers and View files in the project.

    ![controllers](../images/required-controllers.png)

    * Included the required Syncfusion ASP.NET Core (Essential JS 2) scripts and theme files.

    ![scripts and css](../images/scripts-css.png)

    * Restored the required Syncfusion NuGet packages for selected controls under dependencies.

    ![nuget packages](../images/nuget-packges.png)