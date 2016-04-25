#Caravel - Data Exploration and Visualization Tool

1. **What is caravel?**


    Caravel is a data exploration platform designed to be visual, intuitive, and interactive. ( Used internally by **Airbnb** ).
    It's an open source data visualization platform that allows users easy and intuitive way for Data exploration and to create and share beautiful charts and dashboards with Security and Authentication.

2. **Installation and Configuration of Caravel.**
     
    ### Getting Started
    ---------------

    Caravel is currently only tested using Python 2.7.*. Python 3 support is
    on the roadmap, Python 2.6 won't be supported.


    ### OS dependencies
    ---------------

    Caravel stores database connection information in its metadata database.
    For that purpose, we use the ``cryptography`` Python library to encrypt
    connection passwords. Unfortunately this library has OS level dependencies.

    You may want to attempt the next step
    ("Caravel installation and initialization") and come back to this step if
    you encounter an error.

    Here's how to install them:

    For **Debian** and **Ubuntu**, the following command will ensure that
    the required dependencies are installed: ::

        sudo apt-get install build-essential libssl-dev libffi-dev python-dev python-pip

    For **Fedora** and **RHEL-derivatives**, the following command will ensure
    that the required dependencies are installed: ::
        
        sudo yum upgrade python-setuptools
        sudo yum install gcc libffi-devel python-devel python-pip python-wheel openssl-devel

    **OSX**, system python is not recommended. brew's python also ships with pip  ::

        brew install pkg-config libffi openssl python
        env LDFLAGS="-L$(brew --prefix openssl)/lib" CFLAGS="-I$(brew --prefix openssl)/include" pip install cryptography

    **Windows** isn't officially supported at this point, but if you want to
    attempt it, download `get-pip.py <https://bootstrap.pypa.io/get-pip.py>`_, and run ``python get-pip.py`` which may need admin access. Then run the following: ::

        C:\> \path\to\vcvarsall.bat x86_amd64
        C:\> set LIB=C:\OpenSSL-1.0.1f-64bit\lib;%LIB%
        C:\> set INCLUDE=C:\OpenSSL-1.0.1f-64bit\include;%INCLUDE%
        C:\> pip install cryptography

        # You may also have to create C:\Temp
        C:\> md C:\Temp


    ### Caravel installation and initialization
    ---------------------------------------
    Follow these few simple steps to install Caravel.::

        # Install caravel
        pip install caravel

        # Create an admin user
        fabmanager create-admin --app caravel

        # Initialize the database
        caravel db upgrade

        # Create default roles and permissions
        caravel init

        # Load some data to play with
        caravel load_examples

        # Start the development web server
        caravel runserver -d


    After installation, you should be able to point your browser to the right
    hostname:port `http://localhost:8088 <http://localhost:8088>`_, login using
    the credential you entered while creating the admin account, and navigate to
    `Menu -> Admin -> Refresh Metadata`. This action should bring in all of
    your datasources for Caravel to be aware of, and they should show up in
    `Menu -> Datasources`, from where you can start playing with your data!

    ### Database dependencies
    ---------------------

    Caravel does not ship bundled with connectivity to databases, except
    for Sqlite, which is part of the Python standard library.
    You'll need to install the required packages for the database you
    want to use as your metadata database as well as the packages needed to
    connect to the databases you want to access through Caravel.

    Here's a list of some of the recommended packages.
    
    1.  sqlite  -> ``sqlite://`` 

    sqlite3 is pre-installed with caravel installation.

    Note that many other database are supported, the main criteria being the
    existence of a functional SqlAlchemy dialect and Python driver. Googling
    the keyword ``sqlalchemy`` in addition of a keyword that describes the
    database you want to connect to should get you to the right place.


3. **How easy it is to upload data?**
    
    Currently it supports only Database (RDBMS) so we initiated our test on SQLlite Database. ( Don't worry by it's name; it's not that difficult. )
    
    * **Shortcut method :**<br>
    1. Making Database file (.db):
        
        if you want to export CSV and visualise it then,

        Mozilla firefox > Download Plugin > [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/) <br>
    2. `Mozilla firefox Tools` > `SQLite Manager` > `Database` > `New Database` > `Select folder` > `Import CSV` > `select file` > `Give Table name, Column name and Types` > `OK!`
    
    You will find new Table under tables.

    `Database` > `Close Database`

    Done! you will find `yourfilename.db` in selected folder.

4. **How easy to create Visualizations?**

    Quiet easy. Login to caravel tool installed on your machine.

    `Sources` > `Databases` > [+] sign

    Add credentials such as Database name.

    Under **Sqlalchemy Uri** - `sqlite:////home/nipunsadvilkar/notebooks/Teamworks_ETL_new.db`

    and **Save!**

    Again Go to `Tables` under `Sources` > [+] sign > Fill credentials and Checkmark desired box > Save!

    Now select just saved Table and select option from Dropdown menu. (Visualisation type, Groupby kind of operation.) and 
    Press **Query** to get results. In seconds you will see visualisation.

5. **How we are planning on using it for ETL project?**

    Most of the times during ETL we need to see 

    1) Tables, Pivot tables -> To get Counts
    2) Bar graphs -> to get Distibution and Finding out Outliers.

    which means Visualisation becomes integral part of understanding data.

    So Casual approach is : everytime we get new data, we always need to write separate code to visualise it. But, this time we took **Smart approach** to visualise same data with Caravel.

    Advantage is THAT , it's just few clicks and we get visualisations ready and on the other hand, we get wide varity of visualisations depending on use cases.

    **Time saving and No need to write any Code and getting bogged down in any error!**

    
**For more information:**

- [Airbnb.io](http://airbnb.io/caravel/)
- [Caravel installation](http://airbnb.io/caravel/installation.html)
- [Caravel Github](https://github.com/airbnb/caravel)
- [How to tutorial](http://airbnb.io/caravel/tutorial.html)

**Get in touch to explore more! I would like to hear your feedback.**
                                                    