Note:
This is the flatpak-builder yaml manifest for packing the AnycubicSlicerNext 
build for Ubuntu 24.04 to be usable on other distributions. The only 
distribution on which it's being tested is Arch with the latest updates at 
the time of manifest release. This is loosely based on a Orca's manifest.

Any pull request will probably be completely ignored. Copy it, fork it, do 
whatever you like. If it doesn't work for some reason, there is a page
dedicated for that: https://docs.flatpak.org/en/latest/introduction.html

Anycubic released the GNU/Linux version of their fork of Orca slicer for
Ubuntu 24.04 amd64, published on their repo. The repo Release file is 
available at
https://cdn-universe-slicer.anycubic.com/prod/dists/noble/main/binary-amd64/Packages

Usage example:
- buld:
  flatpak-builder --force-clean --user --install-deps-from=flathub --repo=repo --keep-build-dirs  build-dir com.anycubic.slicernext.yaml
- test run:
  flatpak-builder --run build-dir com.anycubic.slicernext.yaml AnycubicSlicerNext
- bundle build:
  flatpak build-bundle repo AnycubicSlicerNext.flatpak com.anycubic.SlicerNext
- bundle install:
  flatpak install AnycubicSlicerNext.flatpak  

Notes:
- for v1.3.7171 gnome platform runtime version v46, slicer won't run when installed as bundle (but will work just fine in test run) and reports
```  
[0x000074461b5a1480] [trace]   Initializing StaticPrintConfigs
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
```
bumped gnome platform back to the v47, where installed bundel works as planned.
- uniinstall could be needed by executing the 
```
flatpak uninstall com.anycubic.SlicerNext
```
that just removes the binary, setting should be preserved after installing corrected bundle
