tv-subtitle-extraction
======================
## Documentation
SubtitleProject is made by the State and University Library in Aarhus, Denmark. The purpose of the project
was to extract subtitles from the library's videofiles (transportStreams, mpeg and wmv). 
SubtitleProject can extract from teletext, dvb_subtitles and hardcoded subs in picture using tesseract-ocr. 
The ocr-result is based on the video quality.

SubtitleProject was written to process danish input, but with the dictionary file and the tesseract language
file, it should be easy to change language.

## Dependendies on Ubuntu

### Tesseract, tested with version: 3.02.01 (website: https://code.google.com/p/tesseract-ocr/downloads/list)

### ImageMagick, tested with version: 6.7.7-10 2013-09-10 Q16 (website: http://www.imagemagick.org/script/install-source.php#unix)

### ProjectX, tested with version: 0.90.4.00/30.03.2006 (website: http://sourceforge.net/projects/project-x/)

### ccExtractor, tested with version: 0.68 (website: http://ccextractor.sourceforge.net/download-ccextractor.html)

### ffmpeg and ffprobe, tested with version: N-60937-gb5005de (website: http://ffmpeg.org/download.html)

## Ubuntu guide

### Tesseract
1. Terminal: sudo apt-get install tesseract-ocr
2. copy dan.traineddata from SubtitleProject/install/Tesseract to /usr/share/tesseract-ocr/tessdata (Owner permissions needed)

### ImageMagick
1. Terminal: sudo apt-get install imagemagick

### ProjectX
1. Terminal sudo apt-get install projectx

### ccExtractor
1. run build from install/ccextractor.0.68/linux/ (Download any dependendies it requires) 
2. write new binary filepath in properties file or use SubtitleProjectArguments

### ffmpeg and ffprobe
1. The package directory which Ubuntu has available is depricated and a newer version is required for SubtitleProject to work. 
   A static version can be Downloaded at http://www.ffmpeg.org/download.html. Insert the generated files in SubtitleProject/var/.

### args
-i: videofile (Must be defined either in args or properties file)

-o: outputdestination (default: /output)

-p: properties-file. (default: /var/SubtitleProject.properties) 

### Properties
	
-ccextractorPath: 	Path to binary file (Must be defined)

-ffprobePath: 		Path to binary file (Must be defined)

-ffmpegPath: 		Path to binary file (Must be defined)

-tesseract:		Path to binary file (Must be defined)

-tesseractConfigPath: 	Config-file used by Tesseract (default: conf/Tesseractconfigfile.txt)

-inputFile: 		This path will be used if the argument -i wasn't used (Must be defined either in args or properties file)

-outPutDirectory: 	This path will be used if the argument -o wasn't used (default: output)

-projectXPath: 		Path to binary file (Must be defined)

-projectXIniPath: 	This file is used by projectX to handle dvb_sutitle streams, you must change the output folder to the outputdestination
                  		which you use. (default filelocation: conf/X.ini)

-convertPath:		Path to binary file, (lib used by ImageMagick) (Must be defined)

-dict: 			path for dictionary txt. When OCR is used, 50% of the analysed text must be in the dictionary file,
	  			otherwise the result is assumed to be noise and is deleted. The dictionary must be in ascending order based
	   			on Ascii values. (default danish: conf/dictv2.txt)

-teleTextIndexPathIndex: xml-file with Teletextindexes to subtitlepages. (default danish: conf/TeletextIndexes.xml)

-terminationTime: 	Hours to run before program will terminate by force (default 1000)