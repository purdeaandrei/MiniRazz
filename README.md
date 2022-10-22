# MiniRazz - open hardware controller replacement for the Mini M keyboard.

This is a replacement keyboard controller, for the Unicomp Mini M
keyboard, this is an independent community project that is not endorsed by
Unicomp, and it is not related to any official controller sold by them.

Licensed under CERN-OHL-P v2 or later

## Images

![Top of the controller board](images/render_top.png)
![Bottom of the controller board](images/render_bottom.png)

## How to order from JLCPCB:
1. Go to http://jlcpcb.com , sign in to your account (create one if you don't have one)
2. Click Order Now, click Add gerber file
3. Upload the .zip file from the "order" subfolder.
4. Wait for the gerbers to be processed.
5. Check that it correctly detected 4-layerboard.
6. Select PCB Qty you wish to build
7. Specify Layer Sequence, click Yes, And select L1=F_Cu L2=In1_Cu L3=In2_Cu L4=B_Cu
8. Set "Remove Order Number" to "Specify a location"
9. Scroll down, turn on the "SMT Assembly" option, turn it on
10. Select "PCBA Type" = "Economic"
11. Select "Assembly Side" = "Top Side"
12. Select "Tooling holes" = "Added by Customer"
13. Click "I agree to the Terms and Conditions..."
14. Click "Next" on the right side
15. Click "Add BOM File", upload the "*_bom_jlc.csv" file from the "order" subfolder.
16. Click "Add CPL File", upload the "*_cpl_jlc.csv" file from the "order" subfolder.
17. Click "Process BPM & CPL"
18. Make sure that all parts say "Confirmed" with a little check box in the final column. If it shows a greyed out "confirm", or a yellow "Inventory shortage", or there is a red "No parts selected" in the Matched Part Detail column, then some parts may be out of stock. (If parts are out of stock then your options are Wait until it's back in stock / Find equivalent replacement with correct footprint, if it is in the JLCPCB parts library / Redesign the board with a different component / Order the missing part from another supplier and solder it yourself )
19. Click "Next"
20. Check the rotation of components. At the time of writing they were all correct, but JLCPCB may change their component libraries, so this may change in the future.
21. Click "Next"
22. Select Product Description: Office Appliance.../Keyboard...
24. Save to Cart, Check Out.

Cost analysis at the time of writing (2023 Feb 12):

| Qty | Cost (USD) | Cost/Board (USD) |
|-----|------------|------------------|
| 5   |  80.10     | 16.02            |
| 10  |  92.27     | 9.227            |
| 15  | 106.03     | 6.069            |
| 20  | 119.50     | 5.975            |
| 25  | 133.05     | 5.322            |
| 30  | 141.94     | 4.731            |
| 50  | 190.91     | 3.818            |

Note that the above table does NOT include other costs such as shipping,
and cost of additional parts that need to be ordered and assembled.

## Components of this design that have to be ordered separately:
- 2 pcs of 16-pin 90-degree triomate connectors / board:
   - Part number: `6-520314-6` (TE Connectivity AMP Connectors)
   - [Digikey](https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/6-520314-6/1153749)
   - If the 90-degree connectors are not in stock, then you may also be able to get away with vertical ones (part number `6-520315-6`)
      - This has not yet been tested for fit in the keyboard.
- USB connector with locking tab
   - Part number: `LUSBA11100` (AMPHENOL COMMUNICATIONS SOLUTIONS)
   - [Farnell](https://ro.farnell.com/amphenol-icc-commercial-products/lusba11100/usb-conn-2-0-type-a-receptacle/dp/2708971?CMP=e-email-sys-orderack-GLB)
- Optional 90 degree headers for solenoid support. You can use one of two options:
   - An 1x4 90-degree header: (recommended)
      - You will need to use single jumper wires to connect the solenoid driver, (or need to crimp a custom cable with dupont connectors)
   - A 2x3 90-degree header: (not recommended)
      - This may not fit well in the space available, and you may need to add tape to isolate the bottom of the backplate.

## Firmware

At the time of writing only ZMK firmware is available, but QMK and VIAL-QMK firmwares are also planned.

The ZMK firmware can be downloaded by clicking Releases here: https://github.com/purdeaandrei/minirazz-zmk-config
The keymap can be customized by forking this repository, and editing the keymap. The firmware will be automatically rebuilt by github, and will be available on the "Actions" tab.
If you want to keep your keymap secret, you can copy the content of this repository into a private github repository.
