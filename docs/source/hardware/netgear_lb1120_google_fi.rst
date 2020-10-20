NETGEAR LB1120 (LTE modem) with Google Fi
=========================================

As of 2020-10-20, I was able to use the NETGEAR LB1120 with Google Fi, with a data-only SIM.
For reliable operation I had to use the APN settings
`documented by Google <https://support.google.com/fi/answer/6330195?hl=en>`_:

* Name: ``Google Fi``

* APN: ``h2g2``

This is configured by heading to the admin interface of the device
at ``http://192.168.5.1`` (default password is on the label on the device).
