# prometheus-rsnapshot-metrics

This repository contains a Prometheus Node Exporter Textfile Collector script
that produces various metrics related to rsnapshot. It is intended to be run
on the rsnapshot server.

Some of the metrics depend on a presence of a per-target marker file. That
file is supposed to be modified (e.g. with "touch" command from cron)
regularly, so that failing backups can be detected easily from the timestamps
of those marker files.

# Usage

Script is invoked as follows:

    Usage: create-rsnapshot-prometheus-metrics.sh [-b backup directory] [-m marker file name] [-a maximum marker file age] [-d maximum search depth]

Sane defaults are provided for each of these settings:

    * Latest backup directory (-b): /var/backups/rsnapshot/daily.0
    * Marker file name (-m): .rsnapshot-marker
    * Max backup age in days (-a): 2
    * Max search depth (-d): 3

Any parameters that are inapplicable in your environment can be overridden on
the command-line.

Note that the script outputs the metrics to the console, so you need to
redirect its output to a metrics file in the Textfile Collector metrics
directory.
