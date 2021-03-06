Mailu configuration settings
============================

Common configuration
--------------------

The ``SECRET_KEY`` **must** be changed for every setup and set to a 16 bytes
randomly generated value. It is intended to secure authentication cookies
among other critical uses.

The ``DOMAIN`` holds the main e-mail domain for the server. This email domain
is used for bounce emails, for generating the postmaster email and other
technical addresses.

The ``HOSTNAMES`` are all public hostnames for the mail server. Mailu supports
a mail server with multiple hostnames. The first declared hostname is the main
hostname and will be exposed over SMTP, IMAP, etc.

The ``POSTMASTER`` is the local part of the postmaster email address. It is
recommended to setup a generic value and later configure a mail alias for that
address.

The ``AUTH_RATELIMIT`` holds a security setting for fighting attackers that
try to guess user passwords. The value is the limit of requests that a single
IP address can perform against IMAP, POP and SMTP authentication endpoints.

Mail settings
-------------

The ``MESSAGE_SIZE_LIMIT`` is the maximum size of a single email. It should not
be too low to avoid dropping legitimate emails and should not be too high to
avoid filling the disks with large junk emails.

The ``RELAYNETS`` are network addresses for which mail is relayed for free with
no authentication required. This should be used with great care. It is
recommended to include your Docker internal network addresses if other Docker
containers use Mailu as their mail relay.

The ``RELAYHOST`` is an optional address of a mail server relaying all outgoing
mail.

The ``FETCHMAIL_DELAY`` is a delay (in seconds) for the fetchmail service to
go and fetch new email if available. Do not use too short delays if you do not
want to be blacklisted by external services, but not too long delays if you
want to receive your email in time.

The ``RECIPIENT_DELIMITED`` is a character used to delimit localpart from a
custom address part. For instance, if set to ``+``, users can use addresses
like ``localpart+custom@domain.tld`` to deliver mail to ``localpart@domain.tld``.
This is useful to provide external parties with different email addresses and
later classify incoming mail based on the custom part.

The ``DMAR_RUA`` and ``DMARC_RUF`` are DMARC protocol specific values. They hold
the localpart for DMARC rua and ruf email addresses.

Web settings
------------

The ``WEB_ADMIN`` contains the path to the main admin interface, while
``WEB_WEBMAIL`` contains the path to the Web email client.

Both ``SITENAME`` and ``WEBSITE`` are customization options for the panel menu
in the admin interface, while ``SITENAME`` is a customization option for
every Web interface.

Advanced settings
-----------------

The ``PASSWORD_SCHEME`` is the password encryption scheme. You should use the
default value, unless you are importing password from a separate system and
want to keep using the old password encryption scheme.
