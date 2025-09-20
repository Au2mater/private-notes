- `obsidian://open?vault=my%20vault`  
    This opens the vault `my vault`. If the vault is already open, focus on the window.
    
- `obsidian://open?vault=ef6ca3e3b524d22f`  
    This opens the vault identified by the ID `ef6ca3e3b524d22f`.
    
- `obsidian://open?vault=my%20vault&file=my%20note`  
    This opens the note `my note.md` in the vault `my vault`, assuming the file exists.
    
- `obsidian://open?path=%2Fhome%2Fuser%2Fmy%20vault%2Fpath%2Fto%2Fmy%20note`  
    This will look for any vault that contains the path `/home/user/my vault/path/to/my note`. Then, the rest of the path is passed to the `file` parameter. For example, if a vault exists at `/home/user/my vault`, then this would be equivalent to `file` parameter set to `path/to/my note`.