Note:
This is the flatpak-builder yaml manifest for packing the AnycubicSlicerNext 
build for Ubuntu 20.04 to be usable on other distributions. The only 
distribution on which it's being tested is Arch with the latest updates at 
the time of manifest release. This is loosely based on a Orca's manifest.

Any pull request will probably be completely ignored. Copy it, fork it, do 
whatever you like. If it doesn't work for some reason, there is a page
dedicated for that: https://docs.flatpak.org/en/latest/introduction.html

Anycubic released the GNU/Linux version of their fork of Orca slicer for
Ubuntu 20.04 amd64, published on their repo. The repo Release fie is 
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

