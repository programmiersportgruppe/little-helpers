# mail-result

This script executes a command, captures the output and creates an email
and a logfile entry when done. It is ideally suited to wrap cron jobs, if more fine grain control
of the generated email is needed.

## Basic Usage

~~~ {.bash}
mail-result -j "run simlulation" -m someone@somedomain.com run-simulation
~~~

This will execute the `run-simulation` program. After the program has finished
an email will be sent to someone@somedomain.com.
The subject line will contain either '[SUCCESS]' or '[FAILURE]' depending on
the exit status of the program. This is useful for filtering out emails about
successful jobs. It will also contain the job name, which in this
case is 'run simulation' and the hostname of the machine on which it was
executed.

The body of the mail contains the standard output and standard error of the
program.

Additionally a one line log message will be written to ~/jobs.log.

To suppress the email sending in case of success the option `-n` can be specified.

## Installation

* The executable script `mail-result` needs to be on the path.
* The `mail` utility needs be working.

