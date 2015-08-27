# hp-41_icebox
## HP-41: The ICEBOX rom

My passion for low level programming has paid off as I have taken Angell Martin’s Toolbox.rom and started forking it as the ICEBOX.ROM. The first changes was to add two new functions, the RROM and WROM (supplanting the less useful sRG? and X>ST functions). With these, you can read and write directly to HEPAX RAM.

In version 1B I also added the function SROM (Search ROM). It will search the ROM for any rom word.

Version 1C saw the advent of the functions >442 and >244. I also added the random nuber generator RAND from SandMath III.

In version 1D I added the functions: Swap Alpha and RAM registers and Swap Stack and RAM registers – including Last X. By setting flags 0-3 you can decide which registers you want to swap (starting register will be from 0 to 15). This means that you can save three sets of stack registers or four Alpha registers for later use. Finally there is an easy way to work with several Extended Memory files and do copy/paste between them.

In version 1E, swtching between HEPAX RAM blocks in the NoV-32 or the NoV-64 became really easy. I added the functions N100, N101, N102 and N103 to switch directly to the desired ram block.

Version 1F is a bug fix release. It corrects some prompting functions (like FDATA).

In version 1G, I added the functions N200, N201, N202 and N203 to complete the direct bank switching for the NoV-64. A function NXXX was also added to take a number in X and write it directly to address 4100 – in this way, the user doesn’t have to go via HEX>NNN and WROM to write a new setting to 4100 (makes for easier bank switching in FOCAL programs). I also added the functions SAVEN and GETN to save and restore main memory to HEPAX RAM (using the file name “N”, these functions call HSAVEA and HGETA respectively). They make it possible to assign the saving and restoring ov main memory to keys.

The function NXXX cahnged name in version 1H to NX for saving two key strokes :-) I added the N? to query address 4100 (it shows the current NoV config). The function NBS (NoV Block Switch) was added to be able to switch to a new config and restore Main Memory to a file named “N” in the new RAM block in one function. NBS is a prompting function that only accepts input in the ranges 000-003, 100-103 and 200-203. An input outside these ranges results in “DATA ERROR”. If the file “N” or the function HGETA are not found, a “NONEXISTENCE” is displayed. If you switch the ROM block (first of the three digits prompted for), the message “CALC OFF” is briefly displayed to remind you that you need to turn the calc off and on to complete the ROM block switch.

Feel free to use the ICEBOX1H.ROM or tweak it’s source. The User Manual should contain what you need to make use of the module.

The ICEBOX uses XROM number 4. If this conflicts with another rom you use, you may use alternative ICEBOX roms with XROM #20 or #16.

#### Saving all HEPAX RAM of a NoV module to mass storage

With the programs “SAVENOV” and “GETNOV”, you can now very easily save and retreive all the HEPAX ram in a NoVRAM, NoV-32 or NoV-64 module.

The scenario: You are a blissful owner of a NoVRAM, NoV-32 or NoV-64 module by Diego Diaz. You have loaded into the module’s ROM the companion module (the ICEBOX) and the excellent CCD OS/X (or another rom with the SAVEROM and GETROM functions). You want an easy way to back up the entire HEPAX RAM to a mass storage device (cassette drive, HP-IL disc drive, RS-232 or PIL-Box connected to a PC). Manually, this is a tedious task, especially with the NoV-64, having 4 blocks of HEPAX RAM with 4 pages of 4K HEPAX RAM each.

With the SAVENOV/GETNOV program in ordinary HP-41 RAM, simply XEQ “SAVENOV” and it will prompt for the type of module you wish to back up (1 for the NoVRAM, 2 for the NoV-32 and 3 for the NoV-64). Upon you pressing the right number and the R/S key, it commences with backing up the whole RAM of the module with files named “N0-8”, “N0-9”, “N0-10”, “N0-11”, “N1-8”, “N1-9″… “N3-11” and shows “NOV SAVED”. The same with retrieving the whole RAM of the module: Prompting for the right module type, copying each page into it’s proper place and ending with “NOV RESTORED” in the display. Simple. For the NoVRAM, the program only saves and restores “N0-8” till “N0-11”, and the NoV-32 includes also the “N1-8” – “N1-11”.

#### MCODE: Using the HP-16C as a tool

Being a calculator collector and addict, I search out new uses for my little precious ones. My calculators are solutions in search of a problem.

I have always thought of the HP-16C as a special item in my collections. It’s the only programmable programmers calculator, and it’s capabilities are indeed impressive. But other than simple additions and subtractions in hex mode, I didn’t really find any use for it. Until I got more heavily involved in Machine CODE (MCODE) programming on the HP-41.

I really love MCODE. With it I can make the HP-41 do just about anything. It’s a nice challenge to do weird stuff on a 30 year old technology.

Some of the challenges in MCODE has to do with calculating jump codes. I used to carry a set of tables to get the right hex words for jumping short distances, for doing calls to the operating system and for the port dependent jumps. No more. The HP-16C comes to the rescue with the MJUMP program.
