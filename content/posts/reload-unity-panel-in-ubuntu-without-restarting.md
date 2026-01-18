+++
date = '2024-11-04T16:29:30Z'
draft = false
tags = ['Unity', 'Ubuntu']
title = 'Reload Unity Panel in Ubuntu Without Restarting'
+++

Here is a command to reload the unity desktop notification panel, in Ubuntu, without restarting the entire system:
```bash
killall unity-panel-service
```

As soon as the process is killed, a new one will be spawned, refreshing the notification panel.

This is useful if you have duplicate icons from frozen apps in the panel.
