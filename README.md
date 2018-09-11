# PlantMovement

README file accompanying supplemental files to "Quantifying crop Movement outdoors through Hemispherical Video Analysis of Agricultural Plots"
By Alexander Susko

The progression recommended here mirrors the one outlined in the paper's methods section.

1) fieldmap_readme.xls contains the field layout at panel 5 in planting date 2 (the sample video provided)
2) The plotfinder script and associated files are in the plotfinder directory.   
3) Open plotfinder_published.m in MATLAB and set the current folder to "plotfinder".  plotfinder_published.m will require the following files in the current directory to execute:

	frame1.tiff;
	redmask.m (red square masking function);
	cropFunGenerator.m (function to generate other cropping functions);
	fieldCoordinates1.csv;
	fieldCoordinates3.csv;
	fieldCoordinates5.csv;
	fieldCoordinates7.csv;
	fieldPlotnames1.txt;
	fieldPlotnames3.txt;
	fieldPlotnames5.txt;
	fieldPlotnames7.txt
	
4) I've provided the cropped images (square foot regions) and their cropping functions the "croppedimages" and "croppingfunctions" subdirectories from a previous execution.  If you re execute plotfinder_published.m, the images and cropping functions will be outputted to the "plotfinder" directory.  
5) Execute FLY07_12_17_p2.m in the "plotfinder" directory to analyze the color changes over the demarcated plot regions of the 360 video. This script will output the normalized color waveforms in .txt file named FLY07_12_17_p2.txt. This file has been provided in the "plotfinder" directory from a previous execution.  FLY07_12_17_p2.m will require the following files in the current directory to execute:

	FLY07_12_17_p2.mp4 (University of Minnesota DRUM link);
	red.m
	
6) Navigate to the "MovementSignalProcessing" directory to process the normalized waveforms from each plot.  The outputted FLY07_12_17_p2.txt from step 5 is provided along with four other .txt files containing the normalized waveforms at panel 5 for the four other video dates examined in the paper.  Execute bandpassParse_p2.m in Matlab, which will output a subdirectory of plot-specific.txt files for each .txt file of normalized waveforms that is inputted. bandpassParse_p2.m requires the following files to execute:

	FLY07_10_17_p2.txt;
	FLY07_11_17_p2.txt;
	FLY07_12_17_p2.txt;
	FLY07_13_17_p2.txt;
	FLY07_17_17_p2.txt;
	
7) Open R and execute stationary_organization_published.r.  This R script is meant to concatenate the mean frequency, amplitude, and plot data from multiple panels, which are not provided in this demo.  We have provided the output data for all panels examined in this paper (stationaryfinal.txt). This script will require that the following subdirectories (created by bandpassParse_p2.m) are present in the working directory "MovementSignalProcessing"

	FLY07_10_17_p2;
	FLY07_11_17_p2;
	FLY07_12_17_p2;
	FLY07_13_17_p2;
	FLY07_17_17_p2;
	
8) Execute stationary_analysis_published.r.  This R script will analyze the output from stationary_organization_published.r, and contains the R code used in the statistical analysis of plant movement presented in the paper. This script will require the following file to execute:

	stationaryfinal.txt
