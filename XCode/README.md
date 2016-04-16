# XCode

Install Xcode command lines for software compiling.

## Installation

1. Install Xcode from MAS or <https://developer.apple.com/xcode/>
2. Open Xcode and agree with `Xcode and iOS SDK License Agreement` or
	
		sudo xcodebuild -license
	
3. Install Xcode command line tools:

		xcode-select --install

*Tip:* Scan available Xcode command line tools:

	ls /Library/Developer/CommandLineTools/usr/bin

## A solution to the slow speed of applications downloading from MAS

1. Use http monitor utility(e.g. `Charles`) capture the hostname of download link && download the application `.dmg` file.
2. Change hosts file: `sudo vim /etc/hosts  ` && bind localhost entry `127.0.0.1` to target link hostname(we got in step 1).
3. Move application `.dmg` file into a temporary folder && start a http service in the folder: e.g. `python -m SimpleHTTPServer 80`, `PHP -S localhost:80`
4. Try downloading application from MAS again.


