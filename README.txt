Remember garbage in, garbage out. Make sure your setting your commandline arguements properly. This script does do some error checking but will run if you supply it with information that is invalid such as vista discovery login, vista discovery logout, vmart zone , vmart hostname etc, however when it gets to them steps will fail out. If you do not supply a zipfile name (-f) on the command line, the script will skip the unzip step.


This command takes in a list of commandline arguements and executes all the commands to do an activation. The command line functions are as follows:

  -s This sets the subset. Use dlci subset name ie NEW_SET_7.1
  -b This sets the datacenter. use austin or AUSTIN, allen or ALLEN -- wont need after migration
  -f This sets the zip file name to extract. use the name that is in dlci.(OPTIONAL, - script will continue without it.)
  -z This sets the vistamart zone. 
  -u This sets the vista discovery login. This is used in vistadiscovery ex: pnoc_operator
  -p This sets the vista discovery password. This is used in vistadiscovery 
  -n This sets the hostname that is used in vista discovery. Use the ip, or server dns name.
  -c This sets the customer. ec: Cbeyond. if your customer has a space in it, put it in " " -- rework unzip then wont need.
  -e This sets the external interface. by default is eth1. (OPTIONAL)  
  -t This sets the port number for vista discovery default is 11080 (OPTIONAL)  
  
  
todo:
  -- add a -O for override function, and run an activation with commandline arguements. -- menu?
  -- add option -G to generate a config file for a customer, and use that for the activation 
  -- add -D option for deleting devices. use the other script i have and make a wrapper around it to take ips from a file.
   * use kashifs script, and idea about using an csv spreadsheet to get the information to generate the conf file.
  -- add lockfile function for vistadiscovery and ciscodiscovery.
   * important to maintain control of the execution flow. 
   * add a function to work with lockfile function to delete lockfile if <CTRL>C is entered.
  -- add subroutine to check if any of the variables are not set,ie: to pick up where it left off the last time
  -- add robustness and some kind of error checking to check if autodiscofile variable is set or not(see latest())
  -- add a function to validate CiscoDiscovery.config
  -- check Ciscodiscovery.config
    
  
   
   -d for if the activation is resuming after being killed -d(? maybe) will signify the data directory ( unzip dir )
 
 
 -------------------
 
  --bug: 05:18:02   [VD-E02202] Error during the discovery in SourcePort processor: error creating the datagram socket [E-0: java.net.BindException].
    -- the zone was not set properly, and caused VDisc to throw this error, but the script continued to execute. not sure what to do about this
    
   -bug: output from time did not get saved in the tee output. need to figure out how to force this info into a log file so we can parse it