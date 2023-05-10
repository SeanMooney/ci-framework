## Role: edpm_build_images
This role will build a edpm images, EDPM hardened uefi and ironic-python-agent images.
It will only package the images inside a container image for distribution based on
the variables "cifmw_edpm_build_images_ironic_python_agent_package" and
"cifmw_edpm_build_images_hardened_uefi_package".

### Privilege escalation
None

### Parameters
* `cifmw_edpm_build_images_basedir`: Base directory. Defaults to `cifmw_basedir` which  defaults to `~/ci-framework`.
* `cifmw_edpm_build_images_src`: `edpm-image-builder` github repo url.
* `cifmw_edpm_build_images_artifacts`: Build images logs.
* `cifmw_build_host_packages`: List of packges required to build the images.
* `cifmw_edpm_build_images_config_dir`: Images dir path from `edpm-image-builder` repo.
* `cifmw_edpm_build_images_elements`: Elements path which contains `edpm-image-builder` and `ironic-python-agent-builder` repo.
* `cifmw_edpm_build_images_all`: (Boolean) Build both the `edpm-hardened-uefi` and `ironic-python-agent` images when it true. Default to false.
* `cifmw_edpm_build_images_hardened_uefi`: (Boolean) Build `edpm-hardened-uefi` image when it true. Default to false.
* `cifmw_edpm_build_images_ironic_python_agent`: (Boolean) Build `ironic-python-agent-builder` image when it true. Default to false.
* `cifmw_edpm_build_images_hardened_uefi_package`: (Boolean) Packaged `edpm-hardened-uefi` image inside a container image for distribution. Default to false.
* `cifmw_edpm_build_images_ironic_python_agent_package`: (Boolean) Packaged  `ironic-python-agent-builder` image inside a container image for distribution. Default to false.
* `cifmw_edpm_build_images_cleanup`: (Boolean) Cleanup virtual enviroment if true. Default to False.

### Example
```YAML
---
- hosts: localhost
  gather_facts: true
  roles:
    - role: "edpm_build_images"
  tasks:
    - name: Build edpm images
      ansible.builtin.include_role:
        name: "edpm_build_images"
```
