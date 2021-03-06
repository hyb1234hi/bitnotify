# BitNotify

Send email notification after change on your bitcoin wallet or bip44 account

- author: Ondrej Sika <ondrej@ondrejsika.com>
- license: [MIT](https://ondrejsika.com/license/mit.txt)

Tips are welcome to address [__1DhDxyquETrhKk3m6TkHreegr3yFmf8FkB__](https://blockchain.info/address/1DhDxyquETrhKk3m6TkHreegr3yFmf8FkB)

## Installation

Setup base project

    git clone git@github.com:ondrejsika/bitnotify.git
    cd bitnotify
    virtualenv .env
    source .env/bin/activate
    pip install -e .
    ./manage.py migrate

Run in gunicorn

    gunicorn wsgi -b 0.0.0.0:9999

Setup cron job

    # add to your crontab
    * * * * * cd /home/projects/bitnotify && .env/bin/python manage.py bitnotify_cron

## Docker Installation

Setup

    git clone git@github.com:ondrejsika/bitnotify.git
    cd bitnotify
    ./docker-build.sh
    cp settings_local--template.py settings_local.py
    # vim settings_local.py

run

    docker run --name bitnotify -p 9999:80 -v `pwd`/db:/app/db/ -v `pwd`/settings_local.py:/app/settings_local.py ondrejsika/bitnotify

and setup cron

    # add to your crontab
    * * * * * docker exec -ti bitnotify python manage.py bitnotify_cron

## Live version

__<http://bitnotify.sikaapp.cz>__


## Change log

#### v0.1.0

- first working release
- only single wallet support
- without registration and front-end

