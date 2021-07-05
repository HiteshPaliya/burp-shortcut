# burp-shortcut
Reference to how to create Burp Suite GUI launcher. 

# For example:
### If your burpsuite jar is named: burpsuite_free_v1.5.jar
### ..and located at: /opt/burpsuite/
### export BURP_VER=1.5
### export BURP_PATH=/opt/burpsuite/
#
export BURP_VER=<insert burp version number here>  
export BURP_PATH=<insert path to burp jar here>

# Extract icon
unzip ${BURP_PATH}/burpsuite_free_v${BURP_VER}.jar */icon64.png
 
# Make icon directory and move icon64.png inside it
mkdir -p ${HOME}/.local/share/pixmaps/
mv ./burp/media/icon64.png ${HOME}/.local/share/pixmaps/burpsuite.png
 
# Make applications directory (where the shortcut will be placed)
mkdir -p ${HOME}/.local/share/applications/
 
#Create launcher item
cat << EOF > ${HOME}/.local/share/applications/burpsuite.desktop
[Desktop Entry]
Name=Burp Suite
Version=${BURP_VER}
Exec=/usr/bin/java -jar ${BURP_PATH}/burpsuite_free_v${BURP_VER}.jar 
Icon=${HOME}/.local/share/pixmaps/burpsuite.png
Terminal=false
Type=Application
Categories=Utility;Application;
EOF

# Delete the ./burp/ directory
rm -rf ./burp/
