# Gunicorn

## WSGI

The WSGI is a spec that standardizes a way for traditional web servers (nginx,  apache, etc) communicate with web applications and frameworks like  flask. Traditional web servers don't understand how to communicate  directly with web applications like flask so you need something to sit  in the middle, which is where a WSGI server comes into play.  

## Gunicorn

The Gunicorn is an implementation of a WSGI server that will act as the intermediary between a tradition web server and your flask application. While you  could server out your app with just the wsgi server, it is more common  to situate it behind a web server e.g.) nginx → gunicorn → flask app  code).    