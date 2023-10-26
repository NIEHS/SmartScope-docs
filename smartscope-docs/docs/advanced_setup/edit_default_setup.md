There is a way to edit the default values of disable certain fields in the [smartscope session setup page](/usage/preparation/setup_session) to suit your facility.

In the SmartScope installation folder, open the `shared/smartscope/default_collection_params.yaml` as shown below:

```yaml
atlas_x : 
  initial: 6
atlas_y :
  initial: 2
square_x :
  initial: 1
  readonly: True
square_y :
  initial: 1
  readonly: True
squares_num :
  initial: 3
holes_per_square :
  initial: 2
bis_max_distance :
  initial: 3
min_bis_group_size :
  initial: 1
target_defocus_min :
  initial: -2
target_defocus_max :
  initial: -2
step_defocus :
  initial: 0
drift_crit :
  initial: -1
tilt_angle :
  initial: 0
save_frames :
  initial: True
force_process_from_average :
  initial: False
  disabled: True
offset_targeting :
  initial: True
offset_distance :
  initial: -1
zeroloss_delay :
  initial: -1
```

## Changing default values

There is one entry for each field in the form. The `initial` key is the default value displayed in the form.

Simply change the value and the changes will be automatically reflected on the webpage.

## Disabling a field

To completely disable a field and always make it use the default value, simply add the `disabled: True` key for the field.
