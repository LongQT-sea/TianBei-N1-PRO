**Fix Code 43 (iGPU) on Intel N150 and Enable Display Output on All Monitors**

**For Proxmox VE:**

1. Download the file `n150_vfio_igd.rom` and place it in:
   `/usr/share/kvm/`

2. In your VM configuration, instead of using:
   `hostpci0: 0000:00:02.0`
   Use the following line:
```
hostpci0: 0000:00:02.0,legacy-igd=1,romfile=n150_vfio_igd.rom
```

3. Set **Display** to `None`.

4. Set **Machine** to `Default (i440fx)`.

---

**For QEMU/KVM (Virt-Manager or CLI):**

* Use machine type: `i440fx`

* Add the following to the QEMU arguments:

  ```
  -device vfio-pci,host=0000:00:02.0,id=hostpci0,bus=pci.0,addr=0x2,romfile=/usr/share/kvm/n150_vfio_igd.rom
  ```

