# OpenWRT Scripts
* Port Mirroring
<pre>This script checking the WAN port and LAN1 and blocking a first port after 
disconnecting second port and on the contrary after connected second port 
unblock first port. Same rule for second port.</pre>
You can view the video on YouTube: https://youtu.be/6U_Vl-BGoWo
* Port Monitor
<pre>This script just checking ports activity and turn on/turn off leds after
connecting or disconnecting patch-cord.</pre>
You can view the video on YouTube: https://youtu.be/V6qmrIIIVa0
# Install
1. Place file into /usr/bin/ folder in your router
2. Set up permission for him <code>chmod +x /usr/bin/<script_name></code>
3. Add line with script name into /etc/rc.local before 'exit 0'
* Example:
  <code><pre><your_script_name\> &
  exit 0</pre></code>
