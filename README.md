# HL7 FHIR to schema.org conversion tool
A tool to convert [HL7 FHIR](http://www.hl7.org/FHIR/) [StructuredDefinition](http://www.hl7.org/FHIR/structuredefinition.html) to 
the [schema.org](http://schema.org/) [data model](http://schema.org/docs/datamodel.html)

See: https://github.com/crDDI/docs/wiki/FHIRToSDO for implementation details


## Requirements
* python3 (ideally >= 3.5, but any 3.x version will do).  You can determine whether you have python on your machine and its version by:
  * `python -v` -- if 3.x you are ready to go, otherwise...
  * `python3 -v` -- if this works you are also ready to go
* virtualenv -- if this isn't on your machine, see <http://pythoncentral.io/how-to-install-virtualenv-python/>
* java -- we need version 1.7 or greater


## Installation
Set up a python3 virtual environment:

```bash
> virtualenv fhirtosdo -p python3
> . fhirtosdo/bin/activate
(fhirtosdo) > pip install fhir-to-sdo
```

## Downloading the FHIR specification
To download the latest copy of the FHIR spec and unzip it:

```bash
(fhirtosdo) > download_fhir_spec  --striptext
```

Note that the above function can take considerable time, as the zipped image of the fhir spec is quite large.  Note that the "-u" option can be used to download different fhir builds as needed

## Run the fhirtosdo transformation
```bash
(fhirtosdo) > fhirtosdo -id data/site -o fhir_core.rdfa --loglevel INFO 
```

Note that the above transformation may generate a numbe of error messages of the form
 "ValueSet access error: http://hl7.org/fhir/ValueSet/measure-population (Not Found)".  This is because not all of the
 value sets referenced in the FHIR structure definitions are currently available on the official fhir website.
 
 The output (fhir_core.rdfa) can then be transferred to the [schema.org](https://github.com/schemaorg/schemaorg) environment.

