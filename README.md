# Readme

This project provides a parent POM file that can be used as starting point for using JEAF Generator.

<br>

## How to use this POM

Basically you have two options:

*  to use this POM as parent POM for your projects
* copy it and use it as a template



## How does this POM work

### JEAF Generator configuration

This POM defines properties for all configuration parameters that are supported by JEAF Generator. Whenever new properties will be introduced then this parent POM will be updated and a new version will be released.

<br>

### Profiles
In addition to all configuration parameters also the following profiles are defined:

* `RunCodeGenerationFromXMIFile`<br>As the name implies, this profile can be used to run the code generation directly from an so called XMI file. XMI files are a tool independent representation of your UML model (e.g. from [MagicDraw UML](https://www.3ds.com/products/catia/no-magic/magicdraw))<br><br>

* `RunCodeGenerationFromModelArtifact`<br>In addition to classic file based approach there also is a variant / profile where the XMI files are provided as Maven artifact.<br>

Besides the location from which the XMI files are read the profiles do not have any further differences.

<br>

## Usage as parent POM

When using this POM as parent POM the a 

Before you can start with code generation you have to provide a minimum set of information:

* Location of the XMI files (either on file system or as Maven artifact)
* Name of the main model file
* UML package



### Run Code Generation from local XMI file

To run JEAF Generator using a local XMI file you have to configure at least the following properties in your POM.

```xml
<properties>
  	<!--
			Directory which contains all XMI files. The files have to be exported from MagicDraw UML using its Eclipse UML2
			Export v2.x (File - Export To - Eclipse UML2 (v2.0x) XMI File)
		-->
		<xmiDirectory></xmiDirectory>

		<!-- UML package (plus subpackages) which will be the one that is considered during code generation. --> 
		<umlPackage>com.anaptecs.jeeaf.demo</umlPackage>

		<!--
			Name of the model file that should be used. Usually it has the same name as the MagicDraw UML project. Only the
			name of the file has to be provided as we assume that the file is located in the XMI directory.
		-->
		<umlModelFile></umlModelFile>
</properties>
```



### Run Code Generation from Maven Artifact

To run JEAF Generator using a Maven artifact that contains the XMI files of the model, have to configure at least the following properties in your POM.

<br>

**Notes:**

+ Please be aware when using the Maven Artifact approach that then your project also needs to have a Maven dependency on the artifact.
+ In general we recommend to use the model artifact approach, as storing XMI files inside SCM systems like git will blow up repository sizes over time

<br>

```xml
<properties>
		<!--
			Group ID of the artifact that contains the XMI files of the UML model.
			
			The UML model can either be defined by pointing to the directory where the XMI files are located directly or by
			referencing an artifact that contains the XMI files.
		-->
		<modelArtifactGroupID></modelArtifactGroupID>

		<!--
			Artifact ID of the artifact that contains the XMI files of the UML model.
			
			The UML model can either be defined by pointing to the directory where the XMI files are located directly or by
			referencing an artifact that contains the XMI files.
		-->
		<modelArtifactArtifactID></modelArtifactArtifactID>

		<!--
			XMI Path inside the artifact that contains the XMI files of the UML model.
		-->
		<modelArtifactXMIPath>xmi</modelArtifactXMIPath>

		<!-- UML package (plus subpackages) which will be the one that is considered during code generation. --> 
		<umlPackage>com.anaptecs.jeeaf.demo</umlPackage>

		<!--
			Name of the model file that should be used. Usually it has the same name as the MagicDraw UML project. Only the
			name of the file has to be provided as we assume that the file is located in the XMI directory.
		-->
		<umlModelFile></umlModelFile>
</properties>
```



