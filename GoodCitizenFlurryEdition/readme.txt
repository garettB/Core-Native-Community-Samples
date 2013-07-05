GoodCitizen Flurry Edition

========================================================================
Sample Description:

 The GoodCitizen sample is an application that is designed to introduce you to a
 number of common development practices that you can use in your own
 applications.

 When you run the application, the application displays a spinning cube that you
 can change the color of by selecting different menu options.
 
 Serveral common actions performed by the user are now logged using the Flurry
 analytics service which has been integrated into the application. Continue
 reading for more details.

 Feature summary
 - Display a 3D cube that responds to a light source
 - Load textures and render text on the screen
 - Handle orientation changes* and touch events*
 - Display a menu on a swipe down gesture*
 - Stop content from being rendered when the app is inactive
 - Save the application state on exit and reload at startup
 - Perform a clean termination
 - Send analytics data to the Flurry server when backgrounded or inactive
 
 * denotes an action logged by the Flurry analytics service


========================================================================
Requirements:

 - BlackBerry® 10 Native SDK 10.0.10 or higher
 - One of the following:
   - BlackBerry® 10 device
   - BlackBerry® 10 simulator

========================================================================
Importing a project into the Native SDK:

 1. From the the Sample apps page, download and extract the sample application.
 2. Launch the Native SDK.
 3. On the File menu, click Import.
 4. Expand General, and select Existing Projects into Workspace. Click Next.
 5. Browse to the location where you extracted the sample app, and click OK.
    The sample project should display in the the Projects section.
 6. Click Finish to import the project into your workspace.

========================================================================
Configuring the sample to use Flurry:

 1. If you have not already done so, create an account with Flurry: 
 	http://www.flurry.com/
 2.	Create a new BlackBerry application in your Flurry account, retrieve the API Key
 	and download the SDK
 3. Drag the Flurry folder of the SDK to the root directory of this project. The folder
 	should have the structure:
 	Flurry/FlurryC.h
 	Flurry/Flurry.h
 	Flurry/armle-v7/libFlurry.a
 	Flurry/x86/libFlurry.a
 4.	Replace "YOUR_API_KEY" in main.c with your API Key retrieved in step 2
 5. Compile and run on a simulator or real BlackBerry 10 device
 6. After testing this application Events should begin to appear in your Flurry dashboard
 	within a few hours, and data in the dashboard in about half a day
 	
========================================================================
Configuring your own native application:

1. Drag the /Flurry folder to the root of your project
2. Open the bar-descriptor.xml file for your project and make the following changes:
	a)	In the "Application" tab add the "read_device_identifying_information" and "access_internet"
		permissions
	b) 	In the "Source" tab change this line
		<env var="LD_LIBRARY_PATH" value="app/native/lib"/>
		to
		<env var="LD_LIBRARY_PATH" value="app/native/lib:/usr/lib/qt4/lib"/>
3.	Add reference to the FlurryC.h header:
	In the project explorer right-click your project name then select 'Properties' > 'C/C++ General'
	> 'Paths and Symbols' > 'GNU C' (under languages) > 'Add...', after clicking this button a dialog
	with the header 'Add directory path' should appear. From this dialog check 'Add to all configurations'
	then click 'Workspace' and browse to the /Flurry folder within your project.
4.	Add reference to library dependencies:
	In the project explorer right-click your project name then select 'Properties' > 'C/C++ Build' >
	'Settings' > 'QCC Linker' > 'Libraries'. Under "Library Paths" add the following entries:
		${PROJECT_ROOT}/Flurry/${CPUVARDIR}
		${QNX_TARGET}/${CPUVARDIR}/usr/lib/qt4/lib
	Under "Libraries" add the following libraries:
		cpp
		QtCore
		curl
		socket
		crypto
		packageinfo
		screen
		bbdevice
		Flurry
5.	Done. You should now be able to add '#include "FlurryC.h"' to your application and begin making calls to the
	Flurry analytics SDK.
	
Alternate instructions can be found here:
http://support.flurry.com/index.php?title=Analytics/GettingStarted/TechnicalQuickStart/Blackberry

API References for the Flurry analytics SDK are bundled with the SDK and can also be found online here:
http://support.flurry.com/index.php?title=Analytics/Code/Doc/Blackberry
 
