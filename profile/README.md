# mtrk

mtrk is an open-source framework for MRI pulse sequence development. It includes a Python api (mtrk_designer_api) to generate .mtrk sequence description files using the Json-based Sequence Description Language (SDL). To ease the programming, mtrk also proposes a web-based drag-and-drop interface to design pulse sequences (mtrk_designer_api). .mtrk files can be visualized in the web-based mtrk_viewer and sent to the mtrk driver sequence (mtrk_seq) to play on a Siemens scanner. 

A conversion tool is available to transform .mtrk files into Pulseq files, allowing for the use of any Pulseq-based external tool.  

<p align="center">
  <img src="profile/mtrk_overview.png" width="529"/>
</p>

## Installation

The install script is available here. 

## SDL file format

The .mtrk files describe MRI pulse sequences using the light-weight human-readable Sequence Desciption Language (SDL) based on Json. The file structure includes seven sections allowing for the definition of technical and sequence specifications, reconstruction information, main sequence structure, and corresponding arrays or equations. 

<p align="center">
  <img src="profile/mtrk_sdl.png" width="886"/>

</p>
