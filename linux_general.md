
Installing an application downloaded as .tar.xz file:

Example: Blender 4.2.3

Download file location: Downloads/blender-4.2.3-linux-x64.tar.xz


Go to Downloads directory:

cd Downloads


Extract the archive:

tar -xf blender-4.2.3-linux-x64.tar.xz

This creates a folder: blender-4.2.3-linux-x64/


Test-run Blender:

cd blender-4.2.3-linux-x64
./blender


Move Blender to a system location:

To keep things tidy, move it to /opt (standard location for third-party apps):

sudo mv blender-4.2.3-linux-x64 /opt/blender-4.2.3


Run Blender from its final location:

/opt/blender-4.2.3/blender


Make Blender runnable from anywhere

Add Blender to your PATH:

echo 'export PATH="/opt/blender-4.2.3:$PATH"' >> ~/.bashrc
source ~/.bashrc

Now you can simply run:

blender


Create a desktop launcher

Create a launcher file:

nano ~/.local/share/applications/blender.desktop

Paste:

[Desktop Entry]
Name=Blender 4.2.3
Exec=/opt/blender-4.2.3/blender
Icon=/opt/blender-4.2.3/blender.svg
Type=Application
Categories=Graphics;3D;

Save and close. Blender will now appear in your application menu.



General process for installing ANY .tar.xz Linux app:

This applies to Blender, Godot, Krita (portable), etc.

tar -xf appname-version-linux.tar.xz
cd appname-version
./appname
