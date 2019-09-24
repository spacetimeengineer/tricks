Bash Tricks
===========

1.) locate: Description: Lists all files with permission that contain string.
        
      $ locate <String>

      $ locate -i <String> | less

      $ locate -i -n <QuantityOfListItems> <String>
    
2.) grep:
        
      # Lists highlighted instances of <String> within <File> in a cat type format.
      $ grep <String> <File>

      # Lists highlighted instances of <String> within multiple files in a cat type format.
      $ grep <String> *

      # This searches for any occurence of "string" in /path.
      $ grep -rl "string" /path
        

3.) find: Lists all files in directory with <StringWithinFileName> contained in it's file name.

      # Lists all files in directory with <StringWithinFileName> contained in it's file name.
      $ find -name "*<StringWithinFileName>*"

