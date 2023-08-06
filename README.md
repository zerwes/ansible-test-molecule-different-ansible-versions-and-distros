[![ansible-lint](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/lint.yml/badge.svg)](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/lint.yml)
[![molecule test](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/molecule.yml/badge.svg)](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/molecule.yml)

:exclamation: this repository is only intended as an example and for demonstration purposes

# ansible-test-molecule-different-ansible-versions-and-distros
test ansible role with different ansible versions using molecule as a github action

## scope
main goal is to test a role with the latest ansible version (6 at the time of writing) and the legacy ansible 2.9 version

## workflow
[.github/workflows/molecule.yml](.github/workflows/molecule.yml)

## caveats
in some cases you might need to add
```diff
 ---
 - name: Converge
   hosts: all
+  vars:
+    ansible_python_interpreter: /usr/bin/python3
   tasks:
     - name: "Include ansible-test-molecule-different-ansible-versions-and-distros"
       include_role:
```
to your molecule playbooks for the legacy test, as the interpreter detection has changed between the versions ...
