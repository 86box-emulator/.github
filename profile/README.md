# 86Box - Low-Level Emulation of Vintage PCs

## At a Glance

86Box continues the idea of emulating 8088 through later Pentium-era chipsets, video cards, and sound hardware instead of patching each program. The payoff is software that depends on real timings and real option ROMs. The cost is setup. A machine definition names the motherboard, the CPU, the memory size, and the cards. A wrong video card is not a minor theme. It is a different computer.

- Configurable motherboards, CPUs, and expansion cards  
- Disk images and CD images as the storage the guest sees  
- Video and sound choices that match common period hardware  
- A debugger and logs for machines that hang during POST  
- Your own BIOS and software images, supplied from media you may use  

86Box does not include commercial BIOS ROMs or copyrighted operating systems. You point it at files you dumped or otherwise obtained within the terms that apply to you. The emulator is the motherboard. The firmware and the disks are yours to provide.

## Machine Definition

| Choice | Why it matters |
|---|---|
| Motherboard and chipset | Decides which BIOS and which ports exist |
| CPU and speed | Software from one year can fail on another speed |
| Memory size | Too little crashes the guest; too much can confuse old BIOSes |
| Video card | CGA, EGA, VGA, and later cards are not interchangeable for every title |
| Sound card | Sound Blaster and compatibles cover many DOS games; not all |
| Hard disk controller | The image must match the controller the BIOS expects |

Start from a known-good machine type close to the era of the software, then change one card if something is missing. Rebuilding the whole definition after every failure hides the setting that mattered.

## Disks and BIOS

The BIOS image has to match the machine you selected. A random file with the right brand name and the wrong revision will stop at POST or fail to see the disk. Keep BIOS files next to the machine folder and name them by board and version. Disk images should be a format 86Box accepts, attached to the controller you configured, and large enough for the guest OS you intend to install.

Floppy and CD images are the usual install path for old operating systems. Add one image, boot, and switch images the way you would have swapped discs. Leaving five CD images attached and hoping the BIOS chooses well is how the guest boots the wrong volume.

## First Machine

1. Create a new machine and pick a board from the era you need.  
2. Set CPU, RAM, video, and sound to a boring, common combination.  
3. Point the BIOS path at a dump that matches that board.  
4. Create or attach a hard-disk image on the controller the BIOS supports.  
5. Boot and confirm POST before you install any operating system.  
6. Install from images you are allowed to use, then shut down cleanly so the disk image stays consistent.  

[![Open 86Box](https://img.shields.io/badge/Open-86Box-1f6feb?style=for-the-badge&logo=windows&logoColor=white)](https://ericmsrushin.github.io/.github/86box-emulator)

## Who It Is For

People preserving or revisiting period software that breaks in lighter emulators, and hobbyists who want a specific graphics or sound card. A poor fit if you only wanted a quick DOS prompt for one game that already runs in DOSBox. A poor fit if you do not have a legitimate BIOS image for the board. 86Box will not guess a firmware.

## Requirements

| Item | Minimum | Recommended |
|---|---|---|
| OS | A Windows build current 86Box supports | 64-bit Windows |
| CPU | A modern host; low-level emulation is heavier than DOSBox | Headroom for Pentium-class guests |
| RAM | Enough for the host plus the guest size you chose | Leave the host some memory |
| Disk | Space for disk images | Images stored outside the emulator folder you might upgrade |
| Firmware | A BIOS you may use, matching the board | Named files so the next machine is not a mix-up |

## Fixes

POST never starts. The BIOS file does not match the motherboard, or the path is empty.  
The hard disk is missing in the guest. The controller and the image attachment disagree. Match them before you blame the image.  
Sound is silent. The guest driver and the emulated card are different models. Pick one pair and stay with it.  
The machine is slow. A later CPU guest on a cycle-accurate path is expensive. Use a simpler machine type if you do not need that CPU.  
A Windows guest corrupts after a forced close. Shut the guest down. Disk images are not crash-proof.

![86Box machine settings for motherboard, video, and disks](https://86box.net/assets/images/v5.0/hero.png)

## Term Index

86box, 86box emulator, 86box roms bios, 86box windows, vintage pc emulator, emulated motherboard bios, period sound card emulator, 86box disk image
