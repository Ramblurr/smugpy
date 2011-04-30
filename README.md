Smugpy
======

Smugpy is an Python library for the [SmugMug](https://secure.smugmug.com/signup.mg?Coupon=2TqKwSOXw5HeU) API created by Chris Hoffman.  Smugpy supports all versions of the API and Oauth 1.0 for API versions 1.2.2+.  For more information, [SmugMug API Documentation](http://wiki.smugmug.net/display/API/)

Installation
------------
Installing the python client is a very simple process. Once you've downloaded the source bundle for the client, execute the following:

    python setup.py install

Usage
-----
Anonymous request:

    from smugpy import SmugMug

    API_KEY = "XXXXXXXXXXXXXXXXXXXXXXXXX"

    smugmug = SmugMug(api_key=API_KEY)
    smugmug.login_anonymously()
    albums = smugmug.albums_get(NickName="williams")

    for album in albums["Albums"]:
        print "%s, %s" % (album["id"], album["Title"])

Oauth request:

    from smugpy import SmugMug

    API_KEY = "XXXXXXXXXXXXXXXXXXXXXXXXX"
    OAUTH_SECRET = "YYYYYYYYYYYYYYYYYYYYYYY"

    smugmug = SmugMug(api_key=API_KEY, oauth_secret=OAUTH_SECRET)

    #Oauth handshake
    smugmug.auth_getRequestToken()
    raw_input("Authorize app at %s\n\nPress Enter when complete.\n" % (smugmug.authorize()))   
    smugmug.auth_getAccessToken()

    albums = smugmug.albums_get(NickName="williams") # Moon River Photography, thanks Andy!
    for album in albums["Albums"]:
        print "%s, %s" % (album["id"], album["Title"])


Known Issues
------------
* Smugpy does not support uploads

Helping Out
-----------
If you notice any problems, please report them to the GitHub issue tracker at [http://github.com/chrishoffman/smugpy/issues](http://github.com/chrishoffman/smugpy/issues). 

License
-------
Smugpy is released under the MIT license.