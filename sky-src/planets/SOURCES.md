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

> **Update 2026-11-20, second commit (session with full network):** most files from "Waiting for download" are now downloaded directly from the primary addresses and are in this folder. See the section **«Загрузка 20.11 по заданию v2»** at the end of this file (exact URL, time, bytes, sha256 of original and output, pixels, projection). Ganymede PIA17901 did not open. Both Earth variants are kept: July topo (above, first commit) and June base 16k (task v2).

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

---

# Загрузка 20.11 по заданию v2

Скачано 20.11.2026 (UTC) по заданию «скачать карты планет v2». Только адреса из задания; замены на других сайтах не искались.
Уменьшение — только GDAL 3.8.4: `gdal_translate -outsize W H -r lanczos -of JPEG -co QUALITY=95`. Проекция и долгота не менялись.
Оригиналы больше 100 МБ в репозиторий не положены (только их sha256 ниже).

Примечание о сети: адреса `planetarymaps.usgs.gov/mosaic/…` отвечают 302 на хранилище самого USGS `asc-pds-services.s3.us-west-2.amazonaws.com/mosaic/…`; файл берётся оттуда.
Меркурий, Марс и архив колец рвались по ходу загрузки и докачаны с того же адреса с места обрыва (`curl -C -`); итоговый размер совпал с Content-Length.

## Таблица

| № | Тело | Файл в репозитории | Пиксели | Байты | sha256 файла в репозитории |
|---|---|---|---|---|---|
| 1 | Меркурий (серая) | mercury_bdr_16k.jpg | 16384×8192 | 61 136 835 | 92dcd1b605e586171625c1df744fe93da53e2aa9323ed6672e422bef3ba3c9f4 |
| 2 | Венера, радар, цвет условный | venus_magellan_8k.jpg | 8192×4096 | 15 262 271 | 193462b81fa1860a64ebb389ec6d9b14f631afb9cc9788a61907cec53c0b2ef9 |
| 3 | Марс | mars_mdim21_16k.jpg | 16384×8192 | 51 728 346 | 4fb07a18eb4b886edd2577a00cbd8f4858161d22c27491c0ab5c3e7329a27692 |
| 4 | Юпитер, OPAL 2025b | jupiter_opal.tif | 3600×1800 | 19 444 834 | ca9f089c64cf79c65cebfa592db1c2d8b8614b5e2470d397c94029ceab7b7815 |
| 4 | — README цикла 32 | jupiter_opal_README.txt | — | 1 733 | 344f5c1bcae360edfc7b4f1183b9ed47f887cbbe7fa0518fdf577c915784fdad |
| 5 | Юпитер, запасной PIA07782 | jupiter_pia07782.tif | 3601×1801 | 19 456 427 | f92ffc7a2fa0235c47ec8f1f168dd36bffeb6acc318292b237878a00a48cf7d9 |
| 6 | Сатурн, OPAL 2025a | saturn_opal_2025a.tif | 1800×900 | 4 885 052 | c34a13a8253a39bcc1f8376b24c077b89f05ce0b5202706f535ded20314440d7 |
| 6 | — README | saturn_opal_2025a_README.txt | — | 1 625 | 31059e9f106905f1ca34c924e005c3094e7c33e94d19a1f5178fcb7f186ca3ca |
| 7 | Сатурн, Cassini RGB | saturn_cassini_rgb.fits | 3601×1801×3, float32 | 77 829 120 | 32a62eca9b82255c7dd763ba0752cee1664ae73d5ec4d5d5260227deecd422af |
| 7 | — метка PDS4 | saturn_cassini_rgb.xml | — | 10 595 | 0d1ab898d6811622688363c1fbe6ef4bd15541c8009a43ea5df6581f8e386a66 |
| 8 | Кольца Сатурна | saturn_rings/ | — | — | см. раздел 8 |
| 9 | Уран, OPAL 2024a | uranus_opal_2024a.tif | 721×361 | 787 762 | 838dbf45072d4354425389d7c5869312185fd8df3d0d5ee526661b22db4c3c12 |
| 9 | — README | uranus_opal_2024a_README.txt | — | 1 504 | 5f71cce6994ad0ea1f4c38034a6e722381618d0b5fb88ccc74ab77f551efbde5 |
| 10 | Нептун, OPAL 2026b | neptune_opal.tif | 721×361 | 789 926 | 456bcf124957cb1f033654e746a9046e80c33840c49e05b25c11216c317b1473 |
| 10 | — README цикла 33 | neptune_opal_README.txt | — | 1 532 | f97b4f9f57c8363419c7f59076ad6050341a2fdb21241420dbd3b9b495dd6101 |
| 11 | Земля, июнь (базовая, без рельефа) | earth_bmng_june_16k.jpg | 16384×8192 | 18 469 701 | a6bb8caea51a2e39f98630476e2c9c086cb25966f566f43fd001ef6ceb9d428c |
| 12 | Ио, цветная | io_8k.jpg | 8192×4096 | 5 643 729 | fa26d8bfe8358e1346b9e1f6dbab3889221907a2a39808bce8f07e84e1eb3afc |
| 13 | Европа, серая | europa_8k.jpg | 8192×4096 | 8 486 388 | d4e1a36cf15cc8c83ea178fc8a637f1c1d22ace36678926f533a8c120309570b |
| 14 | Ганимед | — | — | — | **не открылся** |
| 15 | Каллисто, серая | callisto_8k.jpg | 8192×4096 | 8 119 955 | 412e3b16b301508fee19f5b25388b36a22a4e97a383a2aca48993e17f8ba93d9 |
| 16 | Титан, серая | titan_4k.tif | 4040×2020 | 8 169 529 | ca0fe5f6f9bdba1b6d03245969a42336a010ddc17d636e5e06fffa939d10ca83 |

## Оригиналы (адрес, время загрузки UTC, байты, sha256, пиксели, проекция как есть)

**1. Меркурий** — https://planetarymaps.usgs.gov/mosaic/Mercury_MESSENGER_MDIS_Basemap_BDR_Mosaic_Global_166m.tif
2026-11-20T08:41:38Z · 4 247 470 901 байт · sha256 d4c0880c39d062994a6f02c0462ec6c87f60fdcc504546915e076e2cd472b1da
92160×46080, 1 канал Byte (серый). SimpleCylindrical Mercury_2015, центральный меридиан 0; левый край 180° з. д., правый 180° в. д. Пиксель 166,31 м. В репозиторий не положен (>100 МБ).

**2. Венера** — https://planetarymaps.usgs.gov/mosaic/Venus_Magellan_C3-MDIR_Colorized_Global_Mosaic_4641m.tif
2026-11-20T08:19:19Z · 100 762 261 байт · sha256 6bfcd1ccaa79bad8b6d6943a86b6c77b65c7cf48a6ecbf900e429e334f584f43
8192×4096, RGB Byte. Equirectangular Venus, центральный меридиан 0; от 180° з. д. до 180° в. д. Пиксель 4641 м. Размер не менялся, только перекодирован в JPEG 95. Цвет условный (раскраска радара). Оригинал не положен (>100 МБ).

**3. Марс** — https://planetarymaps.usgs.gov/mosaic/Mars_Viking_MDIM21_ClrMosaic_global_232m.tif
2026-11-20T08:41:34Z · 12 742 411 029 байт · sha256 554f1170998b4cd00359defa48600307e52c49f921c282d842361ad45082aa31
92160×46080, RGB Byte. SimpleCylindrical Mars, центральный меридиан 0; от 180° з. д. до 180° в. д. Пиксель 231,54 м. Оригинал не положен.

**4. Юпитер, OPAL.** Страница https://archive.stsci.edu/hlsp/opal → последний цикл Юпитера на странице — Cycle 32 (https://archive.stsci.edu/hlsp/opal/opal-jupiter-cycle-32). В цикле две цветные карты, 2025a и 2025b; взята более поздняя, 2025b.
Файл: https://archive.stsci.edu/missions/hlsp/opal/cycle32/jupiter/hlsp_opal_hst_wfc3-uvis_jupiter-2025b_f395n-f502n-f631n_v1_globalmap.tif
2026-11-20T08:19:20Z · 19 444 834 байт · sha256 ca9f089c… (как в таблице, файл положен без изменений). 3600×1800 RGB, без геопривязки в TIFF.
README: https://archive.stsci.edu/missions/hlsp/opal/cycle32/jupiter/hlsp_opal_hst_wfc3-uvis_jupiter-2025_all_v1_readme.txt (2026-11-20T08:19:20Z).
По README: съёмка 11–12 декабря 2025, 10 пикс./градус; левый край = 0° System III з. д., долгота убывает вправо; планетографическая широта; цвет F631N/F502N/F395N, TIF «arbitrarily scaled».

**5. Юпитер, запасной** — https://assets.science.nasa.gov/content/dam/science/psd/photojournal/pia/pia07/pia07782/PIA07782.tif
2026-11-20T08:19:21Z · 19 456 427 байт · sha256 f92ffc7a… · 3601×1801 RGB, без геопривязки. Положен как есть.

**6. Сатурн, OPAL 2025a** — https://archive.stsci.edu/missions/hlsp/opal/cycle32/saturn/hlsp_opal_hst_wfc3-uvis_saturn-2025a_f395n-f502n-f631n_v1_globalmap.tif
2026-11-20T08:19:21Z · 4 885 052 байт · sha256 c34a13a8… · 1800×900 RGB. Как есть.
README: https://archive.stsci.edu/missions/hlsp/opal/cycle32/saturn/hlsp_opal_hst_wfc3-uvis_saturn-2025_all_v1_readme.txt (найден на странице цикла 32 Сатурна). По README: левый край = 360° System III з. д.; цвет F631N/F502N/F395N, «slight contrast enhancement». На карте поперёк идёт тёмная полоса — тень колец.

**7. Сатурн, Cassini** — папка https://atmos.nmsu.edu/PDS/data/PDS4/co_iss_global-maps/data_derived/
- Cassini_ISS_RGB_Saturn_global_color_map_original.fits — 2026-11-20T08:19:58Z · 77 829 120 байт · sha256 32a62eca…
- Cassini_ISS_RGB_Saturn_global_color_map_original.xml — 2026-11-20T08:19:58Z · 10 595 байт · sha256 0d1ab898…
Оба положены как есть. Заголовок FITS: 3601×1801×3, float32 (BITPIX −32); LAT_C −90…90 шаг 0,1 (планетоцентрическая); LON_W от 360 до 0 шаг −0,1 (западная долгота); разрешение 161 км/пикс; фазовый угол 42,5°; съёмка 2011-08-11. Метка: Equirectangular, центральный меридиан 180°, Positive West. GDAL 3.8.4 этот FITS не открыл — читать astropy или по метке.

**8. Кольца Сатурна** — https://pds-rings.seti.org/holdings/archives-volumes/CORSS_8xxx/CORSS_8001.tar.gz — см. раздел 8 ниже.

**9. Уран, OPAL 2024a** — https://archive.stsci.edu/missions/hlsp/opal/cycle32/uranus/hlsp_opal_hst_wfc3-uvis_uranus-2024a_f657n-f547m-f467m_v1_globalmap.tif
2026-11-20T08:19:59Z · 787 762 байт · sha256 838dbf45… · 721×361 RGB. Как есть.
README: https://archive.stsci.edu/missions/hlsp/opal/cycle32/uranus/hlsp_opal_hst_wfc3-uvis_uranus-2024_all_v1_readme.txt. Цвет F657N/F547M/F467M, «slight contrast enhancement». Южная часть карты не снята (чёрное поле с цветной бахромой по краю).

**10. Нептун, OPAL.** Последний цикл Нептуна на странице — Cycle 33 (https://archive.stsci.edu/hlsp/opal/opal-neptune-cycle-33). Две цветные карты, 2026a и 2026b; взята более поздняя, 2026b.
Файл: https://archive.stsci.edu/missions/hlsp/opal/cycle33/neptune/hlsp_opal_hst_wfc3-uvis_neptune-2026b_f467m-f547m-f657n_v1_globalmap.tif
2026-11-20T08:19:59Z · 789 926 байт · sha256 456bcf12… · 721×361 RGB. Как есть.
README: https://archive.stsci.edu/missions/hlsp/opal/cycle33/neptune/hlsp_opal_hst_wfc3-uvis_neptune-2026_all_v1_readme.txt. По README: съёмка 31 августа – 1 сентября 2026; 2 пикс./градус (с передискретизацией); левый край = 360° з. д., долгота убывает вправо; цвет F657N/F547M/F467M «with some contrast enhancement». Северная часть не снята (чёрное поле с цветной бахромой по краю).

**11. Земля, июнь** — взята **первая, базовая** (без рельефа): https://assets.science.nasa.gov/content/dam/science/esd/eo/images/bmng/bmng-base/june/world.200406.3x21600x10800.jpg
2026-11-20T08:20:01Z · 21 793 655 байт · sha256 282608580a290723655bfbe917e69ea2f93f4da068dfa96ff4a152b1c6ec36be · 21600×10800 RGB JPEG. Геопривязки в файле нет (по названию — глобальная 21600×10800). Оригинал в репозиторий не положен — в репозитории только уменьшенная версия по таблице. Вторая (topo) не понадобилась.

**12. Ио** — https://planetarymaps.usgs.gov/mosaic/Io_GalileoSSI-Voyager_Global_Mosaic_ClrMerge_1km.tif
2026-11-20T08:20:09Z · 196 637 696 байт · sha256 135f88cb645bfdb4e045b380971ab2ba14e230590c96c9c86cfe7310fda881ac
11445×5723 RGB. SimpleCylindrical Io, **центральный меридиан 0** (края около 180°). Пиксель 1000 м. Оригинал не положен.

**13. Европа** — https://planetarymaps.usgs.gov/mosaic/Europa_Voyager_GalileoSSI_global_mosaic_500m.tif
2026-11-20T08:20:16Z · 192 777 263 байт · sha256 a323f0c9ccb47d5af9902ea8297fe81f9a9708795645b80801f103c3f7c9a624
19631×9816, серая. SimpleCylindrical Europa, **центральный меридиан 180** (края около 0°). Пиксель ≈500 м. Оригинал не положен. Уменьшено до 8192×4096 (у оригинала соотношение 19631:9816 — почти 2:1).

**14. Ганимед** — https://photojournal.jpl.nasa.gov/tiff/PIA17901.tif — **не открылся.** Адрес отвечает 301 на https://science.nasa.gov/photojournal/ (общая HTML-страница); получен HTML на 296 820 байт (sha256 eb6e1d5c…), карты нет. Замена не искалась по правилу 1. Ответ на вопрос «одна карта или две на листе» поэтому неизвестен.

**15. Каллисто** — https://planetarymaps.usgs.gov/mosaic/Callisto_Voyager_GalileoSSI_global_mosaic_1km.tif
2026-11-20T08:20:23Z · 114 640 717 байт · sha256 e1f0bd2e0e05de605d067d6b5f5ededddaf31ca6c064562a1ca770f15a7dbaa3
15138×7569, серая. SimpleCylindrical Callisto, **центральный меридиан 180**. Пиксель ≈1000 м. Оригинал не положен. Внизу карты есть неснятые чёрные области.

**16. Титан** — https://planetarymaps.usgs.gov/mosaic/Titan_ISS_P19658_Mosaic_Global_4km.tif
2026-11-20T08:20:24Z · 8 169 529 байт · sha256 ca0fe5f6… · 4040×2020, серая. Equirectangular Titan, **центральный меридиан 180**. Пиксель ≈4005 м. Положен как есть.

## Разделы

### 8. Кольца Сатурна
Загрузка ещё идёт (архив 6 142 435 253 байт > 100 МБ). По заданию в репозиторий пойдут только профили оптической толщины и их метки. Будет дописано следующим коммитом.

## Не скачивалось (по заданию)
Цветные мозаики Меркурия; USGS `gany_simp_2km.jpg`; Akatsuki.
