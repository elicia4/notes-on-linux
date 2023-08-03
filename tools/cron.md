# The "cron" scheduling tool 

Notes takes on this video by LearnLinuxTV: https://youtu.be/7cbP7fzn0D8 

[***go back to README***](README.md)  

`cron` allows us to schedule tasks in advance.  

A **cron job** is a job, or task scheduled with `cron`.

Every user on the system has their own set of `cron` jobs. A list of cron jobs
for a user is considered their **crontab**. To see the current user's crontab:

    crontab -l

To set up a cron job:

    crontab -e

With this command, you're not *directly* editing the crontab, it's first going 
to have you work on the changes in the `/tmp` directory. Assuming that
everything is good, it's going to copy everything to the actual crontab.

Take a look at the comments inside the file, they can be useful whenever you
forget how to do something.

A cron job consists of 6 fields:

    * * * * * command

Each individual field correlates to a time unit. The format is as follows:

    m h dom mon dow command

1. `m` - minute
2. `h` - hour 
3. `dom` - day of month
1. `mon` - month
4. `dow` - day of week
    
`*` means every. So `* * * * *` means every minute of every hour of every day of
every month on all days of the week. 

Let's say `m` is 5. What it means is that it's going to execute at **00:05**,
**01:05**, **02:05** and so on, so at every time when a minute field equals 5.

What if you wanted your command to run every day at **9:05**?

    5 9 * * * command

Every month at the 15th at **9:05**?

    5 9 15 * * command

Every August at the 15th at **9:05**?

    5 9 15 8 * command

Every August at the 15th *if it's a Friday* at **9:05**?

    5 9 15 8 5 command

You can also run it hourly/daily:

    @hourly command
    @daily command

Run it at reboot:

    @reboot command