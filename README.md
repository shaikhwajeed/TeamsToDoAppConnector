
# Microsoft Teams Get Started Sample in .NET/C#

This app simulates connection to a project management system and allows users and teams to create, manage and search tasks. The content is randomly generated to simulate what you can do with Teams.

This .NET/C# sample only shows the Bot and Compose Extension portion of the sample.  As the Tab and Connector work is web code unrelated to the bot service, we provide a hosted version of that code for this sample, built from the project's Node.js codebase.  For more information on the Tab and Connector support in this sample, please review the [Node repository](../Node/readme.md)

**For more information on developing apps for Microsoft Teams, please review the Microsoft Teams [developer documentation](https://msdn.microsoft.com/en-us/microsoft-teams/index).**

## Prerequisites
The minimum prerequisites to run this sample are:
* The latest update of Visual Studio. You can download the community version [here](http://www.visualstudio.com) for free.
* An Office 365 account with access to Microsoft Teams, with [sideloading enabled](https://msdn.microsoft.com/en-us/microsoft-teams/setup).

>**Note**: some features in the sample require that you [enable Public Developer Preview mode](https://msdn.microsoft.com/en-us/microsoft-teams/publicpreview) in Microsoft Teams.

For more information about how to configure and test our samples, see [Sample applications for the Microsoft Teams Developer Platform](https://msdn.microsoft.com/en-us/microsoft-teams/samples).

## Code Highlights

### Connectors
The sample shows a simple implementation of a Connector registration implementation, and a sample of sending a Connector Card to the registered Connector via a process triggered "externally."

To simply illustrate the Connector functionality, you can utilize the built-in Incoming Webhook connector:
1) Select a channel in Teams you'd like to receive the messages
2) On the channel options, select Connectors, and add the Incoming Webhook Connector
3) Name it anything you wish, and get the resulting URI, the channel webhook URI used in the testing flow per below.
>Note that this process does not leverage the setup or registration flow in the ConnectorController.cs code.

Alternately, you can go through the full process to register a new Connector, which will trigger the setup and registration flows in the ConnectorController.cs file:
1) You'll need to register a new connector in the Connector Developer Portal, Follow the steps here: [Registering your connector](https://msdn.microsoft.com/en-us/microsoft-teams/connectors#registering-your-connector)
2) Ensure you have both Teams and Groups checkboxes selected.
3) For the Landing page for groups during registration, you'll use our sample code's setup endpoint: `https://[BASE_URI]/connector/setup`
4) For the Redirect URL during registration, you'll use our sample code's registration endpoint:  `https://[BASE_URI]/connector/register`
* In both steps 3 & 4, `[BASE_URI]` is the full URI for your running sample which will be the same Ngrok endpoint used for the rest of your sample, if running locally.
5) In the Web.config file, update: `configuration.appSettings.ConnectorAppId` to use your new Connector ID, which you can retrieve via the Connector Developer Portal's Copy Code or Download Manifest buttons. Also, set the `configuration.appSettings.Base_Uri` variable to ngrok https endpoint url.


To test the Connector Card functionality:
1) For a registered Connector:  the registration results page gives you a link for Task Manager portal.
2) Click on Create and enter the task details and Save.
3) You will see the MessageCard in the registered Teams channel. 

## More Information
For more information about getting started with Teams, please review the following resources:
- Review [Getting Started with Teams](https://msdn.microsoft.com/en-us/microsoft-teams/setup)
- Review [Getting Started with Bot Framework](https://docs.microsoft.com/en-us/bot-framework/bot-builder-overview-getstarted)
- Review [Testing your bot with Teams](https://msdn.microsoft.com/en-us/microsoft-teams/botsadd)

