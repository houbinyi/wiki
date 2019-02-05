''rsync [OPTION]... SRC [SRC]... DEST''
''rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST''
''rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST''
''rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST''
''rsync [OPTION]... [USER@]HOST:SRC [DEST]''
''rsync [OPTION]... [USER@]HOST::SRC [DEST]''
''rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]''

''$ rsync -avz user@host:/remote/path/ /local/path/''

--progress --delete 
