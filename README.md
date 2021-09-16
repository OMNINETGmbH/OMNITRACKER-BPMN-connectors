# OMNITRACKER BPMN connectors

Welcome to our exchange platform for OMNITRACKER BPMN connectors. Within this platform you will have the possibility to view, add and also discuss about connectors between OMNITRACKER and third-party systems.

## 1. How to participate

### 1.1 Structure of this repository

We've divided our connector packages into different **directories**. Each directory stands for a third-party-tool, e.g. one directory with a connector package for MS Teams. You can either check existing connector packages, update them or add complete new connector packages to the repository. If you update or add new connector packages, your files need to follow some rules, which you can find next.

We've also added one directory called **skeleton**. This contains an empty connector package and a preconfigured README.md file, which you can download and reuse to create new directories.

Within the directory **otconn template generator** you can find a connector package and also a .bpmn file which you can use to configure new .otconn files. The bpmn file contains a BPMN diagram, which allows you to configure a connector package. You can find a detailed description within the README.md within the directory.

### 1.2 Procedure for versioning an existing or adding a new connector packages

1.2.1 *Check first, if there is already an existing connector package connecting to the third-party-system*

You can download and use these connectors within your OMNITRACKER installation.

1.2.2a *If there is one, use the updating possibility for this connector package (Update existing connector package)*

If you want to update an existing connector package, please replace the existing .otconn file. In addition, we want you to update the README.md file of the directory with the new information about the adapted connector package (see 1.4 for detailled description and rules).

1.2.2b *If there is no existing connector package, create and add a new one (New connector package)*

If you want you can use the sceleton directory and / or the *Template Generator BPMN process* (minimum OMNITRACKER version 12.1.100 required) to create a new .otconn file. Otherwise you can also start from scratch to create the .otconn file (see 1.5 for detailed description and rules).

1.2.3 *Commit a pull request*

You can commit a pull request to add new connector packages or update an existing package. Please note 1.4 and 1.5 for the rules.

1.2.4 *OMNINET will check the structure of the containing files within the pull request*

OMNINET will **not automatically test** each connector within the connector packages of your pull request; we will only check the syntax of the .otconn files and README.md which are pulled from users outside of OMNINET.

### 1.3 Check existing connector packages

- Check the existing connector packages with the different directories.
- Each directory contains one .otconn file with multiple connectors within it.
- You will also find a README.md within each folder with detailed information about the connector package.
- Within the issues you can start or enter a discussion about a connector (package).

### 1.4 Rules for versioning an existing connector package

- Use the existing connector package
- Within the file you can add new connectors to the connector package or also adapt existing connectors
- Also modify the README.md of this directory:
  - Adapt the information about PowerShell, the used module(s), valid from, version
  - Adapt the connectors of the connector package:
    - include a short description of the changes you made to each connector
    - add new connectors if necessary

### 1.5 Rules for adding a new connector package

- Add a new directory with the name of the third-party system or added features, if there is no specific third-party system involved
- Add a new README.md file into the directory with the basic information about the connector package
  - PowerShell Module
  - Valid from
  - PowerShell Version
  - Version: Count +1
  - Connectors of the connector package: add each connector with a short description
- Add the new .otconn file (information about the format see 2.2); please note: you need to add new GUIDs within the connector package

## 2. OMNITRACKER BPMN

With the OMNITRACKER BPMN Engine we are able to automate BPMN processes. Therefore, we can use a connector-based service task to automatically perform executed actions, usually in order to control external third-party systems. A "connector" is a script that is executed on the OMNITRACKER server computer. The script can be written either using VBScript or using PowerShell. A connector is packaged inside an XML file; each XML file can contain multiple connectors and data structure definitions. Aside from the script, a connector contains a list of data inputs and data outputs. The data inputs are filled from the BPMN process, and the data outputs are returned to the BPMN process.

### 2.1 Structure of an OMNITRACKER BPMN connector

In order to add one or more new connectors to OMNITRACKER, you must write a file with the extension ".otconn" and place it into the "Connectors" subdirectory of the OMNITRACKER installation folder on the OMNITRACKER server computer. An .otconn file is a text file in XML format; You can use any text editor or XML editor to create the .otconn file. Each .otconn file can contain more than one connector; therefore, the .otconn file also is called a "connector package". All connectors in the package correspond to the same category, and they have access to the same structures and scripts.

Connectors can be implemented in one of the following programming languages:

- VBScript
- PowerShell

### 2.2 .otconn File Format

An .otconn file is an XML file with the following format:

```xml
<?xml version="1.0" encoding="encoding"?>
<connectorPackage guid="pkgguid" category="category" language="language">
  <script>
    <![CDATA[script]]>
  </script>
  <structures>
    <structure name="structname">
      <members>
        <member name="membername" isArray="isArray" type="conntype" />
        <member ... />
        <member ... />
        ...
        <member ... />
      </members>
    </structure>
    <structure>...</structure>
    <structure>...</structure>
    ...
    <structure>...</structure>
  </structures>
  <connectors>
    <connector name="connname" description="conndescription" guid="connguid">
      <input>
        <inputParameter name="parname" type="partype" isArray="isArray" group="group" description="description" optional="optional"/>
        <inputParameter ... />
        ...
        <inputParameter ... />
      </input>
      <output>
        <outputParameter name="parname" type="partype" isArray="isArray" group="group" description="description"/>
        <outputParameter ... />
        ...
        <outputParameter ... />
      </output>
    </connector>
    <connector ...>
        ... second connector ...
    </connector>
    <connector ...>
        ... third connector ...
    </connector>
    ...
    <connector ...>
        ... last connector ...
    </connector>
  </connectors>
</connectorPackage>
```

Please note: pkgguid = Unique ID ("GUID") of the connector package, such as `{6191ab8b-6123-4273-8e5d-d86aead1538c}`. You must generate a new GUID for each .otconn file you write; otherwise, this will cause problems when you have installed multiple connectors with the same GUID.

### 2.3 Connector Script Object Model

Connector scripts can use following global properties and methods. In PowerShell, you need to prefix the property or method names with `$ctx.`, e.g. use `$ctx.Input('parameter1')` whereas you would use `Input("parameter1")` in VBScript.

*Properties*:

- ConnectorName: Returns the name of the connector for which the script currently is executed. All connectors of the package execute the same script; therefore it is necessary to check ConnectorName if your connector package contains more than one connector.
- Input(name): Returns the value of the connector input parameter with the given name. In order to check whether an optional input parameter has a value in VBScript, use `IsNull(Input("name"))`; it will return False if the parameter has a value. In PowerShell, use `$ctx.Input('name') -eq $null`.
- Output(name): Gets or sets the value of the connector output parameter with the given name.

*Methods*:

- CreateStruct name: Creates a new instance of a structure with the given name. The structure must be defined inside the same connector package
- LogError text: Write the specified error text to the process instance's log.
- LogMessage text: Writes the specified informational text to the process instance's log.
- LogWarning text: Writes the specified warning text to the process instance's log.
- RaiseError text: Raise an error with the specified text. (Raising an error normally aborts the script, unless use On Error Resume Next).
