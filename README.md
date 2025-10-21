# ffmpeg-rpilpfm-streamer-template
A template that listens to a network stream, and transmits it out a selected audio interface to broadcast.

#Prerequisites:
 - Ubuntu Installed with a user configured as a sudoer and preferably with ssh.
 - FFMPEG latest, installed and configured.
 - alsa-utils, installed and configured with an appropriate volume. Note you must configure the output device with its corresponding id eg. 0 - Headphones, this will be referenced later by the script.

#Installation Notes:
Must be installed on ubuntu or similar architecture.
The streamer consistes of two processes:
  - A script that listens to a network m3u8 stream called start_stream.sh which should be placed in the users root folder, or should be returned upon ls directly after login from any user.
    - This must be an executable file, to do so during installation, running "chmod u+x start_stream.sh" in the folder in question.
  - A service file, called streaming.service, that is configured to run at startup "/etc/systemd/system/streaming.service"
    - This service can be operated with the following commands.
      - systemctl **cat** streaming.service
      - journalctl -u streaming.service **-f**

      - sudo systemctl **start** streaming.service
      - sudo systemctl **daemon-reload**
      - sudo systemctl **restart** streaming.service
      - sudo systemctl **stop** streaming.service
