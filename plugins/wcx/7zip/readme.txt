////////////////////////////////////////////////////////////////////////////////
// 7zip Plugin for Total Commander
// Based on 7zip core code (http://www.7-zip.org/)
//
// (c) 2004-2008 Adam Strzelecki <ono@java.pl>
//     2009 Dmitry Efimenko <tbbcmrjytv@gmail.com>
//     2009 Alexandr Popov <Sax0n0xaS@gmail.com>
//     2010 Cristian Adam <cristian.adam@gmail.com>
//     2011 dllee <dllee.tw@gmail.com>
//
// This program is free software; you can redistribute it and/or
// modify it under the terms of the GNU General Lesser Public License
// as published by the Free Software Foundation; either version 2.1
// of the License, or (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU Lesser General Public License
// along with this program; if not, write to the Free Software
// Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
////////////////////////////////////////////////////////////////////////////////

1. About
--------
The 7zip extractor plugin provides 7zip archive support for popular
Total Commander file manager.
Associate it with *.7z extension in WCX Plugin configuration or use built-in
auto-installer of Total Commander 6.5 or higher.

2. Features
-----------
 - File listing
 - Extraction & compression
   (7-Zip 9.x compatible methods)
 - 7zAES file decryption/encryption using password
 - CRC test and detection
 - Multi-language support, langpacks included:
   Chinese(BIG5), Czech, Danish, English (built-in), German, Lithuanian, Russian.
 - SFX support: put 7z.sfx, 7zC.sfx or 7zCon.sfx into 7zip.wcx folder
		and use *.exe filename to create 7zip SFX archive.
	 (additional SFX modules can be found here http://7zsfx.info/en/
	 if you need configuration file for the SFX module, then put config.txt to the 7zip.wcx folder)
 - set 7z datetime to newest file.
 - Extraction & compression files in background.

3. Translation
--------------
To use selected translation from lang/ copy it to 7zip.lng file into 7zip.wcx
installation folder.
Note for translators: On OS supporting unicode codepage= setting is crucial as
	translation strings are set using unicode SetWindowTextW(...).
	Also when sending the translation please translate "7-Zip archive support"
	for your language string in pluginst.inf if it does not exist.

4. Todo
-------
 - 7Zip volumes
 - Custom sort, unsorted packing order

5. Contact
----------
 - official forum thread: http://ghisler.ch/board/viewtopic.php?t=18178

6. History
----------
0.7.6.5a: 2011-10-24 Christian Ghisler
 - New: Recompiled for 64-bit Windows

0.7.6.5: 2011-06-29 dllee
 - New: encrypt password before saving to 7zip.ini file.
        remark: the maximum password size is 64 unicode characters.
 - New: before pack/delete files to/from a packed file, check if it contains digital signature,
        if the packed file contains digital signature, a dialog box will pop-up to confirm the actions.
 - New: add 104 translation ID for digital signature warning dialog box. (can use \n for line break)

0.7.6.4a: 2011-06-21 dllee
 - Try: fixing extract problem, fine tune extract thread, add thread id to debug messages.
 - Fix: stop extracting when user press Cancel as 7zip plugins freezing.

0.7.6.3: 2011-05-17 dllee
 - Add: solid block size default selection when Method/Level changed. (act the same as 7-zip file manager)
 - Fix: add default hidden compression properties, to make 7zip plugins performs the same as 7-zip file manager.
        For old version, those hidden properties are using higher compression level, so, if you use the same
        compression parameters(ex:Level,Dictionary Size,Word Size,Solid Block Size), 7zip plugins will have
        a smaller result but spend more time, especially when using Fast or Fastest level.
        Using this version, you will have the same result as 7-zip file manager for the same parameters.
 - New: add   0 translation ID for 7Zip plugins. (used for the dialog title when packing an unreadable file)

0.7.6.3b: 2011-05-06 dllee
 - Try: Pack/Unpack files in background.
 - Add: Dialog for retry/cancel when packing an unreadable file.
 - New: add  103 translation ID for The file is using by another application. (when packing an unreadable file)

0.7.6.3a: 2011-05-05 dllee
 - Fix: Pack files even if they are operating/opening by another application, like Word, Excel.

0.7.6.2: 2011-04-29 dllee
 - Adj: Dialog adjustment, remove black background of 7zip Icon.
 - Update: danish, russian and lithuanian translation

0.7.6.1: 2011-04-14 dllee
 - Fix: Attributes of file is not correct when extracting
 - New: restore File CreateTime/AccessTime for empty file when extracting

0.7.6.0: 2011-04-13 dllee
 - New: set 7z datetime to newest file
 - New: reorder directory list (bug fixed for the dir's datetime with sub-dir)
 - Fix: overwrite "filename.ext" with "FileName.Ext" in archive
 - Fix: maximum thread count and show again translated label Dictionary size: when changing compression level or method
 - New: force to store File Modify Time to archive, and show 1980-01-01 00:00 when no Modify Time stored in archive
 - New: add  102 translation ID for None found  (for SFX combobox)
 - New: add  115 translation ID for kNumPasses:
 - New: add 2026 translation ID for set 7z datetime to newest file
 - New: add 2027 translation ID for reorder directory list
 - Fix: english.lng 100/101 solid/Non-solid to Non-solid/solid
 - New: chinese-big5 translation

-- maintaining by dllee

0.7.5.0: 2010-12-16
 - Build based on 7Zip 9.20 code
 - Unicode only version

-- Continued workd by Cristian Adam

0.7.2.1: 2009-11-26
 - Fix: update progress bar
 - New: shows error message when creating sfx-archive with password

0.7.2: 2009-11-25
 - New: SFX module and configuration not changes, when updating archives
 - New: selects compatible compression method when updating SFX archives
 - italian translation updated

0.7.1: 2009-11-18
 - Build based on 7Zip 9.07 beta code
 - New: can handle LZMA2 compressed archives

-- Continue work by Alexandr Popov
 
0.6.4: 2009-03-07
 - Fix: zero length files
 - New: memory usage info
 - New: solid block size
 - New: better SFX support
 - New: ability to select application icon when creating sfx-archives
 - New: "expert" options, which can save few bytes on packing
 - improved progress bar while packing/unpacking
 - important, know bug: may not work on big dictionaries

0.6.3: 2009-02-05
 - implemented >2Gb archive support
 - danish, italian, spanish translation
0.6.2: 2009-02-02
- Fix: deletion from archive (again)
- New: ability to select SFX-module then creating sfx-archives
- New: GUI changes
- bug fixes
0.6.1: 2009-01-12
- Build based on 7Zip 4.64 stable code
- Fix: corrected folders deletion from archive
- New: multithread compression with ability to select number of compression threads
- New: kNumPasses parameter for the Deflate and Deflate64 compression methods
- bug fixes

-- Continue work by Efimenko Dmitry

0.5.8: 2008-01-20
 - Build based on 7Zip 4.57 stable code
 - Added Slovenian translation
0.5.7: 2007-07-26
 - Build based on 7Zip 4.51 beta code
0.5.6: 2007-06-12
 - Build based on 7Zip 4.47 beta code
 - wxCommander extension API support (Unicode)
0.5.5: 2007-02-12
 - Build based on 7Zip 4.44 beta code
 - Updated Danish translation
 - Fixed GPL -> LGPL in the plugin DLL description
0.5.4: 2006-12-25
 - Forgot changing GPL -> LGPL in the configuration dialog title
0.5.3: 2006-12-23
 - Plugin is now released on LGPL license, since GPL was not compatible with TC.
 - Note: From this release plugin is not packed anymore with UPX, if you want
   it packed go to UPX site and pack 7zip.wcx.
 - Build based on 7Zip stable 4.33 beta code
 - New Korean, Catalan, Slovak, Swedish translations
 - EXPERIMENTAL! Passwords pooling. Plugin pools passwords for last 8 files
   so you won't be asked anymore for password when unpacking once opened files.
   This also is related to file packing. Plugin will pack files with last
   pooled password. If archive has crypted headers it will crypt headers for
   updated file. If it hasn't, it won't use password unless you were unpacking
   some crypted file. You need to specify password manualy in the config window.
 - Fix: Can handle passwords when updating files.
 - Fix: Version is properly set in the 7zip.wcx DLL properties (file info).
0.5.2: 2006-07-29
 - Multithreading option added for compression
 - New Swedish translation
0.5.1: 2006-06-02
 - Fix: Release number was wrong (No other changes)
0.5.0: 2006-06-01
 - Fix: Annoying bug that was causing not all files being extracted from archive
 - Build based on 7Zip stable 4.42 code
 - New Danish and Italian translations
0.4.8: 2006-01-18
 - Build based on 7Zip stable 4.32 code
 - New Greek, updated Slovak, alternative Russian translations
0.4.7: 2005-06-30
 - Fix: Plugin will stop & report error when (re)packing locked files
 - Fix: Nested folders were not removed when move to archive was requested
 - Delete function reenabled, delete function won't work for solid archives
 - Build based on 7Zip beta 4.23 code
0.4.6: 2005-05-28
 - Fix: Files & folders were not removed when move to archive was requested
 - Build using VC 2005 Beta 2 (plugin size from 256 to 159 KB reduction)
 - Build based on 7Zip beta 4.19 code
0.4.5: 2005-05-05
 - SFX creation support
 - Translations: Chinese Simpl., Romanian, Ukrainian, Slovak, Hungarian
 - Build based on 7Zip beta 4.18 code
0.4.4: 2005-01-21
 - TC 6.5 autoinstall script
 - Translations: Czech, Chinese, French, German, Polish, Russian, Spanish
 - Language fixes, dialog item sizes
 - Shows packed size (note: this value is for whole stream, not single file !)
0.4.3: 2005-01-18
 - Multilanguage
 - 7zip.ini used for settings
0.4.2: 2005-01-14
 - Archive test is really working now
 - Extracted files are checked against CRC errors
 - Fix: Plugin now stores properly folder information, also empty folders
 - Fix: Valid reaction to [Abort] button, even while seeking in the stream
 - Fix: When extracting one file we don't need pass till the end of the stream
   (faster files extraction if they are far from the archive end)
 - Fix: Deletes source files when "pack move files" is requested
 - Build based on 7Zip beta 4.14 code
0.4.1: 2005-01-12
 - Fix: Multiple compression types now working okay
 - Fix: Copy method is used when compression level is Store
 - Header is compressed always with LZMA
0.4: 2005-01-12
 - Fix: Plugin now informs/checks for CRC errors, bad archive errors
 - New configuration dialog with new settings
 - Password / archive encryption support
 - Multiple compression types and modes (trough configuration)
 - Solid/non-solid archives creation
0.3.4: 2005-01-07
 - Fix: Yet another hopeful fix for freezing (thread synchro)
 - Detect 7zip archive by content (Ctrl+PgDn) including SFX archives
0.3.3: 2005-01-06
 - Fix: Wrong (UTC) filetime displayed in the filelist
 - Fix: Last extracted & zero size file's time was not set properly
0.3.2: 2005-01-06
 - Fix: Unpacking zero file size crash problem fixed
0.3.1: 2005-01-05
 - Fix: Windows 9x freezing issues fixed
 - Raises now E_NOT_SUPPORTED errors when archive cannot be modified due
   need to repacking
0.3: 2005-01-04
 - Packing (LZMA method only)
0.2: 2004-12-30
 - Unpacking (multithreaded working only on W2K)
0.1: (UNRELEASED)
 - Initial Release
 - File list