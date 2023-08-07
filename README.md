[![ansible-lint](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/lint.yml/badge.svg)](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/lint.yml)
[![molecule test](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/molecule.yml/badge.svg)](https://github.com/zerwes/ansible-test-molecule-different-ansible-versions-and-distros/actions/workflows/molecule.yml)

:exclamation: this repository is only intended as an example and for demonstration purposes

# ansible-test-molecule-different-ansible-versions-and-distros
test ansible role with different ansible versions using molecule as a github action

## scope
main goal is to test a role with multiple ansible version including the legacy ansible 2.9 version on multiple distros.

## workflow
[.github/workflows/molecule.yml](.github/workflows/molecule.yml)

### workflow matrix
using a [matrix](https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs) of ansible versions and distros will result in **24** jobs:

 * test (ansible82, debian12)
 * test (ansible82, debian11)
 * test (ansible82, debian10)
 * test (ansible82, ubuntu2204)
 * test (ansible82, ubuntu2004)
 * test (ansible82, ubuntu1804)
 * test (ansible74, debian12)
 * test (ansible74, debian11)
 * test (ansible74, debian10)
 * test (ansible74, ubuntu2204)
 * test (ansible74, ubuntu2004)
 * test (ansible74, ubuntu1804)
 * test (ansible62, debian12)
 * test (ansible62, debian11)
 * test (ansible62, debian10)
 * test (ansible62, ubuntu2204)
 * test (ansible62, ubuntu2004)
 * test (ansible62, ubuntu1804)
 * test (ansible29, debian12)
 * test (ansible29, debian11)
 * test (ansible29, debian10)
 * test (ansible29, ubuntu2204)
 * test (ansible29, ubuntu2004)
 * test (ansible29, ubuntu1804)

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
