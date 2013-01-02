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

# tell

This script executes a command tells the user upon completion whether it
succeeded or failed using a text-to-speech facility. This is ideally suited
for long running tasks that require attention when done.

## Usage

~~~ {.bash}
tell make all
~~~

This will say 'success' or 'fail' on completion and also return the exit status
that make originally returned, so something like this is still possible:

~~~ {.bash}
tell make all && git push
~~~

It currently only with macosx, however espeak could be used on linux.

