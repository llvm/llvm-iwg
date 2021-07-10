Hardware_Facts
=========

This role is used to install a custom fact script which helps generate
hardware information about a node.  The information comes from the
system_profiler binary which is part of macOS.  This role focuses on
the SPHardwareDataType within system_profiler.

Dependencies
------------

This role depends on the included file/hardware.fact which will be installed on the target machine.

Example Playbook
----------------

    ---
    - hosts: all
      roles:
        - role: roles/hardware_facts


Example Output
--------------

    TASK [roles/hardware_facts : Print Node Hardware Facts] ***********
    ok: [smoosh-229] =>
      ansible_local.hardware.SPHardwareDataType[0]:
        Lightshow_version: 1.4a6
        SMC_version_system: 2.20e0
        _name: hardware_overview
        boot_rom_version: 426.0.0.0.0
        cpu_type: 6-Core Intel Xeon E5
        current_processor_speed: 3.5 GHz
        l2_cache_core: 256 KB
        l3_cache: 12 MB
        machine_model: MacPro6,1
        machine_name: Mac Pro
        number_processors: 6
        packages: 1
        physical_memory: 32 GB
        platform_UUID: 3C12ED30-F131-5579-A485-C32B0A027221
        platform_cpu_htt: htt_enabled
        provisioning_UDID: 3C12ED30-F131-5579-A485-C32B0A027221
        serial_number: F5KLQ04CF694


Responsible Individual
------------------

Mike Edwards - medwards@llvm.org