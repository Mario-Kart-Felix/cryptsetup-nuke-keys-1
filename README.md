Purpose
=======

This repository is intended to build a RPM (based on Fedora 23 sRPM) with the cryptsetup-nuke-keys patch

To build package you can run:
------------------------------------
<pre>[root:~/src] # rpmbuild -ba SPECS/cryptsetup-1.6.8-2.fc23.spec</pre>

don't forget to rebuild initramfs with the new package installed:

<pre>dracut -vf</pre>

cryptsetup-nuke-keys
====================

A patch for cryptsetup which adds the option to nuke all keyslots given a certain passphrase.
Original cryptsetup patch by Juergen Pabel, found here - http://lxer.com/module/newswire/view/103692/index.html

<pre>
root@kali:~# cryptsetup luksAddNuke /dev/sda5
Enter any existing passphrase:          (existing password)
Enter new passphrase for key slot:      (set the nuke password)
</pre>

Once the machine is rebooted and you are prompted for the LVM decryption passphrase.
If you provide the nuke password, all password keyslots get deleted, rendering the encrypted LVM volume inaccessible.

For more details check -  http://www.kali.org/how-to/emergency-self-destruction-luks-kali
# typescript
README.md
typescript-action status

Create a JavaScript Action using TypeScript
Use this template to bootstrap the creation of a TypeScript action.🚀

This template includes compilation support, tests, a validation workflow, publishing, and versioning guidance.

If you are new, there's also a simpler introduction. See the Hello World JavaScript Action

Create an action from this template
Click the Use this Template and provide the new repo details for your action

Code in Main
Install the dependencies

$ npm install
Build the typescript and package it for distribution

$ npm run build && npm run package
Run the tests ✔️

$ npm test

 PASS  ./index.test.js
  ✓ throws invalid number (3ms)
  ✓ wait 500 ms (504ms)
  ✓ test runs (95ms)

...
Change action.yml
The action.yml contains defines the inputs and output for your action.

Update the action.yml with your name, description, inputs and outputs for your action.

See the documentation

Change the Code
Most toolkit and CI/CD operations involve async operations so the action is run in an async function.

import * as core from '@actions/core';
...

async function run() {
  try { 
      ...
  } 
  catch (error) {
    core.setFailed(error.message);
  }
}

run()
See the toolkit documentation for the various packages.

Publish to a distribution branch
Actions are run from GitHub repos so we will checkin the packed dist folder.

Then run ncc and push the results:

$ npm run package
$ git add dist
$ git commit -a -m "prod dependencies"
$ git push origin releases/v1
Note: We recommend using the --license option for ncc, which will create a license file for all of the production node modules used in your project.

Your action is now published! 🚀

See the versioning documentation

Validate
You can now validate the action by referencing ./ in a workflow in your repo (see test.yml)

uses: ./
with:
  milliseconds: 1000
See the actions tab for runs of this action! 🚀

Usage:
After testing you can create a v1 tag to reference the stable and latest V1 action
