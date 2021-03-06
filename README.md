# MSG Convert

A perl script to convert Outlook .msg files in to .eml files to read on Ubuntu Linux using Thunderbird.

Originally by Matijs van Zuijlen [matijs@matijs.net](mailto:matijs@matijs.net)    
Later edits by Craig Russell [craig@craig-russell.co.uk](mailto:craig@craig-russell.co.uk)

## Usage Instructions

1. Install the required perl packages with the following commands    

        sudo perl -MCPAN -e 'install("Email::Outlook::Message")'
        sudo perl -MCPAN -e 'install("Email::LocalDelivery")'
        sudo perl -MCPAN -e 'install("Getopt::Long")'
        sudo perl -MCPAN -e 'install("Pod::Usage")'
        sudo perl -MCPAN -e 'install("File::Basename")'
    
2. Install Thunderbird (if you don;t already have it) with `sudo apt-get install thunderbird`

3. Download and save `msgconvert.pl` to your computer

4. Make it executable with `chmod +x /path/to/msgconvert.pl`

5. Open .msg files with `/apth/to/msgconvert.pl /path/to/emailfile.msg`    

You can configure Nautilus to open `.msg` files when you double-click them    

1. Right click any .msg file

2. Select *Open with Other Application*

3. Click the arrow next to *Use a Custom Command*

4. Click the *Browse* button and choose the `msgconvert.pl` file

Now when you double click a `.msg` file, it will be automatically converted to a `.eml` file and opened in Thunderbird.

## Options
`msgconvert.pl [options] <file.msg>...`

###--mbox
`--mbox <file>`     
Deliver to the given mbox file instead of creating individual `.eml` files.

###--exec
`--exec <command>`      
After creating output files, run the specified command with each
output file as a parameter
e.g. `msgconvert.pl --exec thunderbird input.msg`

###--verbose
`--verbose`     
Print information about skipped parts of the .msg file.

###--help
`--help`        
Print a brief help message.

## Note

By default the script will open the converted files with thunderbird, you can over ride this with the `--exec` option.
Preferably the script would by default use no application, but Nautilus doesn't allow you to specify options for 'open with' scripts.
If you'd rather have no default application, simply change the parameter on line 19 from `my $execute = 'thunderbird';` to `my $execute = '';`
