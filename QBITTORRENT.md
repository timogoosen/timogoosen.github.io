### QBittorrent Notes

Get temporary password:


```

# journalctl -u qbittorrent-nox@qbittorrent -n 80 --no-pager | grep -i "temporary password"
Sep 15 18:31:47 pi-plex-server qbittorrent-nox[6108]: The WebUI administrator password was not set. A temporary password is provided for this session: Hqn2pI27K
Sep 26 18:09:57 pi-plex-server qbittorrent-nox[52206]: The WebUI administrator password was not set. A temporary password is provided for this session: XWuk7gQkK

```

Good general qbittorrent guide for Debian/Ubuntu:

* [Qbittorrent Guide Linux Debian](https://linuxcapable.com/install-qbittorrent-on-debian-linux/)