# Planet maps for the MATRIKA telescope — sources

Checked 2026-11-20. Two files are in this folder now; the rest are listed under "Waiting for download" with their exact primary-source addresses and terms.

## How these two files got here

The session that made this commit cannot reach NASA servers (its proxy refuses them). Both files were copied from a GitHub repository that downloaded them from NASA and recorded the NASA URL and SHA-256 at download time:
- Repository: https://github.com/xiaoqiuyi0/obsidian-travel-globe, commit `9df1ffc1495136bf04ef292613ea9088ec12187a`, folder `assets/upstream/`
- Record: `assets/realistic/provenance.json` in the same commit (fields `url`, `sha256`, `width`, `height`)

The SHA-256 of each copied file equals the SHA-256 recorded there. For the cloud map the same SHA-256 is also recorded independently in https://github.com/ReeceHumphreys/globes (commit `6517916d3f945806664e6b59f374d3f6ac9f3881`, `examples/viewer/public/data/earth/clouds/README.md`), taken from the Internet Archive copy of the NASA file. The hashes were **not** checked against the NASA server itself.

No resizing, recompression, colour change, crop or longitude shift was applied.

---

## 1. Earth — Blue Marble: Next Generation, July 2004, with topography

- File: `world.topo.200407.3x21600x10800.jpg` — original NASA file name
- Size: 21796912 bytes
- sha256: `40a42c4511ccfbcdc6928d026a50da190e718772c7e6141ebd4ee9dbe946eda8`
- Pixels: 21600×10800, 8-bit RGB JPEG
- Projection: equirectangular (simple cylindrical). The record says: "Equirectangular; left -180°, right +180°, top +90°, bottom -90°. No crop, flip, longitude shift or recoloring."
- NASA file URL: https://assets.science.nasa.gov/content/dam/science/esd/eo/images/bmng/bmng-topography/july/world.topo.200407.3x21600x10800.jpg
- NASA pages:
  - https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/
  - https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/base-topography/
- Credit, verbatim from the BMNG page: "produced by Reto Stöckli, NASA Earth Observatory (NASA Goddard Space Flight Center)"
- Terms, verbatim from https://earthobservatory.nasa.gov/ImageUse:
  - "freely available for re-publication or re-use, including commercial purposes, except for where copyright is indicated"
  - "the only mandatory credit is NASA"
  - "We ask that NASA's Earth Observatory be given credit for its original materials"
- Month: July was chosen over June because the scene's moment is 2027-07-28.
- Note: this "topography" variant has terrain shading painted into the image; the "base map" variant (no shading) is listed below as waiting.

## 2. Earth — Blue Marble (2002) cloud composite

- File: `cloud_combined_8192.tif` — original NASA file name
- Size: 35870468 bytes
- sha256: `d137775d8966ab8d443fd5126dc6e7ad72072bc1ed50555c5818d221735daf0f`
- Pixels: 8192×4096, 8-bit RGB TIFF, LZW
- Projection: equirectangular, north up, longitude −180° at the left edge (from the ReeceHumphreys README: "equirectangular, north-up, longitude −180° at the left")
- NASA file URL (record): https://eoimages.gsfc.nasa.gov/images/imagerecords/57000/57747/cloud_combined_8192.tif — Visible Earth image 57747
- NASA page: https://science.nasa.gov/earth/earth-observatory/the-blue-marble-true-color-global-imagery-at-1km-resolution/ (published May 26, 2002; last updated Dec 18, 2025)
- How it was made, verbatim: "a composite of two days of imagery collected in visible light wavelengths"; per the page "The Blue Marble" (2002), there is also "a third day of thermal infra-red imagery over the poles". This is not one day's weather.
- Credit, verbatim from that page:
  - "NASA Goddard Space Flight Center"
  - "Image by Reto Stöckli (land surface, shallow water, clouds)."
  - "Enhancements by Robert Simmon (ocean color, compositing, 3D globes, animation)."
- Terms, verbatim from that page: "These images are freely available to educators, scientists, museums, and the public." Plus the Earth Observatory image use policy quoted in section 1.

---

## Waiting for download (needs a session that can reach the primary sites)

For every file: record the download date, the exact URL, the size in bytes, and the sha256 of the original.

Resizing rules:
- **Never upscale.** A map narrower than 16384 keeps its own size.
- Files over 100 MB: first try JPEG quality 95 at native size.
- Only if that is still over 100 MB, either cut into tiles (keeps full detail) or downscale to 16384×8192 with Lanczos. Record the sha256 of both the original and the output.
- Use GDAL for the 4 GB and 12 GB files: `gdal_translate -outsize 16384 8192 -r lanczos …`.

| Body | Product | File URL | Size (page) | Pixels | Projection / longitude | Credit (verbatim) | Terms (verbatim) |
|---|---|---|---|---|---|---|---|
| Earth | BMNG July 2004, base map (no shading) | `…/bmng/bmng-base/july/world.200407.3x21600x10800.jpg` (prefix as in section 1; path seen in a third-party README, page not opened) | — | 21600×10800 | equirectangular −180…180 | as section 1 | as section 1 |
| Earth | BMNG July 2004, 500 m tiles A1…D2 | `…/bmng-topography/july/world.topo.200407.3x21600x21600.{A1…D2}.jpg` (pattern from the June page) | — | 8 × 21600×21600 | equirectangular | as section 1 | as section 1 |
| Mercury | MESSENGER MDIS Global Basemap BDR 166m | https://planetarymaps.usgs.gov/mosaic/Mercury_MESSENGER_MDIS_Basemap_BDR_Mosaic_Global_166m.tif | 4 GB | 92160×46080 | Simple Cylindrical, −180…180, Positive East | Publisher "USGS Astrogeology Science Center" | "Access Constraints: None", "Use Constraints: Please cite authors" |
| Mercury | MDIS Enhanced Color 665m | https://planetarymaps.usgs.gov/mosaic/Mercury_MESSENGER_MDIS_Basemap_EnhancedColor_Mosaic_Global_665m.tif | 759 MB | 23040×11520 | Simple Cylindrical, −180…180, Positive East | Primary Authors "Applied Coherent Technology Corporation"; Originators "NASA, Johns Hopkins Applied Physics Laboratory, Arizona State University, Carnegie Science" | "Access Constraints: None", "Use Constraints: Please cite authors". Colour is not visual (USGS: "This is not what Mercury would look like to the human eye.") |
| Mercury | MDIS MD3 Color 665m | https://planetarymaps.usgs.gov/mosaic//Mercury_MESSENGER_MDIS_Basemap_MD3Color_Mosaic_Global_665m.tif | 760 MB | 23040×11520 | Simple Cylindrical, −180…180, Positive East | as Enhanced Color | as Enhanced Color. R/G/B = 1000/750/430 nm, not natural colour |
| Venus | Magellan C3-MDIR Mosaic 2025m (radar, grey) | https://planetarymaps.usgs.gov/mosaic/Venus_Magellan_C3-MDIR_Global_Mosaic_2025m.tif | 170 MB | 18775×9388 | Equirectangular, −180…180 | Originators "PDS Geosciences Node" | "Access Constraints: public domain", "Use Constraints: None" |
| Venus | C3-MDIR Synthetic Color 4641m | https://planetarymaps.usgs.gov/mosaic/Venus_Magellan_C3-MDIR_Colorized_Global_Mosaic_4641m.tif | 96 MB | 8192×4096 | Equirectangular, −180…180, positive east | as above | as above. "developed to simulate the surface of Venus" — the colour is synthetic |
| Mars | Viking MDIM 2.1 Colorized 232m | https://planetarymaps.usgs.gov/mosaic/Mars_Viking_MDIM21_ClrMosaic_global_232m.tif | 12 GB | 92160×46080 | Simple Cylindrical, −180…180, Positive East | Originators "NASA AMES"; Primary Authors "USGS Astrogeology Science Center" | "Access Constraints: Public domain", "Use Constraints: None" |
| Jupiter | OPAL (Hubble), colour globalmap TIF, cycle 32 | pattern: `https://archive.stsci.edu/missions/hlsp/opal/cycle32/jupiter/hlsp_opal_hst_wfc3-uvis_jupiter-2025a_f395n-f502n-f631n_v1_globalmap.tif` (not opened) | — | — | west longitude, planetographic latitude | acknowledgement text on https://archive.stsci.edu/hlsp/opal; DOI 10.17909/T9G593 | "These HLSP data products are licensed for use under CC BY 4.0." |
| Jupiter | PIA07782 (Cassini, Dec 2000) | https://assets.science.nasa.gov/content/dam/science/psd/photojournal/pia/pia07/pia07782/PIA07782.tif | 18.56 MB | — | rectangular, planetocentric | "Credits: NASA/JPL/Space Science Institute" | NASA: "generally are not subject to copyright in the United States"; "must not explicitly or implicitly convey NASA's endorsement of commercial goods or services" |
| Saturn | Cassini ISS Global Maps (PDS) | https://atmos.nmsu.edu/PDS/data/PDS4/co_iss_global-maps.tar.gz | — | RGB 3601×1801×3 float | Equirectangular, centre 180°, Positive West | "Li, Liming, Robert West, Xun Jiang, and Benjamin Knowles (2023)", DOI 10.17189/rkkb-6y30 | PDS: "Data sets archived in the PDS are in the public domain." |
| Saturn | OPAL 2025, colour globalmap TIF | https://archive.stsci.edu/missions/hlsp/opal/cycle32/saturn/hlsp_opal_hst_wfc3-uvis_saturn-2025a_f395n-f502n-f631n_v1_globalmap.tif | — | — | as OPAL | as OPAL | CC BY 4.0 |
| Saturn rings | Cassini RSS CORSS_8001 | https://pds-rings.seti.org/holdings/archives-volumes/CORSS_8xxx/CORSS_8001.tar.gz | — | profiles | — | PDS Ring-Moon Systems Node | PDS public domain |
| Uranus | OPAL 2024, colour globalmap TIF | https://archive.stsci.edu/missions/hlsp/opal/cycle32/uranus/hlsp_opal_hst_wfc3-uvis_uranus-2024a_f657n-f547m-f467m_v1_globalmap.tif | — | — | as OPAL | as OPAL | CC BY 4.0 |
| Neptune | OPAL, latest cycle | see https://archive.stsci.edu/hlsp/opal | — | — | as OPAL | as OPAL | CC BY 4.0 |
| Io | Galileo SSI / Voyager Color Merged 1km | https://planetarymaps.usgs.gov/mosaic/Io_GalileoSSI-Voyager_Global_Mosaic_ClrMerge_1km.tif | 189 MB | 11445×5723 | Simple Cylindrical, −180…180, Positive West | Originators "Planetary Data System" | "public domain", "None" |
| Europa | Voyager–Galileo SSI Global Mosaic 500m (grey) | https://planetarymaps.usgs.gov/mosaic/Europa_Voyager_GalileoSSI_global_mosaic_500m.tif | 184 MB | 19631×9816 | Simple Cylindrical, 0…360, Positive West | Primary Authors "Tammy Becker" | "None", "None" |
| Ganymede | PIA17901 global image mosaic | https://photojournal.jpl.nasa.gov/tiff/PIA17901.tif | — | — | centred 200° W | "USGS Astrogeology Science Center/Wheaton/NASA/JPL-Caltech" | JPL: "may be used for any purpose without prior permission" (unless otherwise noted) |
| Callisto | Galileo/Voyager Global Mosaic 1km (grey) | https://planetarymaps.usgs.gov/mosaic/Callisto_Voyager_GalileoSSI_global_mosaic_1km.tif | 110 MB | 15138×7569 | Simple Cylindrical, 0…360, Positive West | "USGS Astrogeology Science Center" | "public domain", "None" |
| Titan | Cassini ISS Global Mosaic 4005m (938 nm) | https://planetarymaps.usgs.gov/mosaic/Titan_ISS_P19658_Mosaic_Global_4km.tif | 7.8 MB | 4040×2020 | Equirectangular, 0…360, Positive West | Originators "NASA/JPL-Caltech/SSI"; Primary Authors "Cassini ISS Team" | "None", "Please cite authors" |

### Not to be added
- USGS "Ganymede Voyager / Galileo Simple Cylindrical" (`gany_simp_2km.jpg`): the page states no terms.
- Akatsuki (JAXA) Venus UVI maps: CC BY 4.0, but JAXA is not on the list of allowed primary sources; the maps are ultraviolet and each one covers only one hemisphere.

### Not found
- A global visible-light cloud map of Venus.
- Voyager 2 global maps of Uranus or Neptune on NASA Photojournal.
- Colour global mosaics of Europa and Callisto at USGS.
