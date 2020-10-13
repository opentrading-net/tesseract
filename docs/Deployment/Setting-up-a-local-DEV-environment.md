1. Get a copy of the [Tesseract](https://OpenTradingNetwork@dev.azure.com/OpenTradingNetwork/Tesseract/_git/Tesseract) and build the solution in Visual Studio 2019
2. Create assembly directories for the console assemblies and the web assemblies

   * The app config for a tesseract instance (web or console) has a TypeAssembliesPath property of the tesseractDefaults config section
      ```
      <tesseractDefaults>
          <add key="TypeAssemblyPath" value="C:\Repos\OpenTradingNetwork\WebAssemblies" /> 
          ...
       </tesseractDefaults>
      ``` 
3. Use the \Database\Tesseract.Sql script to create a database with the Objects temporatal table. Edit the script to replace 'Tesseract' with your test database name. The default useful database are:

   * Demo - used for interactive demos
   * Test - used for the unit integration tests
   
   The app config has an EntitiesName setting in the tesseractDefaults config section. This points the tesseract instance at an Entity frameworks connection string, e.g.

  
      ```
        <connectionStrings>
          <add name="Test" connectionString="metadata=res://*/Objects.ObjectModel.csdl|res://*/Objects.ObjectModel.ssdl|res://*/Objects.ObjectModel.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=.;initial catalog=Test;integrated security=True;MultipleActiveResultSets=True;App=EntityFramework&quot;" providerName="System.Data.EntityClient" />
          <add name="Demo" connectionString="metadata=res://*/Objects.ObjectModel.csdl|res://*/Objects.ObjectModel.ssdl|res://*/Objects.ObjectModel.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=.;initial catalog=Demo;integrated security=True;MultipleActiveResultSets=True;App=EntityFramework&quot;" providerName="System.Data.EntityClient" />
        </connectionStrings>
        <tesseractDefaults>
          ...
          <add key="EntitiesName" value="Demo" />
        </tesseractDefaults>
      ```

4. Run the type console and test that setup if working with the following commands (ignore the comments)

   * dir Tests -- change directory to the Tests directory
   * bootstrap -- setup bootstrap records in the database
   * remote false -- disable cache messages to remote instances
   * commands CompileAndCreatePersistedType2Objects.cmd -- run a test command to compile types and run scripts

5. Tesseract instances inform other instances of changes to their in-memory cache. An instance knows about other instances via the list of instances in the tesseractInstances collection in the app config. The type console should have this setting so that it knows about the test application
  
      ```
      <tesseractInstances>
           <add key="WebApp" value="http://localhost:60996/api/Cache" />
      </tesseractInstances>
      ```
 
6. To set up the system views then run the type console and run these commands:

   * dir System
   * commands System.cmd

7. Run the web application and you should see the menu and be access system views:


   ![image.png](/.attachments/image-67d24839-7648-4641-8bd4-17c297c9ec42.png)