# The Servlet

Contains several predifined servlet, to serve as the basic template for servlet projects.

Mainly as followed

| Name        	| Description                                                                                                                                             	|
|-------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------	|
| CorePage    	| Provides the basic servlet template, where instance thread isolation is enforced. This extends the standard HttpServlet implementation.                 	|
| CoreApiPage 	| Predefined JSON API endpoint which integrates with APIBuilder                                                                                           	|
| DStackPage  	| Additional integration with DStack data, and their various data providers. In addition, this integrate with local file configuration provider (DConfig) 	|
| BasePage    	| Adds in default user authentication, and static file serving                                                                                            	|
| CommonsPage 	| Add in most common functionality used in a complete project. Such as integration with Vue.js (via node) front end, and development mode API.            	|

