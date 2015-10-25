#XCode

Install Xcode command lines for software compiling.

Steps:

1. Install Xcode from MAS or <https://developer.apple.com/xcode/>
2. Open Xcode and agree with `Xcode and iOS SDK License Agreement` or
	
		sudo xcodebuild -license
	
3. Install Xcode command line tools:

		xcode-select --install

Scan avaliable Xcode command line tools:

	ls /Library/Developer/CommandLineTools/usr/bin

**Tip:** Solution for slow MAS application download speed:

1. Use http monitor utility(e.g. Charles) capture download link & download application dmg by download utility(e.g. wget, aria2c).
2. Cli: `sudo vim /etc/hosts  ` & bind localhoal 127.0.0.1 to link hostname(we get in step 1).
3. Move application dmg to temporary folder & run http serve in the folder: e.g. `sudo python -m SimpleHTTPServer 80`
4. Download application from MAS again
