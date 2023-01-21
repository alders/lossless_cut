# lossless_cut

The Lossless Cut userjobs are used in conjunction with MythTV's commflag and editing UI to create loss less cut mkv video files. Lossless Cut supports multiple video, audio encoding types and subtitles formats. For full details see R.D. Vaughan: https://www.mythtv.org/wiki/Lossless_Cut

Source is compatible with mythtv fixes/32(v32.0-81-ge74f587d1f) running on Fedora release 37.

It is recommended to force the use of mythccextractor by adding the "-X" as a command line parameter to a Lossless Cut user job e.g.:

```bash
/usr/bin/lossless_cut -X -f "%DIR%/%FILE%" -e
/usr/bin/lossless_cut -X -f "%DIR%/%FILE%" -r
```

The userjobs are known to use a lot of memory. Using my 16GB ram machine, this sometimes becomes a problem when converting files larger than 10 GB.

Keep an eye on the memory usage with:
```bash
$ free -h
               total        used        free      shared  buff/cache   available
Mem:            15Gi       1.3Gi        10Gi        74Mi       4.0Gi        13Gi
Swap:          8.0Gi       384Mi       7.6Gi
```

A contab to free your memory may be helpful:
```bash
$ cat freemem.sh
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
$ crontab -l
*/15 * * * * freemem.sh
```

happy converting
