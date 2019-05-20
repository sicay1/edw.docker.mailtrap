# Catch all mail and display it in roundcube interface.



## Start Mailtrap

    $ docker run -d --name=mailtrap -p 8055:80 -p 2525:25 eaudeweb/mailtrap

## Send email

    $ docker run -it --link mailtrap alpine sh

      $ telnet localhost 2525
      ehlo example.com
      mail from: me@example.com
      rcpt to: you@example.com
      data
      Subject: Hello from me
      Hello You,

      This is a test.

      Cheers,
      Me
      .
      quit

## See email via Mailtrap Web UI:

* http://localhost:8055
* **Username:** `mailtrap`
* **Password:** `mailtrap`

## Customisations:

Set environment variables

* `MT_USER` - mailbox user, default mailtrap
* `MT_PASSWD` - mailbox user password, default mailtrap
* `MT_MAILBOX_LIMIT` - mailbox limit in bytes, default 51200000
* `MT_MESSAGE_LIMIT` - message limit in bytes, default 10240000

and recreate the container.
