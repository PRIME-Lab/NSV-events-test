# NSV-events

As part of PRIME Lab's upgrade which includes a second beam source, several methods were tested for communicating commands to the state machine on the real-time targets that control the sample changers.  In previous version of the control system, booleans (10-20) were used.  The goal is to use a single enum to communicate the command.

Initially, DSC notifiers (notifications created when a shared variable's value changes) were played with but they will only work if the RT target uses Windows OS -- the cRIO controllers use a Linux OS.

Settled on the RT target monitoring the timestamp of the shared variable. The user (via an HMI) or the DAQ computer can then simply change/update the shared variable and then the RT target will be triggered to execute the command.

