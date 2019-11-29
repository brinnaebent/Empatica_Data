# Empatica_Data

## This is a Guide to Working with Empatica (E4) data for longitudinal studies.

Data from Empatica is downloaded as zipped files with individual .csv files for each sensor during that recording period. The recording periods can vary in length from seconds to days. This is a quick and easy way to get Empatica files into a readable format using Bash (Terminal for Mac). These instructions are such that you can keep the data as individual sensor types (important if you are doing a study and using only 1-2 sensors).



### Bash

Instructions:

Change directory to raw data (from Empatica these are zipped files from each recording period)

Unzip all zipped folders in directory

$ find -name '.zip' -exec sh -c 'unzip -d "${1%.}" "$1"' _ {} ;

Conglomerate all files from a sensor into one file:

$ find . -name TEMP.csv -exec paste -d , >TEMP.csv {} +

$ find . -name HR.csv -exec paste -d , >HR.csv {} +

$ find . -name IBI.csv -exec paste -d , >IBI.csv {} +

$ find . -name BVP.csv -exec paste -d , >BVP.csv {} +

$ find . -name EDA.csv -exec paste -d , >EDA.csv {} +

$ find . -name ACC.csv -exec paste -d , >ACC.csv {} +


### R

E4_Pipeline_Transform_Data.rmd - R file for taking bash conglomerated files and turning them into tidy, readable .csv files with correct date/timestamps.


### Coming soon

EDA in R and in Python

