### Raster Scan
- electron beam swept across the screen one row at a time from top-to-bottom
	  beam intensity turned on and off to create a pattern of illuminated spots
- picture definition stored in an area called **refresh buffer** or **frame buffer**
	  stores set of intensity values for all screen points
	  stored values retrieved and painted onto the screen
- eg : TV and Printer
- for bi-level system where intensity value is 1 or 0, only 1 bit is needed to indicate that the beam intensity should be off or on
- ![[Pasted image 20250429000827.png]]
- **horizontal retrace** : return to left of screen after refreshing every scan line 
- **vertical retrace** : return to top left of screen at the end of each frame

### Random Scan
- CRT direct electron beam to only the **parts** of screen where picture is to be **drawn** 
- draw picture one line at a time, thus called **vector displays** 
- refresh rate depends on **number of lines** to be displayed
- picture definition stored as **set of line drawing commands** in area of memory called **refresh display file** 