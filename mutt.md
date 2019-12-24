# mutt

## Required softwares
apt-get install mutt w3m

Create cache directory:  
```mkdir -p ~/.mutt/cache```

### .muttrc file
```
# About Me
set from = "<<YOUR.EMAIL.ADDRESS@HERE>>"
set realname = "<<YOUR NAME>>"

# My credentials
set smtp_url = "smtp://<<YOUR.EMAIL.ADDRESS@HERE>>@mobile.serpro.gov.br:465/"
set smtp_pass = "<<YOUR PASSWORD>>*"
set imap_user = "<<YOUR.EMAIL.ADDRESS@HERE>>"
set imap_pass = "<<YOUR PASSWORD>>"

# My mailboxes
set folder = "imaps://mobile.serpro.gov.br:993"
set spoolfile = "+INBOX"

# Caching
set header_cache = "~/.mutt/cache/headers"
set message_cachedir = "~/.mutt/cache/bodies"
set certificate_file = "~/.mutt/certificates"

# Update settings
set mail_check = 30
set move = no
set imap_keepalive = 10
set sort = threads
set ssl_starttls = yes
set ssl_force_tls = yes 
unset imap_passive        
set imap_check_subscribed
set mail_check = 32
set timeout = 10
set net_inc = 5

# Default editor
set editor = "vim"

# Sorting
set sort = reverse-threads
set sort_aux = date-received

# Using .mailcap to view html mails
auto_view text/html

# Wrapping
set wrap = 80

# Visuals
color status white blue
color index green  default ~N  # new
color index red default ~D  # deleted
color index brightmagenta default ~T  # tagged
color index brightyellow default ~F  # flagged
color header green default "^Subject:"
color header yellow default "^Date:"
color header yellow default "^To:"
color header yellow default "^Cc:"
color header yellow default "^Bcc:"
color header yellow default "^From:"
color header red default "^X-.*:"
unset mark_old
```

### .mailcap file
```
text/html; w3m -I %{charset} -T text/html; copiousoutput;
```
