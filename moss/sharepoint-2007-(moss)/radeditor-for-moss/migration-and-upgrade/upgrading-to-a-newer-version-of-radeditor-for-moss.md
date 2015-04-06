---
title: Upgrading to a newer version of RadEditor for MOSS
page_title: Upgrading to a newer version of RadEditor for MOSS | UI for ASP.NET AJAX Documentation
description: Upgrading to a newer version of RadEditor for MOSS
slug: moss/sharepoint-2007-(moss)/radeditor-for-moss/migration-and-upgrade/upgrading-to-a-newer-version-of-radeditor-for-moss
tags: upgrading,to,a,newer,version,of,radeditor,for,moss
published: True
position: 3
---

# Upgrading to a newer version of RadEditor for MOSS



## 

Here is how to upgrade your RadEditor for MOSS from a previous version to the latest one. In the instructions below we will upgrade from __v5.2.2.0__ to__v5.3.1.0.__

In SharePoint 2007 deployments use the following steps to upgrade an existing version of RadEditor for MOSS to a newer version of RadEditor for MOSS:

1. Uninstall the old version of RadEditor for MOSS as described in section [Uninstalling RadEditor]({%slug moss/sharepoint-2007-(moss)/radeditor-for-moss/installation-and-deployment/uninstalling-radeditor%}).

1. Install the new version of Telerik RadEditor for MOSS as described in section [Installing RadEditor in a MOSS 2007 farm]({%slug moss/sharepoint-2007-(moss)/radeditor-for-moss/installation-and-deployment/installing-radeditor-in-a-moss-2007-farm%}).

1. Paste the following __<dependentAssembly>__ element in the __<assemblyBinding>__ tag in the __web.config__file:

````XML
	    <runtime>
	    ...
	        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
	          <dependentAssembly>
	            <assemblyIdentity name="RadEditorSharePoint" publicKeyToken="1f131a624888eeed" culture="neutral" />
	            <bindingRedirect oldVersion="1.0.0.0-<old version>" newVersion="<new version>" />
	          </dependentAssembly>
	    ...
	        </assemblyBinding>
	    ...
	    </runtime>
````

The <old version=""> here represents the old product version (5.2.2.0), while <new version=""> should be replaced with the current version (5.3.1.0 in this example):

````XML
	    <dependentAssembly>
	       <assemblyIdentity name="RadEditorSharePoint" publicKeyToken="1f131a624888eeed" culture="neutral" />
	       <bindingRedirect oldVersion="1.0.0.0-5.2.2.0" newVersion="5.3.1.0" />
	    </dependentAssembly> 
````



1. __(Web Parts)__ To enable the RadEditor Web Parts, which were created with the previous version, open the __web.config__file of your SharePoint site and add the following line right above the __</SafeControls>__ tag:

````XML
	    <SafeControl Assembly="RadEditorSharePoint, Version=<old version>, Culture=neutral, PublicKeyToken=1f131a624888eeed" 
	        Namespace="Telerik.SharePoint" TypeName="*" Safe="True" /> 
````

In this case __<old version>__ is__5.2.2.0__, so the __<SafeControl>__ tag should look like this:

````XML
	    <SafeControl Assembly="RadEditorSharePoint, Version=5.2.2.0, Culture=neutral, PublicKeyToken=1f131a624888eeed" 
	        Namespace="Telerik.SharePoint" TypeName="*" Safe="True" /> 
````

