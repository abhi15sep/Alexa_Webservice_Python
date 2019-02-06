# Alexa_Webservice_Python
Alexa skill using webservice (Python)

Use ngrok to consume locally running webservice in alexa development kit as https endpoint. It uses port forwarding to expose it over public internet.

Steps to setup ngrok:
====================
1) Download from https://dashboard.ngrok.com/get-started
2) Unzip to install
    $ unzip /path/to/ngrok.zip
3) To start tunnel
./ngrok http 5000 (here 5000 is the port of locally running webservice).


Example Output:
===============
Session Status                online
Session Expires               7 hours, 25 minutes
Version                       2.2.8
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://c83a32a7.ngrok.io -> localhost:5000
Forwarding                    https://c83a32a7.ngrok.io -> localhost:500


At last use  https://c83a32a7.ngrok.io as https endpoint. Make sure to select "My development endpoint is a sub-domain of a domain that has a wildcard certificate from a certificate authority" option.

Steps to Deploy code in Heroku:
==============================
Heroku steps

i) Flask run code
   port = int(os.getenv('PORT', 5000))
   print "Starting app on port %d" % port
   app.run(debug=False, port=port, host='0.0.0.0')
   
ii) Create Procfile, requirements.txt

iii) Commands:
    >> git init .
    >> git add .
    >> git commit -m "init" 
    >> heroku create greetingsskillalexa
    >> git remote -v
    >> heroku git:remote -a <name from above step>
    >> git push heroku master
  
  iv) To set env variable in heroku:
    >> heroku config:set GREETINGS_DEBUG_EN=True
    >> heroku config:unset GREETINGS_DEBUG_EN
