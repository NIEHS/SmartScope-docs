## Register a microscope to the SmartScope database

Now that the connection to SerialEM works, we can add our microscope to the database.

To do so, navigate to the [admin portal](/getting_started/administration/admin_panel) and then the Microscopes section and add microscope. It should bring you to [localhost:48000/admin/detector/add/](localhost:48000/admin/microscope/add/).

Then follow the instructions on how to [add a microscope](/getting_started/administration/microscopes)

## Register a detector to the SmartScope database

!!! warning 
    
    Each microscope must have least one detector.

Similarly to adding a microscope, navigate to the admin portal and then the Detectors section and add. It should bring you to [localhost:48000/admin/detector/add/](localhost:48000/admin/detector/add/).

Then follow the instructions on how to [add a detector](/getting_started/administration/detectors)


## Steps specific to JEOL CRYO ARM systems

To run SmartScope on CRYO ARM a few options need to be enabled in the microscope tab since all the scopes have the following items:

- Aperture Control
- Cold FEG
- Energy Filter (for every detector entry)

Next, to manage grid exchanges, SerialEM must call the custom `Transfer_Cartridge.bat` script provided by JEOL. The default path for gridswapper is set to `C:\Program Data\SerialEM\PyTool\Transfer_Cartridge.bat`

If this path needs to be changed, a additional settings file must be created. First, find your microscope id from the url in the admin portal as show below:

![Micropscope ID](/assets/microscope_id.png)

Then create a file with `MICROSCOPE_ID.yaml` in `shared/smartscope/`

Then add the new path to the `Transfer_Cartridge.bat` as shown below:

```yaml
transfer_cartridge_path: 'C:\PATH\TO\Transfer_Cartridge.bat'
```

Example on how to add it in a single command (please replace with your own values):
```shell-session
echo "transfer_cartridge_path: 'C:\PATH\TO\Transfer_Cartridge.bat'" > shared/smartscope/7INHMHBe2LyOZ2xKEKpsAGhd889pCO.yaml 
```