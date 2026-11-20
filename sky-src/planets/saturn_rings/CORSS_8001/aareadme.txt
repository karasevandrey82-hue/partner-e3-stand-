PDS_VERSION_ID                  = PDS3
LABEL_REVISION_NOTE             = "M.K. GORDON, 2018-11-30"
RECORD_TYPE                     = STREAM

DATA_SET_ID                     = "CO-SR-RSS-4/5-OCC-V2.0"

OBJECT                          = TEXT
  PUBLICATION_DATE              = 2018-11-30
  NOTE                          = "This data set contains derived 
radial occultation profiles of the rings of Saturn based on radio 
occultations made with the Cassini RSS instrument during the Cassini 
mission."
END_OBJECT                      = TEXT
END

                CASSINI RSS RING OCCULTATION ARCHIVE
                --------------------------------------
                

1. INTRODUCTION

  This data set contains derived radial occultation profiles of the 
  rings of Saturn based on radio occultations made with the Cassini 
  RSS instrument during the Cassini nominal mission. The 
  observations were obtained between June 2005 and early 
  September 2010.
   
  This is version 2 of the data set. Summary of changes
  
  Version 1 included observations through May 2008. Version 2 
  includes reprocessed versions of the material contained in 
  the earlier version, plus all subsequent RSS occultations 
  obtained prior to the loss of the Cassini UltraStable 
  Oscillator (USO) in late 2011.
  
  In addition, this version includes 'DLP' files for each observation
  which contain higher resolution calibrated but diffraction-limited 
  optical depth and phase shift profiles of Saturn's rings, that is, 
  calibrated profiles before reconstruction to remove diffraction 
  effects.

  Version 1 contained only X band data files. Version 2 contains 
  K, S, and X band data.
   
  Details of the data processing involved in the production of this 
  data set are provided in MAROUFETAL1986.

2. Volume format

  This volume has been formatted according to the ISO 9660 Level 2 
  Interchange Standard.  This format is compatible with a large 
  variety of computer systems (e.g.  Sun, DEC, Macintosh, PC).  For 
  further information, refer to the ISO 9660 Standard Document, RF# 
  ISO 9660-1988, 15 April 1988.

3. File formats

  Files on this volume are named according to PDS standards, where 
  the 1-3 characters after the period indicate the file type. The 
  file types used on this volume are:

ASCII text files:
    PDS labels                          *.LBL
    ASCII tables and indices            *.TAB
    PDS catalog files                   *.CAT
    Text documentation files            *.TXT

3.2 PDS LABELS

Essentially every file in this data set is described by an associated
PDS label. (See ERRATA.TXT for a list of any exceptions). Most files
are described by a detached label, which has the same name as the
corresponding file but an extension '.LBL'. Text files (*.TXT, *.CAT)
have attached labels. See the PDS Standards Reference (JPL D-7669) for
a complete description of the PDS label format. This document can be
obtained on line at:
        http://pds.jpl.nasa.gov/documents/

3.3 ASCII TEXT FILES

Different popular operating systems use different standards for how
ASCII text files are formatted. On Unix systems, lines are terminated
by a <LF> (linefeed character, control-J, ASCII 10). On Macintosh
computers, lines are terminated by a <CR> (carriage return character,
control-M, ASCII 13). On PCs, lines are terminated by a <CR><LF> pair.
PDS standards require all text files to use <CR><LF> line termination.
If the PDS label indicates INTERCHANGE_FORMAT = ASCII or RECORD_TYPE =
STREAM, then this line termination is in use.

On occasion, users on Unix and Macintosh computers may need to change
the line termination on some text files before they can use them. This
can be handled via text editors or a variety of utilities. For
example, the Unix tr (translate) command can be used to change
carriage returns to blanks: tr "\015" " " <oldfile.txt >newfile.txt

Some data files provided on this volume are ASCII tables. These
contain comma separated values in fixed width columns.  For each data
file, a detached PDS label is provided containing additional
parameters.

4. Volume contents

4.1 DATA SELECTION

Only reduced data are provided in this data set. The source raw RSS 
data may be obtained from the PDS.

The data files in the primary data directory, EASYDATA are the original
files submitted to the PDS by members of the RSS team. 

4.2 DIRECTORY & DATA FILE NAMING CONVENTIONS

DATA

Subdirectories = Revzzz

    Subdirectories = Revzzz_aaaa_yyyy_ddd_sss_b
 
 where         
        Revzzz = The Cassini orbit "Rev" designation
         aaaa = the instrument ID, RSS for this data set
     yyyy_ddd = date of the beginning of the observation
          sss = identifier for wave band and ground station antenna
            b = occultation direction: E (egress) or I( ingress)

Data File names = aaaa_yyyy_ddd_sss_b_ccc_nnKM.ttt

 where 
         aaaa = the instrument ID, RSS for this data set
     yyyy_ddd = date of the beginning of the observation
          sss = identifier for wave band and ground station antenna
            b = occultation direction: E (egress) or I( ingress)
          ccc = identifies the file contents: 
                CAL = calibration file
                DLP = calibrated but diffraction-limited optical 
                      depth and phase shift profiles
                GEO = supplemental geometry file
                TAU = calibrated optical depth and phase shift 
                      profiles reconstructed from the diffraction-limited 
                      diffraction-limited measurements.
         nnKM = the radial resolution of the bins used
                either 01KM or 10KM for this data set.
          ttt = TAB for the tabular data file
                LBL for the associated label file

Supplemental File names = 
    archive_summary_Revzzz_aaaa_yyyy_ddd_sss_b_Summary.ttt
    
where     zzz = the Orbit Rev ID
          all other place holders the same as above, except
          ttt = PDF for the supplemental information file
                LBL for the associated label file
                
4.3 DIRECTORY STRUCTURE

This Volume is organized in a directory tree as follows:

root directory
|
|-aareadme.txt          This file.
|
|-errata.txt            A file that reports any known errors and
|                       describes any known deviations from PDS
|                       standards.
|
|-voldesc.cat           A PDS volume object, providing a high-level
|                       description of the volume and its contents.
|
|-data/                 Directory containing ring occultation profiles 
|                       in ASCII table files.
|
| |- revxx              A directory containing the data and support files
| |                     for a single occultation experiment
| |        
| | |-x .tab            A ring radial profile from a single occultation,
| | |                   ingress and egress portions are given in 
| | |                   separate files.
| | |                   
| | |-x .lbl            Detached PDS labels for the above.
|                       
| | |-y .pdf            A file containing documentation for the 
| | |                   associated observations. 
| | |                   
| | |-y .lbl            Detached PDS labels for the above.
|                       
|-datainfo.txt          Description of the files in this directory
|                       tree.
|
|-catalog/              A directory containing PDS catalog
| |                     information, providing high-level descriptions
| |                     of the data, instruments, etc.
| |
| |-catinfo.txt         Description of the files in this directory.
| |
| |-dataset.cat         PDS catalog file describing this data set, 
| |                     including a brief summary of the data and 
| |                     and the processing involved.
| |
| |-inst.cat            Catalog file describing Cassini Radio Science 
| |                     Subsystem.
| |
| |-insthost.cat        Catalog file describing the Cassini Orbiter.
| |
| |-mission.cat         Catalog file describing the Cassini-Huygens 
| |                     mission.
| |
| |-person.cat          Catalog file describing the personnel involved
| |                     in acquiring and archiving this data set.
| |
| |-ref.cat             Catalog file containing bibliographic
| |                     references relevant to this dataset.
| |                     
| |-ref.cat             Catalog file containing bibliographic
| |                     references relevant to the entire mission.
|
|-document/             A directory containing supplemental 
| |                     documentation.
| |                     
| |                     
| |-docinfo.txt         Description of the files in this directory.
| |
|
|-index/                A directory containing indices of the files in
| |                     this data set.
| |
| |-indxinfo.txt        Description of the files in this directory.
| |
| |-index.tab           A table of all the data files on this volume.
| |
| |-index.lbl           A detached PDS label for the above, defining
|                       each column in the table.
 

================================================================= 
PEER REVIEW 

This volume has completed a PDS peer review and all peer review 
liens have been addressed.
 
=================================================================   
          
5.  CITING THIS DATA SET

The following is the recommended information to include in a journal
citation of this data set:

"Marouf, E., CASSINI ORBITER SATURN RSS RING RADIO OCCULTATIONS 2.0,
 CO-SR-RSS-4/5-OCC-V2.0, NASA Planetary Data System, 2018."

6.  CONTACT INFORMATION

For questions concerning this data set contact:                                                    
                                                                              
Mitch Gordon
PDS Rings Node
SETI Institute 
189 Bernardo
Mountain View, CA 94043                           
Phone: 276-393-8822                                                           
Email: mgordon@seti.org                                                        
                                                                              
Prof. Essam Marouf,
Electrical Engineering Department,
San Jose State University,
San Jose, CA 95192-0084;
Phone: 408-924-3969;
Email: essam.marouf@sjsu.edu.
 