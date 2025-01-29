# Virt Manager QEMU extension

This is a "separate" project from the main `virt-manager` flatpak aiming to give proper QEMU support for the virt-manager flatpak, including tools like `virtiofsd` and whatever else is necessary to get a proper libvirt user session going.

## Building

In order to build it, you'll need the runtime and SDK for the extension (both will be thrown as warnings if you try to compile without them):

```bash
flatpak install org.flatpak.Builder
flatpak run org.flatpak.Builder --user --install --force-clean --default-branch=stable --disable-rofiles-fuse build org.virt_manager.virt_manager.Extension.Qemu.yaml
```

This will build and install the extension as a `--user` flatpak in a way that will make it work with an installed non-testing version of the virt-manager flatpak.

Make sure that when testing the extension you run
```
flatpak kill org.virt_manager.virt-manager
flatpak run --command=rm org.virt_manager.virt-manager -r /run/user/1000/libvirt
```
That will reset the libvirt state and will make it so your changes work on the local system

## Contributing

Just make sure your contribution works and makes sense for the scope of this extension, otherwise, anything goes! 

You can also contribute in other ways by adding metadata or straight up contributing monetarily to the maintainers. 😉
