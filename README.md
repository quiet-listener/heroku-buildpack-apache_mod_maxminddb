# heroku-buildpack-apache_mod_maxminddb

heroku-buildpack-apache_mod_maxminddb can be used with other heroku buildpack consisting of apache to enable maxminddb module in apache. To Use, you must know the path of apxs binary location.
e.g. apxs binary path for heroku/php buildpack is 

```/app/.heroku/php/bin/apxs```

you can check yours apxs path in following way:
```bash
heroku run bash --app foobar #Your app name in place of foobar
# Now you will be in a shell of a dyno 
# Replace /app with  your app $HOME dir most probably it would be /app
~$ find /app -name apxs -type f
```

## Usage

Add this buildpack after your apache buildpack in order.

```bash
heroku buildpacks --app foobar #Yourappname
```
By running above command with your app name you could list you buildpack attached to that app. Attach this build pack at any order after your buildpack containing apache.
``` bash 
# replace 3 with your position and foobar with your app name
heroku buildpacks:add --index 3 https://github.com/quiet-listener/heroku-buildpack-apache_mod_maxminddb.git --app foobar
```
The default maxminddb version is set to ```1.1.0``` and default apxs path is set to ```/app/.heroku/php/bin/apxs```

you can add change it by adding env variable specifying them
```
MAXMINDDB_VERSION = 1.1.0 # custom maxminddb version
APXS_PATH = /app/.heroku/php/bin/apxs # custom apxs path
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
