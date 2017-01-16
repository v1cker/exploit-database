The Exploit Database Git Repository
===================================

This is the official repository of [The Exploit Database](https://www.exploit-db.com/), a project sponsored by [Offensive Security](https://www.offensive-security.com/).

The Exploit Database is an archive of public exploits and corresponding vulnerable software, developed for use by penetration testers and vulnerability researchers. Its aim is to serve as the most comprehensive collection of exploits gathered through direct submissions, mailing lists, and other public sources, and present them in a freely-available and easy-to-navigate database. The Exploit Database is a repository for exploits and proof-of-concepts rather than advisories, making it a valuable resource for those who need actionable data right away.

This repository is updated daily with the most recently added submissions. Any additional resources can be found in our [binary sploits repository](https://github.com/offensive-security/exploit-database-bin-sploits).

Included with this repository is the **searchsploit** utility, which will allow you to search through the exploits using one or more terms.
For more information, please see the [SearchSploit manual](https://www.exploit-db.com/searchsploit/).

```
root@kali:~# searchsploit -h
  Usage: searchsploit [options] term1 [term2] ... [termN]

==========
 Examples
==========
  searchsploit afd windows local
  searchsploit -t oracle windows
  searchsploit -p 39446

=========
 Options
=========
   -c, --case     [Term]      Perform a case-sensitive search (Default is inSEnsITiVe).
   -e, --exact    [Term]      Perform an EXACT match on exploit title (Default is AND) [Implies "-t"].
   -h, --help                 Show this help screen.
   -j, --json     [Term]      Show result in JSON format.
   -m, --mirror   [EDB-ID]    Mirror (aka copies) an exploit to the current working directory.
   -o, --overflow [Term]      Exploit titles are allowed to overflow their columns.
   -p, --path     [EDB-ID]    Show the full path to an exploit (and also copies the path to the clipboard if possible).
   -t, --title    [Term]      Search JUST the exploit title (Default is title AND the file's path).
   -u, --update               Check for and install any exploitdb package updates (deb or git).
   -w, --www      [Term]      Show URLs to Exploit-DB.com rather than the local path.
   -x, --examine  [EDB-ID]    Examine (aka opens) the exploit using $PAGER.
       --colour               Disable colour highlighting in search results.
       --id                   Display the EDB-ID value rather than local path.
       --nmap     [file.xml]  Checks all results in Nmap's XML output with service version (e.g.: nmap -sV -oX file.xml).
                              Use "-v" (verbose) to try even more combinations
=======
 Notes
=======
 * You can use any number of search terms.
 * Search terms are not case-sensitive (by default), and ordering is irrelevant.
   * Use '-c' if you wish to reduce results by case-sensitive searching.
   * And/Or '-e' if you wish to filter results by using an exact match.
 * Use '-t' to exclude the file's path to filter the search results.
   * Remove false positives (especially when searching using numbers - i.e. versions).
 * When updating from git or displaying help, search terms will be ignored.

root@kali:~#
root@kali:~# searchsploit afd windows local
--------------------------------------------------------------------------------- ----------------------------------
 Exploit Title                                                                   |  Path
                                                                                 | (/usr/share/exploitdb/platforms)
--------------------------------------------------------------------------------- ----------------------------------
Microsoft Windows XP - 'afd.sys' Local Kernel Denial of Service                  | ./windows/dos/17133.c
Microsoft Windows 2003/XP - 'afd.sys' Privilege Escalation (K-plugin) (MS08-066) | ./windows/local/6757.txt
Microsoft Windows XP/2003 - 'afd.sys' Privilege Escalation (MS11-080)            | ./windows/local/18176.py
Microsoft Windows - 'AfdJoinLeaf' Privilege Escalation (MS11-080) (Metasploit)   | ./windows/local/21844.rb
Microsoft Windows - 'afd.sys' Dangling Pointer Privilege Escalation (MS14-040)   | ./win_x86/local/39446.py
Microsoft Windows 7 (x64) - 'afd.sys' Privilege Escalation (MS14-040)            | ./win_x86-64/local/39525.py
Microsoft Windows (x86) - 'afd.sys' Privilege Escalation (MS11-046)              | ./windows/local/40564.c
--------------------------------------------------------------------------------- ----------------------------------
root@kali:~#
root@kali:~# searchsploit -p 39446
Exploit: Microsoft Windows - 'afd.sys' Dangling Pointer Privilege Escalation (MS14-040)
    URL: https://www.exploit-db.com/exploits/39446/
   Path: /usr/share/exploitdb/platforms/win_x86/local/39446.py

Copied EDB-ID 39446's path to the clipboard.

root@kali:~#
```

SearchSploit requires either "CoreUtils" or "utilities" (e.g. `bash`, `sed`, `grep`, `awk`, etc.) for the core features to work. The self updating function will require `git`, and the Nmap XML option to work, will require `xmllint` (found in the `libxml2-utils` package in Debian-based systems).
