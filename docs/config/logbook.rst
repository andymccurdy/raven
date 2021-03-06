Configuring ``logbook``
=======================

Raven provides a logbook handler which will pipe messages to Sentry.

First you'll need to configure a handler::

    from raven.handlers.logbook import SentryHandler

    # Manually specify a client
    client = Client(...)
    handler = SentryHandler(client)

You can also automatically configure the default client with a DSN::

    # Configure the default client
    handler = SentryHandler('http://public:secret@example.com/1')

Finally, bind your handler to your context::

    from raven.handlers.logbook import SentryHandler

    client = Client(...)
    sentry_handler = SentryHandler(client)
    with my_handler.applicationbound():
        # everything logged here will go to sentry.
