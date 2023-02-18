# protonvpn

https://protonvpn.com/support/official-linux-vpn-kali/


How to install a VPN on Kali Linux

To install Proton VPN on Kali Linux:

1. Download our DEB package to install our repository

This package contains the repository configuration and keys that are required to install the Proton VPN app.

Download the Proton VPN DEB package

2. Install the Proton VPN repository

In the terminal, enter the following text (followed by <enter>).

sudo apt-get install {/path/to/}protonvpn-stable-release_1.0.3_all.deb

Replace {/path/to/} with the path to where you download the file. For example:

sudo apt-get install ~/Downloads/protonvpn-stable-release_1.0.3_all.deb 

Please don’t try  to check the GPG signature of this release package (dpkg-sig –verify). Our internal release process is split into several part and the release package is signed with a GPG key, and the repo is signed with another GPG key. So the keys don’t match.

If you want to check the repo package integrity, you can check its checksum with the following command:

echo "c409c819eed60985273e94e575fd5dfd8dd34baef3764fc7356b0f23e25a372c
 protonvpn-stable-release_1.0.3_all.deb" | sha256sum --check -

3. Update the apt-get package list

The following command updates the list of available packages and their versions. Doing this allows you to install the Proton VPN App. Run:

sudo apt-get update

4. Install the app

Now run:

sudo apt-get install protonvpn

Reboot your Linux PC and log in to the Proton VPN app with your Proton Account details. If you do not already have a Proton Account, you can sign up for a Proton VPN Free plan for Linux.

The Proton VPN Linux app is now ready to secure your internet browsing and allow you to access the free and open internet. However, please note that the system tray icon may not work on Kali Linux. This is because the system tray icon requires dependencies that have been deprecated in Kali. 

Learn how to use the Proton VPN Linux app
Notes
1. Uninstall the Proton VPN app
To remove the Proton VPN app from your Kali system, open the terminal and run:

sudo apt-get autoremove protonvpn

Remove any leftover files:

rm -rf ~/.cache/protonvpn

Followed by:

rm -rf ~/.config/protonvpn

2. Disable the kill switch if you have uninstalled the official app

You should disable the kill switch before uninstalling our official app. Failure to do this will likely prevent you from accessing the internet. Fortunately, this is easily fixed:

a) Open the terminal and use the following command to identify connections belonging to Proton VPN:

nmcli connection show --active

b) You will see a list of active connections. Look for any of them with the prefix pvpn- This usually includes pvpn-killswitch and pvpn-ipv6leak-protection, and may include pvpn-routed-killswitch. Delete all these connections using the following command:

nmcli connection delete [connection name]

For example:

nmcli connection delete pvpn-killswitch

c) Run the following command again to ensure that you have deleted all Proton VPN connections:

nmcli connection show --active

If any remain, delete them as described above.
3. Required dependencies

You’ll need one of the following Linux keyrings installed on your Kali system for our Linux app to work. But the chances are that one of them is already installed (you don’t want both, though, as this can cause problems).

    KWallet
    Gnome-keyring

Also needed (but probably already installed) is:

    systemd

4. Help Proton iron out bugs with the early release version of this app

Proton is a community-based project that relies on your support. If you want to help us identify bugs before this app is made available to the general public, you can download the following early access version instead of the one we link to in step 1 of this guide.  

Download the early access version of the Proton VPN DEB package

To check the integrity of the package, use the following command:

echo "caba770e3544a4f33b7d5718dedd8bc1d06cfcd2b2f8c4f33b5a42d15a78e74a  protonvpn-beta-release_1.0.3_all.deb" | sha256sum --check -

Setup instructions are otherwise as described above. 

Helping us in this way will give you access to the latest features before they are available for general release, but it’s only recommended if you are an experienced Linux user who is relaxed about your threat model.  

