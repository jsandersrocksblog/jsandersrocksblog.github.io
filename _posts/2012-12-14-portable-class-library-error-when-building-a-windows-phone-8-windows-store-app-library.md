I had a customer issue that I thought I would share in the event you run into this issue (it may save you some heartburn).

Here is the error:

<font face="Consolas">The "Vbc" task failed unexpectedly. <br />System.Runtime.InteropServices.COMException (0x80004005): Unable to find required file &#8216;Microsoft.VisualBasic.dll&#8217;.</font>

&#160;

The repro of this is as follows:

With WP8 SDK and VS2012 Pro or above installed:

1. Create a new Visual Basic Portable Class Library

2. Choose .NET 4.5, Windows Phone 8, and Windows Store apps as the targets (or if you leave Windows Store apps unchecked)

3. Build project

&#160;

The solution is quite simple and should be in the next release of Visual Studio 2012

1. Close Visual Studio

2. Open the vbproj file with a text editor like notepad

3. Find the first entry <ProjectTypeGuids> and after the closing tag add: <VBRuntime>Embed</VBRuntime>

Example:&#160; 

&#160;&#160;&#160; <ProjectTypeGuids>{14182A97-F7F0-4C62-8B27-98AA8AE2109A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
&#160;&#160;&#160; <VBRuntime>Embed</VBRuntime>

4.&#160; Rebuild the project

&#160;

Let me know if this helped you!

Peace,

Jeff