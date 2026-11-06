---
layout: page
title: "CAMCityRoads: The Cambridge City Roads Dataset"
description: "From raw LiDAR sweeps to a textured, labelled and georeferenced model of a city's local streets, recorded with one low-cost scanner and no GNSS."
image: /assets/camcityroads/01_hero_title.jpg
---

<style>
.ccr-subtitle { font-size: 1.1rem; color: #767676; }
.ccr-links { font-weight: bold; }
.ccr-todo { color: #ac4142; font-weight: normal; }
.ccr figure { margin: 0 0 1rem; }
.ccr figure img { width: 100%; height: auto; margin-bottom: .4rem; }
.ccr figcaption { font-size: .85rem; line-height: 1.4; color: #767676; }
/* grids may be wider than the 38rem text column so the images stay readable */
.ccr-wide { position: relative; left: 50%; transform: translateX(-50%); width: min(64rem, calc(100vw - 2rem)); }
.ccr-grid { display: grid; gap: 1rem; grid-template-columns: 1fr; }
@media (min-width: 40em) { .ccr-grid { grid-template-columns: repeat(2, 1fr); } }
@media (min-width: 64em) { .ccr-grid.ccr-3 { grid-template-columns: repeat(3, 1fr); } }
.ccr-video { position: relative; aspect-ratio: 16 / 9; margin-bottom: 1rem; background: #f9f9f9; border: 1px dashed #ccc; border-radius: 5px; display: flex; align-items: center; justify-content: center; text-align: center; }
.ccr-video iframe { position: absolute; inset: 0; width: 100%; height: 100%; border: 0; border-radius: 5px; }
.ccr-attrib { font-size: .75rem; color: #767676; }
</style>

<div class="ccr" markdown="1">

# CAMCityRoads: The Cambridge City Roads Dataset

<p class="ccr-subtitle">From raw LiDAR sweeps to a textured, labelled and georeferenced model of a city's local streets, recorded with one low-cost scanner and no GNSS.</p>

<p class="ccr-links">Paper <span class="ccr-todo">(TO ADD)</span> · Dataset <span class="ccr-todo">(TO ADD)</span> · Code <span class="ccr-todo">(TO ADD)</span> · Video <span class="ccr-todo">(TO ADD: YouTube link)</span></p>

<figure>
  <img src="/assets/camcityroads/01_hero_title.jpg" width="1920" height="1080" alt="CAMCityRoads title over the survey drives drawn on the Ordnance Survey map of Cambridge">
</figure>

## Overview

Local highway authorities maintain most of the road network, yet there is little open data on which to test
automated inspection of local streets, and little evidence of which measurements a cheap survey can be trusted for.
CAMCityRoads is an open mobile-mapping dataset of Cambridge, UK, built to provide both.

It holds 14 drives (51.7 km, 22.9 km of distinct street, much of it driven more than once) with:

- the raw LiDAR, camera and IMU streams;
- LiDAR SLAM trajectories and point clouds;
- 72 textured street meshes and a city mesh joining every drive;
- 26-class labels on every photo and every LiDAR point the camera sees;
- road and street-asset indicators mapped across the city, each validated between independent drives.

<!-- When the YouTube link exists, replace the placeholder <p> below with:
<iframe src="https://www.youtube-nocookie.com/embed/VIDEO_ID" title="CAMCityRoads video" loading="lazy" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
-->
<div class="ccr-video">
  <p class="ccr-todo">Video: TO ADD (YouTube link)</p>
</div>

## The rig

<figure>
  <img src="/assets/camcityroads/03_rig_annotated.jpg" width="1580" height="1053" loading="lazy" alt="The scanner on the van's roof bars, with the LiDAR, camera and IMU labelled">
</figure>

A prototype scanner on the roof bars of a mid-sized van: a Velodyne VLP-16 LiDAR (16 beams, 10 sweeps a second), one
forward RGB camera (3.2 MP) and an Xsens MTi-610 IMU (400 Hz). There is no GNSS receiver; everything is positioned
from the LiDAR alone. None of the hardware is new: the LiDAR was eleven years old at the time of the survey.

## From raw data to a city model

<div class="ccr-wide ccr-grid ccr-3">
  <figure>
    <a href="/assets/camcityroads/04_lidar_sweep.jpg"><img src="/assets/camcityroads/04_lidar_sweep.jpg" width="1920" height="1280" loading="lazy" alt="A single raw LiDAR sweep"></a>
    <figcaption><strong>One LiDAR sweep.</strong> A single 0.1 s rotation of the 16 beams.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/05_slam_map.jpg"><img src="/assets/camcityroads/05_slam_map.jpg" width="1920" height="1280" loading="lazy" alt="LiDAR sweeps aligned into a loop-closed SLAM map"></a>
    <figcaption><strong>SLAM map.</strong> Thousands of sweeps aligned into one loop-closed map.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/06_coloured_cloud.jpg"><img src="/assets/camcityroads/06_coloured_cloud.jpg" width="1622" height="1081" loading="lazy" alt="Point cloud coloured from the anonymised photos"></a>
    <figcaption><strong>Colour.</strong> Each point coloured from the anonymised photos.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/07_mesh_untextured.jpg"><img src="/assets/camcityroads/07_mesh_untextured.jpg" width="1620" height="1080" loading="lazy" alt="Untextured surface mesh built from the LiDAR"></a>
    <figcaption><strong>Mesh.</strong> Surface geometry built from the LiDAR.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/08_mesh_textured.jpg"><img src="/assets/camcityroads/08_mesh_textured.jpg" width="1620" height="1080" loading="lazy" alt="LiDAR mesh with the photos projected as texture"></a>
    <figcaption><strong>Texture.</strong> The photos projected onto the LiDAR mesh.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/09_3d_labels.jpg"><img src="/assets/camcityroads/09_3d_labels.jpg" width="1620" height="1080" loading="lazy" alt="Point cloud coloured by semantic class"></a>
    <figcaption><strong>3D labels.</strong> Road, footway, kerb, lane markings, manholes, buildings, vegetation, poles, street lights and traffic signs.</figcaption>
  </figure>
</div>

Faces and number plates are blurred in every photo, and the blurring is carried into the coloured clouds and the
mesh textures.

## Case studies

The labelled clouds and photos are used to map road and street-asset indicators every 10 m across the city. Each
map is checked by agreement between independent drives of the same street and by judging random samples of flagged
places in the photos.

<div class="ccr-wide ccr-grid ccr-3">
  <figure>
    <a href="/assets/camcityroads/10_usecase_road_markings.jpg"><img src="/assets/camcityroads/10_usecase_road_markings.jpg" width="1620" height="1080" loading="lazy" alt="Road markings coloured by paint contrast"></a>
    <figcaption><strong>Road markings.</strong> Painted markings, coloured by their contrast against fresh paint every 10 m (orange: lower, white: higher). An indicative measure of wear.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/11_usecase_vegetation.jpg"><img src="/assets/camcityroads/11_usecase_vegetation.jpg" width="1920" height="1280" loading="lazy" alt="Branches inside the 5.3 m road clearance highlighted in orange under a grid"></a>
    <figcaption><strong>Vegetation clearance.</strong> Branches inside the 5.3 m clearance over the carriageway (orange), under a grid drawn at 5.3 m above the road.</figcaption>
  </figure>
  <figure>
    <a href="/assets/camcityroads/12_usecase_traffic_sign_3d.jpg"><img src="/assets/camcityroads/12_usecase_traffic_sign_3d.jpg" width="1920" height="1280" loading="lazy" alt="A traffic sign inside a tree, highlighted yellow in the point cloud"></a>
    <figcaption><strong>Traffic signs hidden by foliage.</strong> A sign inside a tree (yellow in the point cloud). From 56 m away it cannot be seen; close up it is clear.</figcaption>
    <div class="ccr-grid" style="grid-template-columns: 1fr 1fr; gap: .5rem; margin-top: .5rem;">
      <a href="/assets/camcityroads/13_traffic_sign_photo_far.jpg"><img src="/assets/camcityroads/13_traffic_sign_photo_far.jpg" width="1404" height="1051" loading="lazy" alt="Photo from 56 m: the sign, ringed, is hidden by the tree"></a>
      <a href="/assets/camcityroads/14_traffic_sign_photo_near.jpg"><img src="/assets/camcityroads/14_traffic_sign_photo_near.jpg" width="1404" height="1051" loading="lazy" alt="Close-up photo: the sign, ringed, is visible"></a>
    </div>
  </figure>
</div>

Between drives, gradient and crossfall agree to a median 0.14–0.15% and kerb height to 6 mm; 79–100% of judged
flagged places were confirmed. Rutting and ponding, millimetre-scale surface shape, do not repeat with this sensor
and are reported as limits.

## One city, on the national grid

<div class="ccr-wide">
  <div class="ccr-grid">
    <figure>
      <a href="/assets/camcityroads/15_city_drives.jpg"><img src="/assets/camcityroads/15_city_drives.jpg" width="1180" height="787" loading="lazy" alt="All 14 drives joined into one point cloud"></a>
      <figcaption>All 14 drives joined into one frame using the LiDAR alone.</figcaption>
    </figure>
    <figure>
      <a href="/assets/camcityroads/16_georeferenced_on_os_map.jpg"><img src="/assets/camcityroads/16_georeferenced_on_os_map.jpg" width="1538" height="1025" loading="lazy" alt="The drives overlaid on the Ordnance Survey map of Cambridge"></a>
      <figcaption>The same drives placed on the British National Grid using only open data (Ordnance Survey building outlines and the Environment Agency terrain model). On held-out sections the road lies a median 0.14 m from the terrain model and the facades 0.52 m from the building outlines.</figcaption>
    </figure>
  </div>
  <p class="ccr-attrib">Contains OS data © Crown copyright and database right 2026. Contains Environment Agency information © Environment Agency copyright and/or database right 2022.</p>
</div>

## Citation

```bibtex
@article{camcityroads,
  title   = {CAMCityRoads: The Cambridge City Roads Dataset},
  author  = {TO ADD},
  journal = {Advanced Engineering Informatics},
  year    = {TO ADD},
  doi     = {TO ADD}
}
```

## Acknowledgements

Part of the Digital Roads Prosperity Partnership, supported by EPSRC [EP/V056441/1]. SLAM and LiDAR classification
were produced with Exwayz 3D Mapping, published with Exwayz's permission. The data are CC BY 4.0; the labels are
CC BY-NC-SA 4.0.

</div>
