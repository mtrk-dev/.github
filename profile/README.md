## ISMRM 2024 
Abstract number 4671, "mtrk – A flexible open-source framework for developing MRI pulse sequences based on common web standards". (https://submissions.mirasmart.com/ISMRM2024/Itinerary/PresentationDetail.aspx?evdid=5911)

Contact: anais.artiges@nyulangone.org

## What is mtrk?

mtrk is a novel concept for developing and working with pulse sequences in Magnetic Resonance Imaging (MRI). Traditionally, MRI pulse sequences are developed as dynamically loadable binary libraries, programmed using vendor-provided proprietary SDKs. These monolithic SDKs are complex, barely documented, and only in part accessible to external developers and members of the MRI research community. This makes MRI development very challenging - on the one hand because only few researchers manage to work with the SDKs, on the other hand because frequent invasive changes to the vendor SDKs create significant maintenance effort. Furthermore, strict license agreements make dissemination of research developments impossible and contend with the idea of reproducible research.

mtrk is an attempt to change the paradigm in MRI sequence development towards a modern Open-Source-driven model. While current open-source and vendor-agnostic initiatives like Pulseq (Layton et al., MRM, 2017) or SequenceTree (Magland et al., MRM, 2016) provide reliable solutions to design an share pulse sequences, mtrk comes with a complementary concise and user-friendly Sequence Description Language (SDL) file format. Its two-fold goal is to enable rapid exchange of SDL files for cloud computing and smooth sequence tuning by either manual modification of the SDL file, Python command line, or a web-based graphical interface.

mtrk takes the shape of an open-source framework for MRI pulse sequence development. It includes a Python api (mtrk_designer_api) to generate .mtrk sequence description files using the Json-based SDL. To ease the programming, mtrk also proposes a web-based drag-and-drop interface to design pulse sequences (mtrk_designer_api). .mtrk files can be visualized in the web-based mtrk_viewer and sent to the mtrk driver sequence (mtrk_seq) to play on a Siemens scanner. 

A conversion tool is also available in mtrk_designer_api to transform .mtrk files into Pulseq files, allowing for the use of any Pulseq-based external tool.  

<p align="center">
  <img src="mtrk_overview.png" width="529"/>
</p>

## Flexibility

mtrk uses a highly modular design in which sequences are formulated using a Sequence Description Language (SDL) based on the common JSON syntax. The SDL is un-opinionated, meaning that multiple ways for formulating one sequence exist. Moreover, the SDL makes no assumption on how the SDL files have to be generated, giving researchers the freedom of choice regarding which programming language they want to use for their sequence development projects. Moreover, because the SDL is a common text-based format, the sequence calculation can be done on any operating system and on any computer, ranging from the MRI scanner’s console computer over local research servers to cloud instances.

<p align="center">
  <img src="mtrk_sdl.png" width="886"/>
</p>

## Accessibility

mtrk provides a graphical user interface (mtrk_designer_gui), which enables the development of pulse sequences in an intuitive way without programming. This web-based GUI is intended to be used both for education and training, as well as for research applications later on. It has for now been used to implement simple sequences, such as spin echo and gradient echo with single line readout, but will soon be able to handle more complex ones. 

To improve accessibility, the SDL format can be converted to Pulseq, which is already widely used in open-source pulse sequence programming. We are also working on a converter from Pulseq to SDL to make the connexion between the two formats smoother. 

<p align="center">
  <img src="mtrk_ui.png" width="886"/>
</p>

## Reproducibility

When executing an mtrk sequence, the MRI scanner plays out the instructions and pulses contained in the mtrk file. This means that the pulse sequence is entirely defined by the mtrk file and not dependent on the specific MRI software version used during data acquisition. Hence, researchers can reproduce scientific results at a later time or at a different location because the mtrk file can be easily archived or distributed. Because the SDL format is decoupled from the vendor SDKs, the mtrk files can be shared in Git repositories attached to publications without violating license agreements, and they do not require refactoring for every software update installed on the MRI scanners.

## Transparency

With the traditional development model, sequence binaries are black-boxes in the sense that it is unclear how the sequence settings translate into DSP instructions. Moreover, because part of the functions are hard-coded into the MRI software platform and can change with every release, it is impossible to say which exact waveforms and timings were used to acquire the data. With mtrk on the other hand, all instructions can transparently be read form the mtrk file. This enables exact Bloch simulations of the sequence, so that automated testing and quality control of sequences is possible. Furthermore, part of the development work can be shifted from sitting in front of an MRI scanner towards simulation-driven development.

## Documentation

To learn more, please take a look at the mtrk [Documentation](https://mtrk-dev.github.io/doc/). Please note that mtrk is still under active development, so that the code and documentation may not be complete yet and evolve over time. Please also don’t hesitate to get in touch with us if you like to contribute to the development.

## Installation

### Test Installation (using Vagrant)

A quick test installation of the MTRK tools (prototype state) can be done using Vagrant, which will provision a VM and install the software automatically into the VM.

Install both VirtualBox (https://www.virtualbox.org) and Vagrant (https://www.vagrantup.com) on your host computer. This can be done using any computer with an Intel chipset (Windows, Linux, Intel-based Apple Mac).

Clone the MTRK Designer GUI repository into a folder on your computer:

`git clone https://github.com/mtrk-dev/mtrk_designer_gui.git`

Change the directory and run the vagrant command:

```
cd mtrk_designer_gui
vagrant up
```

This will create a new VM and install all required dependencies. Once the installation has finished, the MTRK Designer GUI and MTRK Viewer Software can be accessed by opening the URLs `127.0.0.1:5010` and `127.0.0.1:6010` respectively in a modern browser (Firefox or Chrome).

If the page is not visible at the designated port. Run the `vagrant port` command to see if the port has been auto-forwarded due to a collision and access the tool on that port.

### Server Installation

Automatic installation on a production server can be done using a provided installation script. MTRK currently requires **Ubuntu 22.04 LTS** as the operating system.

Check out the repositories on the server and start the installation:
```
cd /opt
git clone --depth 1 https://github.com/mtrk-dev/mtrk_viewer.git
git clone --depth 1 https://github.com/mtrk-dev/mtrk_designer_gui.git
cd mtrk_designer_gui/app
git clone --depth 1 https://github.com/mtrk-dev/mtrk_designer_api.git
sudo bash /opt/mtrk_designer_gui/install.sh
```
### Acknowledgements

<p align="center">
  <img src="cloud_mr_logo.png" width="200"/>
</p>

mtrk is part of Cloud MR, a multi-year project aimed at developing a comprehensive software platform to simulate all aspects of the MRI experiment. This research project is supported by the National Institute of Biomedical Imaging and Bioengineering (NIBIB) of the National Institutes of Health (NIH) under the Awards R01 EB024536 (PI: Riccardo Lattanzi).



