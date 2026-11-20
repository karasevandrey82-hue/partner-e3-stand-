OPAL Jupiter Maps README file

Cycle 32 Jupiter data were acquired with WFC3/UVIS between December 11, 2025 07:24UT and December 12, 2025 02:54UT.

Images were navigated using an ellipsoid limb fitting technique with equatorial and polar radii of 71492 and 66854 km, respectively.  The FQ889N data were fringe corrected post-pipeline, resulting in an ~2% correction. Each map was generated at the sub-earth longitude at 10 pixels/deg resolution, between 0 and +90 deg planetographic latitude.  Maps were mosaicked to cover 360 deg of longitude (left edge = 0 System III W. longitude, decreasing to the right) and seams between maps were interpolated to smooth, where needed.  The table below lists the Minnaert correction (ratio of cosines of incidence and emission angles to the k power) applied to remove limb darkening for each map.  The mosaics are available in TIF (arbitrarily scaled) and FITS.  The FITS values can be converted to I/F by multiplying by the values in the table below.

Map Artifacts: The FQ889N retains slight residual fringes after post-processing. The first visit did not include the F343N filter, but with 13 visits, 2 rotations of Jupiter were still available in all filters; the maps are shifted by one Hubble orbit for that filter, see times below.  

Rotation 1 F343N (Dec. 11 09:19:58 to Dec. 11 17:10:43)
Rotation 1 other filters (Dec. 11 07:24:09 to Dec. 11 15:40:10)
Rotation 2 F343N (Dec. 11 18:44:52 to Dec. 12 02:35:36)
Rotation 2 other filters (Dec. 11 16:49:03 to Dec. 12 01:05:03)

Filter	Minnaert k	I/F scale factor (FITS files)
FQ889N	1.000		.00088
F658N	0.999		.00460
F631N	0.999		.00383
F502N	0.950		.00386
F467M 	0.950		.00376
F395N	0.850		.00365
F343N	0.850		.00235 
F275W	0.520		.00256
