# Dell xps 13 9350

This role corrects various small driver/compatibility issues and provides some power-management settings for the 9350 model Dell xps 13.

Under Ubuntu 16.10, the 9350 experiences a problem where wifi doesn't reconnect properly when the machine resumes from suspend. This role includes a very simple service, `wifi-resume.service` that executes `ExecStart=/bin/systemctl restart network-manager.service` on resume. This workaround corrects the issue.

## Role Variables

- `powertop_commands`: a list of Powertop recommended commands to execute. Defaults:

  ```yaml
  powertop_commands:
    - "echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';"
    - "echo 'auto' > '/sys/bus/usb/devices/1-4/power/control';"
  ```

- `enable_wifi_resume_service`: boolean indicating whether or not to
  create and enable the `wifi-resume` service.

## License

MIT
