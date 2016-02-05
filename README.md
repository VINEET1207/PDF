# PDF Adapter Overview
The PDF Adapter allows to read and write PDF Acroform documents .  The PDF adapter user Apache PDF Box for the support. 


## Minimum Requirements : 

WTX v8.4.1.x <br>
ITX v9.0.0.x

## Command Alias : 

Adapter commands can be specified by using a command string on the command line or creating a command file that contains adapter commands. The execution command syntax is:

-IM[alias] card_num <br>
-OM[alias] card_num


where -IM is the Input Source Override execution command and -OM is the Output Target Override execution command, alias is the adapter alias, and card_num is the number of the input or output card. The following table shows the adapter alias and its execution command.


Adapter 	:  PDF <br>
Alias 	        :  PDF <br>
As Input        :  -**IMPDF**card_num <br>
As Output       :  -**OMPDF**card_num <br>    	  


## PDF Adapter commands

The following table lists valid commands for the PDF Adapter, the command syntax

Location (-U)     : Location of the Input / output PDF Document<br>
Schema (-S)	  : Location of the Schema<br>
Template Location (-P )  : Location of the PDF Template<br>. Supported on the Target only and is optional argument
Named file Location (-N )  : Location of the Named file generated by the importer Template. Supported on the Target only

## PDF Adapter Command Line Examples
###Inbound Adapter : 


Command Line : -U JohnDoe1040.pdf -S f1040.xsd 

GET RULE : =PARSE(GET("PDF", "-S f1040.xsd", BlobIn))

###Outbound Adapter : 


Command Line with Template : -U My1040.pdf -N f1040.names -P f1040.pdf

PUT RULE : PUT("PDF", "-U My1040.pdf -N f1040.names -P f1040.pdf -T", Input))



## PDF Adapter Installation Instructions 
### Design Studio

a) Drop com.ibm.websphere.dtx.ui.importers.pdf.nl_Version.jar, com.ibm.websphere.dtx.ui.importers.pdf.version.jar
to "WTX INSTALL"\DesignStudio\wtx_eclipse\eclipse\plugins 

b) Drop m4pdf.jar in to "WTX INSTALL" <br>

c) Edit adapters.xml and add the following line 

M4Adapter name="Abode PDF" alias="PDF" id="165" type="app" class="com/ibm/websphere/dtx/m4pdf"

d) Download Apache PDFBox artifacts from [PDFBox](https://pdfbox.apache.org/download.cgi) version 1.8.x Copy pdfbox-xxx.jar to <WTX INSTALL DIR> 


d) Invoke cleanextenderstudio.bat.
 
### Runtime

a) Drop m4pdf.jar in to <WTX INSTALL> on windows and to <WTX INSTALL>/libs on UNIX <br>
b) Edit adapters.xml and add the following line (UNIX, the file is present under config folder) <br>

M4Adapter name="Abode PDF" alias="PDF" id="165" type="app" class="com/ibm/websphere/dtx/m4pdf"


d) Download Apache PDFBox artifacts from [PDFBox](https://pdfbox.apache.org/download.cgi) version 1.8.x Copy pdfbox-xxx.jar to <WTX INSTALL DIR> <br>


####Note : For any defects or usage concerns, please open an issue ticket and shall be addressed. 