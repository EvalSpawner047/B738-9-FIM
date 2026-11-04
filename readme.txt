 
 Title: PDF Technical Publication README.txt
 Copyright: © The Boeing Company
 Modified: 2022-08-31
 Modified By: 275142
 Export Control: Not subject to U.S. Export Administration Regulations (EAR)
 (15 C.F.R. Parts 730-774) or U.S. International Traffic in Arms Regulations
 (ITAR), (22 C.F.R. Parts 120-130)
 
 Table of Contents:

 	- PDF Technical Publications Overview
		- Package Structure & Contents
		- How to View a PDF Technical Publication
		- Managing Publication Supplements
		- Package File Name Convention
	- JSON-LD Metadata
		- PDF Technical Publication Vocabulary

 ===========================================================================
                   PDF Technical Publication Overview
 ===========================================================================

 A PDF Technical Publication (PTP) package is a ZIP archive that contains
 data files for a Boeing airplane support document. 
 
 Package Structure & Contents
 -----------------------------
 
 Data files/directories found in a PTP ZIP archive file are:

	- A uniquely named folder/directory containing data files, including:
		- One or more Portable Document Format (PDF) files
		- An "index.html" file that, when viewed in a web browser,
		  will display publication metadata and a table of contents
		  with links to the PDF files
		- This readme.txt file
		  
 Example:
	
	ALL_ACMS__D123456-01__PDF_20120201T000000Z.zip (the PTP zip package)
		/ALL_ACMS__D123456__PDF_20120201T000000Z (a folder/directory)
    		index.html
    		ACM___.PDF
    		readme.txt

 How to View a PDF Technical Publication
 ----------------------------------------
 
 1. Unzip the PTP ZIP archive to any local device (i.e. hard drive, portable
 media, etc.) or network location.
 
 2. Navigate to the folder/directory where the archive was unzipped and
 double-click the index.html file. This should open in the default web
 browser and display the publication with a table of contents that links to
 the PDF files.

 3. A PDF reader is required to render the Portable Document Format (PDF)
 files. Some web browsers, like Chrome and Firefox, come with default PDF
 readers embedded within them. Should an issue occur when viewing PDF files,
 it is recommended that a download and install of the most current version
 of Adobe Reader be performed if compatible with your device.
 (https://acrobat.adobe.com/us/en/acrobat/pdf-reader.html).

 Managing Publication Supplements
 ---------------------------------
 
 Some publications have supplemental data that is important to make 
 available to users of a publication. Examples of Supplements include
 Temporary Revisions, Airline Revisions, Revision Notices, and Process
 Document Departures.
 
 The PTP table of contents (i.e. the index.html) has a "Supplemental
 Material" hyperlink that points to a directory on the local Windows C:  
 drive where supplements can be manually stored and accessed by clicking
 on the link.
 
 To utilize this feature when receiving supplement material:

 1. Create a directory for the parent document per the "Supplemental 
    Material" link path found in the index.html table of contents file.

 2. Extract the supplement files to this location.

 3. Users clicking the "Supplemental Material" link will be navigated to the 
    location where the files are stored.
 
 The default "Supplemental Material" location path linked to is as follows:
 
 file:///C:/PDF/<OEM>/<Type>/<Identifer>
 
 where: 
 <OEM> = The original equipment manufacturer (default value is "TBC")
 <Type> = A unique acronym for the type of publication
 <Identifier> = the document identifier
 
 Example: file:///C:/PDF/TBC/SDS/D633W101-ZAP
 
 If the PTP files are being stored on a shared network location, the 
 "Supplemental Material" link in the HTML may be updated as desired.
 
 Package File Name Convention
 -----------------------------
 
 The PTP ZIP archive filename and the root directory name within the ZIP 
 archive are uniquely named to allow for many packages to be stored/unzipped
 in the same location without creating conflicting directory names.
 
 The unique name is composed of seven elements that are delimited by an 
 underscore "_". Fields that are not used will be present, but will be blank.
 
 1. Customer Code: The Boeing three-letter code for whom the document was
   customized for. If not customized, this defaults to "ALL".

 2. Document Type: A unique acronym for the document type.

 3. Volume Type: A unique acronym for the volume type (if volume based).

 4. Identifier: The document number.

 5. Supplement Identifier: the identifier of a supplement publication.

 6. Product Label: Default value of "PDF" for the PTP product.

 7. Issue Date: The issue date of the publication.


 ===========================================================================
                  JSON-LD Metadata
 ===========================================================================
 
 The PTP index.html file has metadata encoded into it using the W3C 
 "JSON-based Serialization for Linked Data" format (JSON-LD). 
 
 Boeing has provided this data to enable customers to extract a limited
 number of metadata elements that customer systems can use to provide 
 enhanced functionality to its users. 

 This documentation will not provide details about what JSON-LD is or
 how to use it. Please refer to the W3C specification or other online
 resources about JSON-LD for more details. As normal JSON data, it is 
 relatively simple for most developers to leverage this data without
 having to know much about JSON-LD itself.

 More about JSON-LD can be found here:
 - W3C Specification: https://www.w3.org/TR/json-ld/
 - JSON-LD Website: https://json-ld.org/
 - Software Implementations: https://json-ld.org/#developers 

 ------------------------------------------
 PDF Technical Publication Vocabulary v1.0
 ------------------------------------------
 
 The JSON-LD data in a PTP document uses a "vocabulary" of terms that
 describe data objects and their properties. The following describes the 
 "types" (objects) and "properties" used to describe a PTP publication.
  
 -----------------------------
 Type: PdfTechPub

	A PDF Technical Publication.
	
	Has properties: applicabilityLabel applicableAirplaneIdType 
	applicableAirplaneRange applicableEngine applicablePart
	assignedSubject customizedFor exportControlStatement
	fmsmCalibrationUnit fmsmQuantityUnit identifier issueLevel issued
	modified MSGRevision ptpVocabVersion rightsHolder rightsHolderCage
	rightsStatement supplementLink title valid volumeTitle
	
	The HTML document shall have only one PdfTechPub. Unless
	otherwise specified, all Properties of PdfTechPub appear only once.

 -----------------------------
 Property: applicabilityLabel
	
	Gives a description of applicability.
	
	Value type is plain text.
		
 -----------------------------
 Property: applicableAirplaneIdType
	
	Gives the type of identifier used in the applicableAirplaneRange list.
	
	Value type is one of: 'variableEffectivity', 'basicEffectivity', 
	'serialNumber', or 'lineNumber'.
				
 -----------------------------
 Property: applicableAirplaneRange
	
	Gives a list of applicable airplane ranges.
	
	Each listed applicableAirplaneRange is a plain text, dash delimited
	range of airplanes identified by the type of airplane identifier
	given by the applicableAirplaneIdType property. Note that in some
	cases the range will only be for a single airplane (ex. ZA001-ZA001).
		
 -----------------------------
 Property: applicableEngine
	
	Gives a list of applicable engine names.
	
	Each listed applicableEngine is plain text value.	
		
 -----------------------------
 Property: applicablePart
	
	Gives a list of applicable part numbers.
	
	Each listed applicablePart is plain text value.

 -----------------------------
 Property: assignedSubject
	
	Gives a list of applicable assigned subject numbers.
	
	Each listed assignedSubject is plain text value.

 -----------------------------
 Property: customizedFor
	
	The Boeing customer code for whom the PdfTechPub was customized.
	
	Value type is a Boeing three character customer code.
			
 -----------------------------
 Property: exportControlStatement
	
	Gives a list of export control statements.
	
	Each listed exportControlStatement is plain text value.
	
 -----------------------------
 Property: fmsmCalibrationUnit
	
	Gives the measuring stick calibration unit of measure (Fuel Stick
	Measuring Manuals only).
	
	Value is one of 'Centimeters', 'Dimensionless', 'Inches', 'Kilograms',
	'Liters', 'Pounds'.
		
 -----------------------------
 Property: fmsmQuantityUnit
	
	Gives the fuel tank load unit of measure (Fuel Stick Measuring 
	Manuals only).
	
	Value is one of 'Imperial Gallons', 'Kilograms', 'Liters',
	'Pounds', 'U.S. Gallons', 'Gallons'.
				
 -----------------------------
 Property: identifier

	Gives the PdfTechPub number/identifier (a.k.a. "document number").
	
	Value type is plain text.
	
 -----------------------------	
 Property: issued

	Gives the date/time the PdfTechPub was issued.
	
	Value type is a date/time in ISO 8601 format: YYYY-MM-DDTHH:MM:SS
	
 -----------------------------		
 Property: issueLevel
	
	Gives the sequential issue level for the PdfTechPub revision.
	
	Value type is plain text.
	
 -----------------------------
 Property: modified
	
	Gives the last modified date of the PdfTechPub.
	
	Value type is a date/time in ISO 8601 format: YYYY-MM-DDTHH:MM:SS
	
 -----------------------------
 Property: MSGRevision
	
	Gives the Maintenance Steering Group (MSG) revision level.
	
	Value is one of 'MSG-1', 'MSG-2', 'MSG-3' (the MSG revision level)
	or 'non-MSG' (for manufacturer recommendation).

 -----------------------------
 Property: ptpVocabVersion
	
	Gives the current version of the PTP Vocabulary.
	
	Value type is a version number with format [major].[minor].
	Examples: 1.0, 3.4, etc.

 -----------------------------
 Property: rightsHolderName
	
	Gives the name of the organization managing rights for the 
	PdfTechPub.
	
	Value type is plain text.
	
 -----------------------------
 Property: rightsHolderCage
	
	Gives the Commercial And Government Entity (CAGE) code of the 
	organization managing rights for the PdfTechPub.
	
	Value type is a 5 character CAGE code defined by the US Defense 
	Logistics Agency.
		
 -----------------------------
 Property: rightsStatement
	
	Gives the statement about various property rights, including 
	intellectual property.
	
	Value type is plain text.

 -----------------------------
 Property: supplementLink
	
	Gives the link to the local C: drive where supplemental document 
	files may be stored.
	
	Value type is a valid Windows file path starting with
	"file:///C:/PDF".
			
 -----------------------------
 Property: title
	
	Gives the title of the PdfTechPub.
	
	Value type is plain text.
	
 -----------------------------
 Property: valid
	
	Gives a date range describing when the PdfTechPub is valid for use.
	
	Value type is ISO 8601 date interval in the following format:
	"YYYY-MM-DD/YYYY-MM-DD". The first date is the "from" date; the date 
	after the slash is the "to" date of the range.

 -----------------------------
 Property: volumeTitle
	
	Gives the title of the PdfTechPub if it is a Volume.
	
	Value type is plain text.
	
