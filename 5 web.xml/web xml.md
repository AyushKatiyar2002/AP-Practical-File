# 5. Undersatanding Modification Of Web.XML
 ## 1. What is the Default Servlet ?
  The default servlet is the servlet which serves static resources as well as serves the directory listings (if directory listings are     enabled). It is declared globally in $CATALINA_BASE/conf/web.xml.
 ## 2. What is Web XML?
  The web .xml file is the deployment descriptor for a Servlet-based Java web application (which most Java web apps are). Among other     things, it declares which Servlets exist and which URLs they handle. The part you cite defines a Servlet Filter. Servlet filters can     do all kinds of preprocessing on requests.
 ## 3. Why we use web .xml?
  Generally speaking, this is the configuration file of web applications in java. It instructs the servlet container (tomcat for ex.)     which classes to load, what parameters to set in the context, and how to intercept requests coming from browsers.
  There you specify:
  - what servlets (and filters) you want to use and what URLs you want to map them to
  - listeners - classes that are notified when some events happen (context starts, session created, etc)
  - configuration parameters (context-params)
  - error pages, welcome files
  - security constraints
  In servlet 3.0 many of the web.xml parts are optional. These configurations can be done via annotations (@WebServlet, @WebListener).
 ## 4. How to modify web.xml to enable https?
  ### To modify the web.xml file to enable HTTPS
  1. Open the web.xml file usually located in the $CATALINA_HOME/webapps/moab/WEB-INF/ directory.
  2. Add a <security-constraint> section to cause all pages to be hosted with HTTPS.
  ### Code:
  ```
  <web-app>
    ...
      <security-constraint>
       <web-resource-collection>
         <web-resource-name>Viewpoint Secure URLs</web-resource-name>
         <url-pattern>/*</url-pattern>
       </web-resource-collection>
       <user-data-constraint>
        <transport-guarantee>CONFIDENTIAL</transport-guarantee>
       </user-data-constraint>
      </security-constraint>
  </web-app>
  ```
| Property | Description |
| --- | --- |
| Debug | Debugging level. It is not very useful unless you are a tomcat developer. As of this writing, useful values are 0, 1, 11, 1000. |
| Listings | If no welcome file is present, can a directory listing be shown? value may be true or false [false] Welcome files are part of the servlet api. WARNING: Listings of directories containing many entries are expensive. Multiple requests for large directory listings can consume significant proportions of server resources. |
| Precompressed | If a precompressed version of a file exists (a file with .br or .gz appended to the file name located alongside the original file), Tomcat will serve the precompressed file if the user agent supports the matching content encoding (br or gzip) and this option is enabled. [false] The precompressed file with the with .br or .gz extension will be accessible if requested directly so if the original resource is protected with a security constraint, the precompressed versions must be similarly protected. It is also possible to configure the list of precompressed formats. The syntax is comma separated list of [content-encoding]=[file-extension] pairs. For example: br=.br,gzip=.gz,bzip2=.bz2. If multiple formats are specified, the client supports more than one and the client does not express a preference, the order of the list of formats will be treated as the server preference order and used to select the format returned. |
| ReadmeFile | If a directory listing is presented, a readme file may also be presented with the listing. This file is inserted as is so it may contain HTML. |
| GlobalXsltFile | If you wish to customize your directory listing, you can use an XSL transformation. This value is a relative file name (to either $CATALINA_BASE/conf/ or $CATALINA_HOME/conf/) which will be used for all directory listings. This can be overridden per context and/or per directory. See contextXsltFile and localXsltFile below. The format of the xml is shown below. |
| contextXsltFile | You may also customize your directory listing by context by configuring contextXsltFile. This must be a context relative path (e.g.: /path/to/context.xslt) to a file with a .xsl or .xslt extension. This overrides globalXsltFile. If this value is present but a file does not exist, then globalXsltFile will be used. If globalXsltFile does not exist, then the default directory listing will be shown. |
| LocalXsltFile | You may also customize your directory listing by directory by configuring localXsltFile. This must be a file in the directory where the listing will take place to with a .xsl or .xslt extension. This overrides globalXsltFile and contextXsltFile. If this value is present but a file does not exist, then contextXsltFile will be used. If contextXsltFile does not exist, then globalXsltFile will be used. If globalXsltFile does not exist, then the default directory listing will be shown. |
| Input | Input buffer size (in bytes) when reading resources to be served. [2048] |
| Output | Output buffer size (in bytes) when writing resources to be served. [2048] |
| Readonly | Is this context "read only", so HTTP commands like PUT and DELETE are rejected? [true] |
| FileEncoding | File encoding to be used when reading static resources. [platform default] |
| UseBomIfPResent | If a static file contains a byte order mark (BOM), should this be used to determine the file encoding in preference to fileEncoding. [true] |
| SendfileSize | If the connector used supports sendfile, this represents the minimal file size in KB for which sendfile will be used. Use a negative value to always disable sendfile. |
| UseAcceptRanges | If true, the Accept-Ranges header will be set when appropriate for the response.[true] |
| ShowServerInfo | Should server information be presented in the response sent to clients when directory listing is enabled. [true] |
| SortListings | Should the server sort the listings in a directory. [false] |
| sortDirectoriesFirst | Should the server list all directories before all files. [false] |
| AllowPartialPut | Should the server treat an HTTP PUT request with a Range header as a partial PUT? Note that RFC 7233 clarified that Range headers are only valid for GET requests. [true] |
  
