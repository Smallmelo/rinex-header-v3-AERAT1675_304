
# Making Sense of the V3 RINEX Header Rows for PPP Submissions


The [Canadian Spatial Reference System Precise Point Positioning (CSRS-PPP) tool] (https://webapp.geod.nrcan.gc.ca/geod/tools-outils/ppp.php?locale=en) improves accuracy positions of raw GNSS data. During 2018, they modernized their tool to accept single frequency GPS data.  This means that anyone with the capability of pulling raw data from their receiver can improve their data’s accuracy.

One of the accepted file formats is the Receiver Independent Exchange Format [RINEX](ftp://igs.org/pub/data/format/rinex303.pdf) format. 

The full instructions for submissions are available on their website. They are really great instructions, but I wanted to document  some of road blocks I came across along the way with the RINEX header. I’ve only submitted preliminary data to CSRS-PPP, so I’ll be improving my documentation and notes as I get more experience with it. 

## Notes for Specific Header Rows

### “ANTENNA #/ TYPE"
The antenna name & dome characteristics must appear in columns 21-40 and must be 20 characters log in the "ANT # / TYPE row” row.  If there are no dome characteristics, be sure to “right indent” the phrase “NONE” within columns 21-40
Get your antenna name and dome characteristics from NGS (https://www.ngs.noaa.gov/ANTCAL/#).  If you aren’t sure what your antenna model is, reach out to the maker of your GPS receiver.
To be certain you are entering your antenna information correctly, Open your antenna’s ANTEX file from the NOAA Antenna database and copy/paste it into characters 21-40 of your header.

[Sample ANTEX](https://www.ngs.noaa.gov/ANTCAL/LoadFile?file=AERAT1675_304_NONE.atx) antenna file for the AT1675-304 made by Aero Antenna Technology for the Eos Arrow 100 GPS.

### “SYS / # / OBS TYPES” 
* Be sure that your header indicates single frequency
* G = GPS, R = GLONASS, C = BeiDou For more details, see figure 1 in the [RINEX specs](ftp://igs.org/pub/data/format/rinex303.pdf)
* Single frequency submissions should only include observation types from L1
* The “#” represented the number of observation types proceeding
* Single Frequency Settings Used for SYS / # / OBS TYPES (see tables 5-10 in the []RINEX specs](ftp://igs.org/pub/data/format/rinex303.pdf):
  * G   3 L1C C1C D1C
  * R    3 L1C C1C D1C
  * C    3 L2I C2I D2I


### "ANTENNA: DELTA H/E/N"
* The first value (H) is the height of your antenna above the marker


## General Notes:

* Make sure that there are no tabs in your header, only spaces.
* If the tool fails in static mode and it fails, it will run it in kinematic mode.
* Pay attention to the formatting requirements for v2 and v3 (ftp://igs.org/pub/data/format/rinex303.pdf)
* Unlike [OPUS](https://www.ngs.noaa.gov/OPUS/), there are no time restrictions for static submissions




## Submission Settings for [Precise Point Positioning](https://webapp.geod.nrcan.gc.ca/geod/tools-outils/ppp.php?locale=en) from the south western part of the United States
* STATIC
* ITRF
* CGVD2013

## Thanks

Thanks to the Geodetic Team at Natural Resources Canada Team and the Eos tech team for making themselves available to answer my many questions!