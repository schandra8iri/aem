# aem

AEM Tutorial

Create a node, see the structure in crx and json
Create a script to dispalye basic HTML
Parabase
Parsys
global.js

Chapters

1. Technology and Architecture (JCR-oak,Sling,OSGI-felix)
2. Installation and setup
3. Content and scripts basics (Sling)
4. Templates and Components
5. Dialogs and Design Dialog
6. CSS, JS and Client library
7. OSGI service and configuration
8. Jobs and workflow
9. Deployment
10. Agents
11. Storage
12. Maintainance
13. Logs
    14

Chapter 2 - Installation and setup

Installation

Developer setup

- Install AEM plugin in eclipse
- Create AEM multmodule project using the below mvn cmd

```sh
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=27 \
 -D aemVersion=6.4.0 \
 -D appTitle="polar Site" \
 -D appId="polar" \
 -D groupId="com.sach" \
 -D frontendModule=general \
 -D includeExamples=n
```

Create a folder under apps called polar, two other folder under polar
templates
components

Create a first component called basepage, with foundation page as super resource type.

Add a heading in basepage.jsp to display something

```json
{
  "jcr:primaryType": "cq:Component",
  "jcr:createdBy": "admin",
  "jcr:title": "Base Page",
  "jcr:created": "Fri Dec 24 2021 00:01:58 GMT+0530",
  "sling:resourceSuperType": "foundation/components/page",
  "componentGroup": "polar",
  "basepage.jsp": {
    "jcr:primaryType": "nt:file",
    "jcr:createdBy": "admin",
    "jcr:created": "Fri Dec 24 2021 00:01:58 GMT+0530",
    "jcr:content": {
      "jcr:primaryType": "nt:resource",
      "jcr:lastModifiedBy": "Administrator",
      "jcr:mimeType": "text/plain",
      "jcr:lastModified": "Fri Dec 24 2021 00:04:49 GMT+0530",
      ":jcr:data": 184,
      "jcr:uuid": "d1d1d71d-3e7b-41a9-b7f3-70b3485a02e2"
    }
  }
}
```

Now create a template called template under base template, point it to basepage component

```json
{
  "jcr:primaryType": "cq:Template",
  "jcr:createdBy": "admin",
  "jcr:title": "Base Template",
  "allowedPaths": ["/content(./*)?"],
  "jcr:created": "Fri Dec 24 2021 00:03:22 GMT+0530",
  "ranking": 100,
  "jcr:content": {
    "jcr:primaryType": "cq:PageContent",
    "jcr:createdBy": "admin",
    "jcr:created": "Fri Dec 24 2021 00:03:22 GMT+0530",
    "sling:resourceType": "polar/components/basepage"
  }
}
```

Go to localhost:4502/siteadmin
Click on website and click on new
Click on New Page and select the base template to creata page
Open the newly created page, to see the heading display

replace editor.html with cf#

Include below script to get the sidekick

```html
<cq:include script="/libs/wcm/core/components/init/init.jsp" />
```

or, inclide head.jsp, which has the above script

````html
<cq:include script="head.jsp" /> <cq:include script="body.jsp" />

below line will add the parsys at the end ```html
<cq:include path="par" resourceType="foundation/components/parsys" />
````

Create new component - Menu as below

```json
{
  "jcr:primaryType": "cq:Component",
  "jcr:createdBy": "admin",
  "jcr:title": "menu",
  "jcr:created": "Fri Dec 24 2021 00:34:36 GMT+0530",
  "sling:resourceSuperType": "foundation/components/parbase",
  "componentGroup": "polar",
  "menu.jsp": {
    "jcr:primaryType": "nt:file",
    "jcr:createdBy": "admin",
    "jcr:created": "Fri Dec 24 2021 00:34:36 GMT+0530",
    "jcr:content": {
      "jcr:primaryType": "nt:resource",
      "jcr:lastModifiedBy": "Administrator",
      "jcr:mimeType": "text/plain",
      "jcr:lastModified": "Fri Dec 24 2021 00:37:06 GMT+0530",
      ":jcr:data": 218,
      "jcr:uuid": "f1d5e6b3-b740-455c-a892-a5974003d5fe"
    }
  }
}
```

parbase component adds the drag and drop ability to the component

Right click on menu and create dialog.
Create cq:EditConfig node
Cretae design_dialog node

```json
{
  "cq:editConfig": {
    "jcr:primaryType": "cq:EditConfig",
    "jcr:createdBy": "admin",
    "jcr:created": "Fri Dec 24 2021 00:46:58 GMT+0530"
  },
  "design_dialog": {
    "jcr:primaryType": "cq:Dialog"
  },
  "dialog": {
    "jcr:primaryType": "cq:Dialog",
    "title": "menu",
    "xtype": "dialog",
    "items": {
      "jcr:primaryType": "cq:Widget",
      "xtype": "tabpanel",
      "items": {
        "jcr:primaryType": "cq:WidgetCollection",
        "tab1": {
          "jcr:primaryType": "cq:Panel",
          "title": "Tab 1"
        }
      }
    }
  }
}
```

Go to the first page created
Open design mode

by clicking on the design button

or

by adding this at the end of the url

    ?wcmmode=design

Design bar is displayed, click on edit
Enble and the required component for the page

Now components should be available for adding to the page

It not displayed, check on different browser
