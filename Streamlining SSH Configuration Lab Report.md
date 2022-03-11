# Streamlining SSH Configuration

## .config File

I used Notepad++ to open and edit the .config file to add the Host properties and give it the
`ieng6` alias as seen in the image below.

![.config File](/ssh_config_streamlining_lab_report_resources/ssh_config.png)

## Logging In Using Host Alias

As it can be seen in the image below, login using just the host alias `ieng6` was successful.

![Login via Alias](/ssh_config_streamlining_lab_report_resources/ssh_login_via_alias.png)

## `scp` a File Using Host Alias

In the image below, the scp command runs successfully to transfer a test image `TestImage.png` to
the ieng6 account.

![scp via Alias](/ssh_config_streamlining_lab_report_resources/scp_via_alias.png)