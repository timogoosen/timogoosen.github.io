## OSX Notes

Here are my notes for upgrading OSX if you have a very tiny hardrive.

## Major OSX Update

If it is a major update then:

Download Big Sur and write to external drive with 

* [Download Big Sur Update to external Drive](https://support.apple.com/en-za/HT201372)

```
sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume

```

Free up space with tips/ideas from this thread: 
* [Free Up Space on Mac Ideas Thread](https://developer.apple.com/forums/thread/650026?page=2)

If you use docker and dont mind rebuilding your images run this:

```
docker system prune -a

```


Delete local timemachine backup snapshots: (Just reboot afterwards to actually see the freed up space):

```

sudo tmutil deletelocalsnapshots /

```

Then run Big Sur installer from installer
PS: Remember to make a backup with time machine backup to external before upgrading just for in case

