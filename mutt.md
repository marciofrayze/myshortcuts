# mutt

## Required softwares
apt-get install mutt w3m

### .muttrc file
```
# About Me
set from = "<<YOUR.EMAIL.ADDRESS@HERE>>"
set realname = "<<YOUR NAME>>"

# My credentials
set smtp_url = "smtp://<<YOUR.EMAIL.ADDRESS@HERE>>@serpro.gov.br@mobile.serpro.gov.br:465/"
set smtp_pass = "<<ENTER PASSWORD HERE>>"
set imap_user = "<<YOUR.EMAIL.ADDRESS@HERE>>"
set imap_pass = "<<ENTER PASSWORD HERE>>"

# My mailboxes
set folder = "imaps://mobile.serpro.gov.br:993"
set spoolfile = "+INBOX"

# Where to put the stuff
set header_cache = "~/.mutt/cache/headers"
set message_cachedir = "~/.mutt/cache/bodies"
set certificate_file = "~/.mutt/certificates"

# Etctext/html; w3m -I %{charset} -T text/html; copiousoutput;
set mail_check = 30
set move = no
set imap_keepalive = 900
set sort = threads
set editor = "emacs"

# Sorting
set sort=reverse-threads
set sort_aux=date-received

# Using .mailcap to view html mails
auto_view text/html

# Wrapping at 80
set wrap=80
```

### .mailcap file
```
text/html; w3m -I %{charset} -T text/html; copiousoutput;
```
