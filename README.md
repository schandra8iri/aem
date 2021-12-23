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
14. 



Chapter 2 - Installation and setup

Installation


Developer setup


- Install AEM plugin in eclipse 
- Create AEM multmodule project 

```sh
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=XX \
 -D aemVersion=cloud \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n
 ```
