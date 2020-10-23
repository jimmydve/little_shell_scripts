## Little useful shell scripts

Here's the --help for each shell script:

### 7ze

	usage: 7ze file [archive.zip]
	
	    Add 'file' to AES256 enctrypted archive.
	    If the name of the archive is not given then
	    'file.zip' will be used as archive name.
	
	    Archive with file encrypted in this way should
	    be compatible with windows.
	
	    7ze will ask for the password.
### ansible-vault-rgrep

	usage: ansible-vault-rgrep [-H] directory [GREP_PARAMS]
	       ansible-vault-rgrep --help
	
	   Recursively grep ansible vault files.
	
	   -H    prefix each match with the filename
	
	   You should either set `DEFAULT_VAULT_PASSWORD_FILE`
	   or set `vault_password_file` in your ansible
	   config file, otherwise ansible-vault-rgrep will
	   be hardly useful.
	
### bash_aliases

	These bash_aliases need to be called from ~/.bashrc or similar like this:
	
	    . /path/to/this/bash_aliases
	
	They provide the following commands:
	
	    ackp      - execute "ack --pager="less -R""
	    df        - execute "df -h"
	    du        - execute "du -h"
	    bc        - allow for calculations with decimal places by default in bc
	    hg        - grep shell history
	    hl        - page shell history
	    pg        - grep processes
	    rgl       - rgrep regex | less
	    rgp       - execute "rg --color=ansi | less -R"
	    rgpc      - execute "rg --color=ansi -C 25 | less -R"
	    aps       - execute 'ansible-playbook setup.yml'
	    apst      - execute 'ansible-playbook setup.yml --tags='
	    apsv      - execute 'ansible-playbook setup.yml \
	                         --vault-password-file ~/vault_from_gpg_agent.py
	    apstv     - execute 'ansible-playbook setup.yml \
	                        --vault-password-file ~/vault_from_gpg_agent.py \
	                        --tags='
	
	    apt-find file - say which Debian package contains "file"
	                    needs apt-file
	
	Shortcuts to put firefox, chrom(e|ium) or thunderbird to rest.
	Requires {firefox,thunderbirf,chrome}-sleep/wake
	
	    chs, chw, ffs, ffw, ths, thw
	
	git shortcuts
	
	    g    - status
	    gd   - diff
	    ga   - add
	    gac  - add and commit, commit msg is optional
	    gc   - commit
	    gca  - commit -a
	    gcam - commit -a -m
	    gci  - commit --interactive
	
	chmod shortcuts (not available in zsh)
	
	    +x  file
	    +r  file
	    +w  file
	    a+x file
	    a+r file
	    a+w file
	
	change directory
	
	    cdreal  file - chdir to wherever the file is located
	    cdwhich file - chdir to wherever the executable is located
	    mcd     name - make directory and cd into it
	    mcdt         - make temporary directory and cd into it
	    mcptmp  file - make temporary directory, cp given file into it
	                   and cd into the tmp dir. Supports the same
	                   options as cptmp.
	
### brightness

	usage: brightness [--show|percent]
	
	    set or show panel brightness on intel chips in percent (default is 60%)
	
### bromium

	usage: bromium [--enable-cookies] [--userdir /path/to/userdir] [URL]
	       bromium --help
	
	    Run chromium with an empty temporary profile
	    or with a given directory.
	
	    By default bromium will run in "incognito"
	    mode. If you want to allow cookies then
	    use --enable-cookies
	
	    If you are using bromium as a privacy tool
	    then you may want to consider changing your
	    default search provider. See
	    https://stackoverflow.com/a/50888866
	
	    --enable-cookies  - do not run in incognito mode
	
	    --userdir $DIR    - run from a given user directory. This
	                        can be used to prepare a specific
	                        configuration for a specific application
	                        and then use that directory only for that
	                        application.
	                        When run with --userdir, cookies will
	                        be *enabled*.
	
	    How to prepara a special userdir:
	
	    1. terminate all chromium browser
	    2. move your original chromium configuration to the side
	       `mv ~/.config/chromium ~/.config/chromium.your-original-config`
	    3. start chromium
	    4. configure whatever you need
	    5. terminate chromium
	    6. move the config to the side
	       `mv ~/.config/chromium ~/.config/chromium.my-special-config`
	    7. restore your original config
	       `mv ~/.config/chromium.your-original-config ~/.config/chromium`
	    8. now you can use your special config with bromium
	       `bromium --userdir ~/.config/chromium.my-special-config $SOME_APPLICATION_URL`
	
### catnamed

	usage: catnamed file ...
	
	    print name of file and then cat it
	
### cat_null_terminated

	usage: cat_null_terminated file
	       cat_null_terminated --help
	
	   When file contains "lines" or "items" separated
	   by null values, then cat_null_terminated will
	   replace those nulls with line breaks and `cat`
	   the file out
	
	   Many special files under /proc contain such
	   null-separated lines.
	
	   see https://unix.stackexchange.com/a/29132
	
### catwhich

	usage: catwhich executable
	
	    cat executable that is somewhere in $PATH
	    or can be located via "locate"
	
### cert-fingerprint

	usage: cert-fingerprint certificate.crt
	       cert-fingerprint --help
	
	    print fingerprint of x509 certificate
	
### cert-server-add

	usage: cert-server-add remote.host.name [port]
	       cert-server-add --help
	
	    connects to server, retrieves its certificate and
	    adds it to the local system's trusted certificates
	
	    ATTENTION:
	
	        * No checks on the retrieved certifica are done,
	          f.ex. if it claims to be a CA certificate etc.
	
	        * the certificate is put under /etc/ssl/certs/,
	          which is probably not entirely compatible
	          accross all distributions
	
### cert-show

	usage: cert-show (--help|certificate|--host host:port [--smtp|--postgres])
	
	    print all kinds of certificates
	
### cert-show-all

	usage: cert-show-all [--debug] [certificates.crt]
	       cert-show-all --help
	
	    print all certificates contained in certificates.crt chain
	
	      --debug   include original encoded certificates in printout
	
### changelog

	usage: changelog
	
	    edit the user's system changelog
	
### chrome-sleep

	usage: chrome-sleep
	
	    suspend all chrome/chromium processes
	
	    Note: it's advisable to add an 'alias chs=chrome-sleep'
	
	    See also: chrome-wake
	
### chrome-wake

	usage: chrome-wake
	
	    wake up all chrome/chromium processes
	
	    Note: it's advisable to add an 'alias chw=chrome-wake'
	
	    See also: chrome-sleep
	
### chromium-create-private-profile

	usage: chromium-create-private-profile SHORTCUT URL
	       chromium-create-private-profile --help
	
	   PURPOSE:
	
	   Will create a clean, private, dedicated profile for
	   a web site that you can call from the command line
	   via shortcut.
	
	   DETAILS:
	
	   Will create an executable under ~/bin/SHORTCUT that
	   will use a clean, private chromium config and data
	   directory under ~/.local/chrome-SHORTCUT.
	
	   You can customize ~/bin/SHORTCUT as you wish.
	   By default it will use `bromium --enable-cookies`
	   to access the given URL.
	
	   The ~/.local/chrome-SHORTCUT directory will
	   be created (copied) from the
	   ~/.config/chromium.fresh-after-start.with_titlebar
	   template.
	
	   You will need to create the
	   template ~/.config/chromium.fresh-after-start.with_titlebar
	   once and can use it after with
	   chromium-create-private-profile. Create the template
	   as follows:
	
	     * `mv ~/.chromium ~/.chromium.original`
	       (do not overwrite a previously existing
	        ~/.chromium.original !)
	     * `chromium` # will create a fresh ~/.chromium
	     * configure chromium as you wish
	     * terminate chromium
	     * `mv ~/.chromium ~/.config/chromium.fresh-after-start.with_titlebar`
	     * `mv ~/.chromium.original ~/.config/chromium`
	       (restore original chromium config)
	
### copy_args_to_clip

	usage: copy_args_to_clip arg1 arg2 ...
	
	    copy arguments to clipboard (CTRL-V)
	
	    if no argument is given, then copy stdin to clipboard
	
### copy_args_to_file

	usage: copy_args_to_file file_name arg1 arg2 ...
	
	    copy arguments to file
	
	    if no argument is given, then copy stdin to clipboard
	
### copy_file_to_clip

	usage: copy_file_to_clip [file]
	
	    copy file to clipboard (CTRL-V)
	
	    if no file is given, copies stdin
	
### copy-resolv-conf

	usage: copy-resolv-conf destination_machine
	       copy-resolv-conf --help
	
	    Copies your /etc/resolv.conf over to the destination_machine
### copy_sel_to_clip

	usage: copy_sel_to_clip
	
	    copy selection (mouse select) to clipboard (CTRL-V)
	
### copy_stdin_to_file

	usage: copy_stdin_to_file file_name
	
	    copy input to file
	
### cptmp

	usage: cptmp [--dir] [opts] file
	
	    copy given file to /tmp/foo.XXXXX
	
	    cptmp accepts the same arguments as cp
	
	    --dir   /tmp/foo.XXXXX will be a directory
	
### executable_wrapper

	usage: executable_wrapper (unwrap|wrap|test) executable
	
	    This script is used to wrap executables in order to
	    analyse how they are called by other scripts, daemons etc.
	
	    The original file will be renamed to `executable.orig`.
	
	    It will log all parameters and the environment of the
	    originally called executable to a log file for inspection.
	    The log file will be called `/tmp/executable.log.XXXXXX`,
	    where 'XXXXX' will be some random string.
	
	      wrap   - wrap the given `executable`
	
	      unwrap - unwrap the given `executable`
	
	      test   - test this script
	
### exif-del

	usage: exif-del image
	
	    remove all meta-tags from exif informations
	
### file_extension

	usage: file_extension [--lowercase|--uppercase] file_path
	
	    print file extension of given file
	
### findhere

	usage: findhere SEARCH_STRING [OTHER_FIND_OPTIONS]
	
	    will execute "find . -name "*SEARCH_STRING*" [OTHER_FIND_OPTIONS]"
	
### find_ls_sort

	usage: find_ls_sort [--help]
	
	    A fusion of find and ls. Very useful for comparing systems.
	
### firefox-sleep

	usage: firefox-sleep
	
	    suspend all firefox (and plugin) processes
	
	    Note: it's advisable to add an 'alias ffs=firefox-sleep'
	
	    See also: firefox-wake
	
### firefox-wake

	usage: firefox-wake
	
	    wake up all firefox (and plugin) processes
	
	    Note: it's advisable to add an 'alias ffw=firefox-wake'
	
	    See also: firefox-sleep
	
### heat.sh

	usage: heat.sh
	
	    run infinite loop that will consume 100% of a CPU core
	
	    Useful for fan and temperature regulation testing
	
### host_only_ip

	usage: host_only_ip hostname
	       host_only_ip --help
	
	       Same as `host`, but will return IP address only.
### kernelog

	usage: kernelog
	
	    Will jump to the end of /var/log/kern.log, page it with
	    'less' and update it when it changes.
	
### konsole_fork_ssh

	usage: konsole_fork_ssh
	       konsole_fork_ssh --help
	
	    Fork a konsole tab that is running a ssh session.
	
	    The idea is to bind this program to a key-combination
	    and press the respectiv key while working inside konsole.
	
	    When the currently active tab is running a ssh session,
	    konsole will open a new Tab and execute ssh to the same host.
	
### linechop

	usage: linechop
	       linechop --help
	
	    chop lines of at right margin of the screen
### mairi

	usage: mairi _search _parameters
	
	    mairi searches your mail and displays results in mutt
	
	    mairi is a simple wrapper around mairix and mutt and accepts
	    the same parameters as mairix
	
### mcdts

	usage: mcdts
	       mcdts --help
	
	   Open shell in new temporary directory, delete directory after exit
	
### meetjitsi

	usage: meetjits [handle]
	       meetjits --help
	
	   Will start bromium on the given Jitsi Meet
	   channel.
	
	   You can configure your channels like this:
	
	       $ cat ~/.meetjitsi.yaml
	       urls:
	         default:  https://meet.jit.si/example-default
	         myown:    https://meet.jit.si/example-myown
	
	   Jitsi Meet uses 4000 - 6000kbps.
	
### modinfo_all

	./modinfo_all : list information on all currently installed kernel modules
	./modinfo_all --desc : list only description of each module
### mount_encrypted

	usage: mount_encrypted [options] image [mountpoint]
	
	    see also umount_encrypted
	
	    if mountpoint is not provided mounts under /media/image
	
	    --ro     mount read only
	
### mount_iso

	usage: mount_iso iso_image destination
	       mount_iso --help
	
### mv_ln

	usage: mv_ln src_ln dest_dir
	       mv_ln --help
	
	  Move the symbolic link src_ln into dest_dir while
	  keeping it relative
### psa

	usage: psa [-w] [pattern]
	
	    Show all processes in full detail (ps faux) excluding kernel
	    processes. If a pattern is given, then the process list is
	    grep'ed with that pattern.
	
	    psa will by default chop off long lines.
	
	    -w    wrap lines instead of chopping them off
	
	    psa depends on the linechop tool.
### psql_access_priv_decoder

	usage: psql_access_priv_decoder
	       psql_access_priv_decoder --help
	
	   Will decode access privileges displayed by psql
	
	   How to use:
	
	     1. in `psql` do `\l accounting` or such to list the database "accounting".
	     2. copy the output including the header
	     3. start psql_access_priv_decoder
	     4. paste
	     5. CTRL-D
	     6. you will get the access privileges in human readable form displayed
	
	   Example:
	
	     $ psql
	     postgres=# \l accounting
	                                                List of databases
	          Name     |   Owner    | Encoding |   Collate   |    Ctype    |     Access privileges    
	     --------------+------------+----------+-------------+-------------+--------------------------
	      accounting   | henry      | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =T/postgres             +
	                   |            |          |             |             | henry=CTc/postgres      +
	                   |            |          |             |             | alice=c/postgres
	
	     $ psql -c "\l accounting" | psql_access_priv_decoder
	     "=T/accounting" means:
	       role "postgres" allowed "PUBLIC" to:
	         T -- create TEMPORARAY tables while using the DB
	
	     "henry=CTc/accounting" means:
	       role "postgres" allowed "henry" to:
	         C -- CREATE new tables/schemas
	         c -- CONNECT to DB
	         T -- create TEMPORARAY tables while using the DB
	
	     "alice=c/accounting" means:
	       role "postgres" allowed "alice" to:
	         c -- CONNECT to DB
	
### reset_usb_devices

	usage: reset_usb_devices
	
	    resets all USB devices that the script finds
	
### select_lines

	usage: select_lines (only-left|only-right|in-both) left_file right_file
	       select_lines --help
	
	   Depending on first argument will emit a list of
	   lines that are either only in the left, the right
	   or in both files.
	
	   (The script will create sorted temporary copies
	    of both files...)
	
	    Thanks to mr.spuratic in https://stackoverflow.com/a/18205289
	
### show_csv

	usage: show_csv [file.csv] [separator]
	       show_csv --help
	
	    pretty print and page CSV file with 'less'
### show_rh_updates

	usage: show_rh_updates [--help]
	
	    shows current and new version of packages that would get
	    updated.
	
### ssh-host

	usage: ssh-host [host]
	
	    Host lookup inside ~/.ssh/config. If no host
	    is given then output the whole ~/.ssh/config file.
	
	    This script is most useful together with bash
	    completion:
	
	        _ssh_host()
	        {
	            local cur prev words cword
	            _init_completion -n = || return
	            _known_hosts_real -a -F ~/.ssh/config "$cur"
	        } && complete -F _ssh_host ssh-host
	
### ssh-update-config

	usage: (ssh-update-config|ssh-update-config-template)
	
	    Construct a new ~/.ssh/config from ~/.ssh/config.d.
	    A backup of the current ~/.ssh/config is done
	    automatically.
	
	    If called as `ssh-update-config` then:
	
	      * ~/.ssh/config.d/* is `cat`ed together and
	        the result used as ~/.ssh/config
	
	    If called as `ssh-update-config-template` then:
	
	      * ~/.ssh/config.d/main.template is
	        `source`d instead and the result written to
	        ~/.ssh/config
	
	    ssh-update-config requires the `versioned_backup`
	    script
### switch_off_radeon

	usage: switch_off_radeon
	
	    tries to switch off the heat producing Radeon VGA card
	
### thunderbird-sleep

	usage: thunderbird-sleep
	
	    suspend all thunderbird processes
	
	    Note: it's advisable to add an 'alias tbs=thunderbird-sleep'
	
	    See also: thunderbird-wake
	
### thunderbird-wake

	usage: thunderbird-wake
	
	    wake up all thunderbird processes
	
	    Note: it's advisable to add an 'alias tbw=thunderbird-wake'
	
	    See also: thunderbird-sleep
	
### to_jpg

	usage: to_jpg image.png [image.jpg]
	
	    transform png image to jpg format
	
### umount_encrypted

	usage: umount_encrypted mountpoint
	
	    see also mount_encrypted
	
### versioned_backup

	usage: versioned_backup filename [.file_extension]
	
	    makes a versioned backup of filename. If provided
	    then the version number will be inserted before the
	    .file_extension
	
	    Example:
	
	    $ ls
	    foo
	    $ versioned_backup foo
	    $ ls
	    foo
	    foo.0001
	    $ versioned_backup foo
	    $ ls
	    foo
	    foo.0001
	    foo.0002
	    $ touch bar.mp3
	    $ versioned_backup bar.mp3 .mp3
	    $ ls
	    foo
	    foo.0001
	    foo.0002
	    bar.mp3
	    bar.0001.mp3
### vimgrep

	usage: vimgrep (REGULAR_EXPRESSION|rg_option)+
	       vimgrep --help
	
	    will:
	      - use ripgrep (`rg`) to grep files
	      - display the result
	      - ask for confirmation
	      - edit the files with vim
	
	    You can set the VVV environment variable to
	    set options for vim:
	
	        VVV=-o vimgrep foo
	
	    Attention: this will run `rg` twice
	
### vimn

	usage: vimn file:n
	
	    edit file and jump to line 'n'
	
### vimtmp

	usage: vimtmp
	
	    create a /tmp/foo.XXXXX file and edit it
	
### vimwhich

	usage: vimwhich
	
	    edits executable that is somewhere in $PATH
	    or can be located via "locate"
	
### vimx

	usage: vimx [params] file
	
	    create and edit executable bash script
	    that has a --help command
	
### vimxb

	usage: vimx [params] file
	
	    create and edit executable bash script under ~/bin
	
	
### wake-sleep-log

	usage: wake-sleep-log
	       wake-sleep-log --help
	
	  searches /var/log/kern.log for power management events
	  and displays a list when the machine went to slee and
	  woke up again
	
### whois_ip

	usage: whois_ip IP
	       whois_ip --help
	
	    will to a DNS lookup and a whois lookup on an IP
	    and filter out the relevant fields. Used for
	    as a help tool for manually dropping spammer IPs
	    and networks into a firewall
### window

	usage: window kill
	       window --help
	
	    lets you visually select a window and then
	    depending on the command given:
	
	    kill: will send SIGTERM and then SIGKILL to
	          the process
	
	    pressing ESC while in selection mode will
	    abort the action
	
### wping

	usage: wping [URL]
	
	    retrieves website via HTTP in order to see whether the web/internet
	    works. Default site is http://sourcepole.ch
	
### zuletzt

	usage: zuletzt
	       zuletzt --help
	
	       'zuletzt' means 'last time' in German. It will
	       play the next multimedia file.
	
	       Do create a file ZULETZT which contains:
	
	         1600_##.mp3
	         0
	
	       Then call `zuletzt` and it will play the
	       file 1600_01.mp3 and increase the '0' to '1'
	       after having successfully played the file with
	       mpv.
	
