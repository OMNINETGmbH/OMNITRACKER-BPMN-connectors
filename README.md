# OMNITRACKER BPMN connectors

Welcome to our exchange platform for OMNITRACKER BPMN connectors. Within this platform you will have the ability to view, add and also discuss about connectors between OMNITRACKER and third-party systems. 

 
## How to participate

### Structure of this repository

We've devided our connector packages into different folders. Each folders stands for a third-party-tool. e.g. one folder with one connector package for MS Teams, etc. You can either check existing connector packages, update them or add complete new connector packages to the repository. If you update or add new connector packages, your files need to follow some rules, which you can find next.

### Rules for updated and new connector packages
1. Check first, if there is already an existing connector package connecting to the third-party-system
2a. If there is one, use the updating possibility for this connector package
*Update existing connector package*
2b. If there is no existing connector package, create and add a new one
*New connector packages*
- Please add a new folder with the name of the third-party system 
3. Start a pull request
4. OMNINET will check the structure of the containing files within the pull request
**Please note**: OMNINET will **not test** each connector; we will only check the syntax of the .otconn files which are pulled from users outside of OMNINET.

### Check existing connector packages
### Versioning an existing connector package
### Creation of a new connector package

## OMNITRACKER BPMN
With the OMNITRACKER BPMN Engine we are able to automate BPMN processes. Therefore, we can use a connector-based service task to automatically perform executed actions, usually in order to control external third-party systems. A "connector" is a script that is executed on the OMNITRACKER server computer. The script can be written either using VBScript or using PowerShell. A connector is packaged inside an XML file; each XML file can contain multiple connectors and data structure definitions. Aside from the script, a connector contains a list of data inputs and data outputs. The data inputs are filled from the BPMN process, and the data outputs are returned to the BPMN process.

### Structure of an OMNITRACKER BPMN connector
In order to add one or more new connectors to OMNITRACKER, you must write a file with the extension ".otconn" and place it into the "Connectors" subdirectory of the OMNITRACKER installation folder on the OMNITRACKER server computer. An .otconn file is a text file in XML format; You can use any text editor or XML editor to create the .otconn file. Each .otconn file can contain more than one connector; therefore, the .otconn file also is called a "connector package". All connectors in the package corresponds to the same category, and they have access to the same structures and scripts.

Connectors can be implemented in one of the following programming languages:
- VBScript
- PowerShell

### .otconn File Format
An .otconn file is an XML file with the following format:

![grafik](https://user-images.githubusercontent.com/61735509/121145278-1245ef00-c83f-11eb-9aef-5511df2ee493.png)

Please note: pkgguid = Unique ID ("GUID") of the connector package, such as "{6191ab8b-6123-4273-8e5d-d86aead1538c}". You must generate a new GUID for each .otconn file you write; otherwise, this will cause problems you have installed multiple connectors with the same GUID.

### Connector Script Object Model
Connector scripts can use following global properties and methods. In PowerShell, you need to prefix the property or method names with "$ctx.", e.g. use $ctx.Input('parameter1') whereas you would use Input("parameter1") in VBScript. 

*Properties*:
- ConnectorName: Returns the name of the connector for which the script currently is executed. All connectors of the package execute the same script; therefore it is necessary to check ConnectorName if your connector package contains more than one connector.
- Input(name): Returns the value of the connector input parameter with the given name. In order to check whether an optional input parameter has a value in VBScript, use IsNull(Input("name")); it will return False if the parameter has a value. In PowerShell, use "$ctx.Input('name') -eq $null".
- Output(name): Gets or sets the value of the connector output parameter with the given name.

*Methods*:
- CreateStruct name: Creates a new instance of a structure with the given name. The structure must be defined inside the same connector package 
- LogError text: Write the specified error text to the process instance's log.
- LogMessage text: Writes the specified informational text to the process instance's log.
- LogWarning text: Writes the specified warning text to the process instance's log.
- RaiseError text: Raise an error with the specified text. (Raising an error normally aborts the script, unless use On Error Resume Next).
