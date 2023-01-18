#BIOS configurations
## List of BIOS configurations which should be modified
Item | Default value | To be modified | Can be modified on BIOS menu ?
-------------------- | ------- | -------------- | -------
Secure Boot | Enables | Disabled | Yes
CFG Lock | Enabled | Disabled | No
EHCI Hand-off | Disabled | Enabled | No
## Modification of configurations which are not shown on the BIOS menu
Some required BIOS configuration items are not accessible with BIOS menu of GPD Pocket 3.  
`EFI/OC/Tools/modGRUBShell.efi` is a tool to modify such BIOS configuration. Run `modGRUBShell.efi` from UEFI shell, then use following commands to modify BIOS. You can start UEFI shell `OpenShell.efi` with pushing SPACE key at picker screen on OpenCore. 

`modGRUBShell.efi` can run only under Secure Boot is disabled.

### Disable CFG Lock
```
> setup_var_cv CpuSetup 0x43 0x01 0x00
```
### Enable EHCI Hand-off
```
> setup_var_cv UsbSupport 0x02 0x01 0x01
```

## Reset BIOS in case of any trouble
The small hole on the rear of the GPD Pocket 3 beside to the module slot is BIOS reset button.

## Appendix

`bios_rom` directory contains BIOS dump data as following.

* `gpd3_bios_default.bin` BIOS ROM dump by chipsec.
* `Setup_body.fbd` Extracted IFR data from `gpd3_bios_default.bin` by UEFITool
* `setup.txt` Extracted IFR config from `Setup_body.fbd` by ifrextract