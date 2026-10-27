# AIRouter updates

Signed application releases for AIRouter Linux ARM64 appliances, maintained by SayonaraMan.

Existing AIRouter appliances check the latest stable release hourly, with up to ten minutes of random delay. Checks only report a new version. Installation requires the owner to run `sudo systemctl start 9router-install.service` locally; no release is installed automatically. No GitHub account or token is required on the device. Updates contain the application and AIRouter integration adapters; device accounts, passwords, provider credentials and raw Linux disk images are excluded.

The manual policy requires the current AIRouter device bootstrap. Application packages do not replace the privileged updater; older installations need a separate bootstrap migration first.

## Authenticity

`channel.json` is a signed envelope containing an Ed25519-authenticated manifest. The manifest fixes the version, increasing release sequence, supported platform, HTTPS asset URL, size and SHA256. The appliance verifies it against a pinned public key before downloading and activating the package. `update-public.pub` is provided for independent inspection; trust it through an existing trusted installation or separately verified source, not merely because it accompanies a downloaded package.

Release assets: `airouter-VERSION-linux-arm64.tar.gz`, `channel.json`, `SHA256SUMS`. Installation is intended for an already provisioned AIRouter appliance with Node 22 and its native SQLite runtime. These packages are not bootable Linux images.

The device keeps configuration outside the application release and restores the previous application and saved data after a detected startup failure. This channel does not modify the Linux kernel, bootloader, hardware configuration or storage partitions. It is not a full firmware recovery system.

## Licenses

AIRouter includes the upstream 9router application under the MIT license. Its LICENSE and third-party license files remain inside each package. Public packages contain inspectable JavaScript; the private development repository does not make distributed application code confidential.
