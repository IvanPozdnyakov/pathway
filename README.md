<h1>VQI Pathway Editor</h1>
<h2>Introduction</h2>
<h3>Overview</h3>
The VQI Pathway editor is a standard pathway viewer, editor, and analyzer that enriches biologists understanding of the underlying biological process involved in the interaction of proteins, genes, etc. Pathways are visual networks that represent entity interaction in graph form. There are many other pathway editors/analyzers, this specific one aims at being a web-based application that handles editing on the front-end with analysis being delegated to remote services through requests. For additional reference on existing tools and how they might compare to this editor refer to the list below.

<h3>Other tools</h3>
*Pathway Common* - The first tool that will be looked at is Pathway Commons (PC) which has multiple components that add up to the overall package. Firstly PC serves as a pathway database; It’s supportive of typical query functionality such as extraction and publication, it aims to offer clear author attribution and also provide end-users tools for analysis. It uses the BioPAX as the representational standard when storing, passing and receiving pathway information. It pulls in pathway data from source databases but avoids duplicating some of the more advanced databasing features of those databases. On the user-end Pathway Commons offers tools for visualization and analysis. On the web it offers PCViz for simple visualization, primarily as a way to see genes in the context of a pathway. Secondly it offers ChiBE as a slightly more powerful visualization tool that can be downloaded as a Java application. Finally there is the CyPath2 tool which can be used for querying and analysis. This is much more of a studio suite that utilizes flash based cytoscape at the core of it’s design.

*Wikipathways* - Is complementary to the efforts of PC and just the same offers a place to facilitate the contribution and maintenance of pathways. The website is built on MediaWiki software and provides an interface that most people are familiar with. It offers an embedded editor that can be used to alter existing pathways or create new ones. Version history is kept so that changes can be reverted. Pathways can be downloaded and used in a variety of formats including object oriented (JSON,XML, etc) or images (JPG,PNG,etc). Exported files can be used with other tools that handle analysis.

*Pathway Studio* - Pathway Studio is proprietary owned software with associated use charges through licensing. It is available both through web and can be downloaded. Being that it is closed source there is no access to internal design of the application. Thusly the study will look at it in terms of its available features on the user end. Being that this is company owned software the natural expectation going into this survey study is that it’s the most powerful in terms of the features it offers and overall production quality.

<h3>Feature List</h3>
* Editing
  * Add/Remove/Update entities
  * Add/Remove/Update interactions
  * Bundle/Unbundle Entities
  * Collapse/Uncollapse Bundles
  * Save Remote/Download locally pathway
  * Maintain history of edits
  * Spray data over entities
  * Load multiple pathways on one canvas
  * Searching for entities
  * Duplicate entities 
* Analysis
  * Display found paths & scores (external service)
* Design
  * API (integerate with other services)
  * None-GUI Application (fallback)
  * Self-Documenting Code
  * Test framework

<h2>Design</h2>
The following section will go over the application at it's design level. Starting with how the project is currently formatted. This may very well change in the future thusly this section of the document **needs** to be kept up to date, to avoid confusion. Since this application uses Cytoscape.js as the design base this section will include a high level explaination of how Cytoscape is structured, including the purpose of the core and collection.

<h3>Project Structure</h3>

*VQI_PathwayEditor* - Overarching superclass, can be instantiated to run in 'test' or 'regular' modes. When running in test mode the internal functions and objects are exposed. The class maintains the service list, definitionHub, and other globals that are necessary in both GUI and NoGUI versions of the applications as well as functions that are used universally.

*VQI_PathwayEditor.NoGUI* - This subclass maintains the code for the NoGUI version of the application. This subclass can be instantiated easily, in the sense that it's dependency free. This means that it doesn't use cytoscape.js or any other external library since it doesn't require rendering. Despite being very lightweight the NoGUI editor still has useful functionality including the ability to load in pathways into memory, spray data over the pathways, print json representation of graph, download a json representation of the graph, get/set person ID, and call the find & score path service.

*VQI_PathwayEditor.GUI* - This subclass is where the bulk of the application is located. The high level overview of the subclasses structure is as followed.

* Globals (strVar maintains the applications view)
* Set the innerHTML of the parent container
* Code to execute once HTML loaded
 * internal functions
 * visual pathway (Initialize cytoscape graph)
 * ---Set type styling properties
 * ---Set layout
 * ---Code to excute once cytoscape graph loaded
 * ------This includes setting listeners and setting the view's state
* Setting the functionality on the dialog boxes
* Load in the remote pathway list
* Set listeners on the GUI
* API (external methods to call)
* Callback

<h3>Core</h3>
<h3>Collection</h3>
<h3>Test Framework</h3>
<h2>Dependencies</h2>
<h3>Cytoscape.js</h3>
<h3>Bootstraps</h3>
<h3>D3</h3>
<h2>Interface</h2>
<h2>Known Bugs</h2>