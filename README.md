# starview
A simple no-frills windowing + management enviroment influnced by SunView.

## Usage
starview is simply started via the command `starview`. However, due to
partly a choice of not using conventions expected of today's GUI's and
due to design choices to ensure a unusally small size (target platforms 
do include several m68k machines, dreamcast, acorn RISC-PC, late-model 
VAX systems, i386 +, m88k, & possibly all of the total systems that the
current BSD's support that do support graphics & have at least 10MB), starview may not handle 
like you'd expect it to:

	* what would be commonly called a window is a frame here.

	* Only two titlebar buttons on each side, depending upon what mouse- 
	button you press:

		*left corner: right- close, left- iconify.

		*titlebar: right- move, left- resize.

		*right corner(may be absent in some versions): right- push back on
		z-order; left- push fowards on z-order.

	* much of the included apps (excluding terminal) don't use a main or 
	context menus, said functionalty expected from menus may be found in
	the toolbar-like application rows.

	* not much in the way of persionalation, the only options are 
	foreground & background hues.

	* the inabilty to resize windows beyond the left & top sides of the 
	screen.

	* resizing will relocate the cursor to the lower right corrner of the 
	frame.

	* In line with older systems, but not modern ones usally- resizing & movement
	are indicated via a outline.

	* A noticable lack of colors expect black & white, this is on purpose and for
	1-bit graphics using systems. Implemtations on color-using systems can have the
	widgets use their own background & foreground colors as needed.

### Included apps

The applications found in with a standard install of starview are:

	* Edd: the text editor.

	* Espy: the sunOS Organizer-esque file manager.

	* Terminal: the terminal emulator.

	* veh: feh-like image-viewer. Can use color on systems that use it.

	* SheetCalc: Very-no-frills spreadsheet app.

	* edvis: the starview pixmap editor.

	* rake: simple music tracker on systems that support sound.

	* pig: I/O pin peeker & poker on systems with user-accesable GPIO pins.

	* hyperbole: general purpose visual markup viewer, includes support for:

		- HTML on par with netscape 2.0 + tables.

		- genimani.

		- markdown.

	* parcel: the mail(1) & email client + viewer.

	* heat: CPU usage history, GPU usage history, RAM usage history, 
	storage usage history, network usage history, & heat indicator.

	* runlist: active applications list.

	* scorch: application terminator akin to xkill.

	* visxit: Visual session exit wizard, can be canceled.

## Configuration
Starview is configured in a manner not unlike sunview, in using a `.starview` file found
in the user's directory that has a mostly simular synthex that's easier to remember.

Avaible options are:

	* Background(mandatory on color systems):

	* Foreground(manadatory on color systems):

	* RootFrameBg(optional on color systems): Background color seprate from the 
	main background color.

	* RootFrameFg(optional on color systems): Foreground color seprate from the 
	main foreground color.

	* ShadowBg:

	* ShadowFg:	

	* Inverted: Inverts the background and foreground colors.

	* RootFramePixmap: The pixmap to use with the root-frame.

	* ShadowPixmap: the pixmap for the shadows to use.

	* titleFont: Font used for titlebars.

	* appFont: Default font used for applications & menus.

	*

	* action button(can be excluded from view):

		*function1: shrink

		*function2: close

	* Titlebar:

		*function1: move

		*function2: resize

	* thruster(can be excluded from implemation):

		*function1: lower

		*function2: arise

## Developing for starview
As said with using starview, devloping apps for it is not what you had encounted
before, while it's somewhat more simple, it is a fair amount more constrained if
you are using built in functions:

	*All aplications include a static icon, said icon is shown by espy or on the root-
	frame when shrunk..

	* an rather bare-bones included widget set, while the included libs 
	allow for custom widgets, said built-in widget set is small in amount
	mainly for the least amount of disk-space:

		* button: it can have one item in it (usually a label or image). can 
		have but not recomended to have diffent actions depending upon what 
		mouse button was pressed.

		if needed (but not recomended usually), a button can not show a frame
		around it (that also includes the shadow), pressing on it inverts the 
		widget area, the button's disabled apperance is slightly "grey"ed out.

		Starview's interactive bits of the frames are composed of frameless
		buttons.

		* label: is much like the commonly expected label widget.

		label is expected to be the most inherented built-in widget aside from
		the hover-labels that also use it. it can have the text justifcations
		of:

			-left

			-center

			-right

		* image: like label, but in place of text- a specified pixmap. Has the
		following options:

			-none: Don't repeat

			-tile: Do repeat

		starview's root-frame background uses a repeating image.

		* hover-label: used by many of the widgets for context help on hover,
		it is much like what's found on other platforms.

		* text-field: a area outlined by a black rectangle that can have 
		user-input text entered into it. it's disabled apperance is 
		indisguisable from a disabled frameless button.

		* view-area: the widget most expected to be extended via non-included
		widgets. It can show items in:

			-coloumns

			-rows

			-rows overflowing into coloumns 'flowrow'

		if desired, the view-area can be set to have item-wraping by the dev or
		the user.

		* slider: sliders & scrollbars are the one & the same in terms of how they 
		are programed and their apperance in starview. can be set with:

			-width

			-slider size

		* menu: Is much like the modern expected behavior of a menu. can be summoned
		by right mouse button clicks or widget buttons.

		* tables:

## Modfying & compiling starview

