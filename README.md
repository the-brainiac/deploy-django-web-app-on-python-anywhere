# Deploying a Django Web-app on Python-anywhere

- First of all you have to make an account on [python anywhere](https://www.pythonanywhere.com/login/) then login to your account.
## Open Bash Terminal.
-  **Clone your github repo**
    ```
    git clone REPO_URL
    ```
    where REPO_URL is the address of your github repository.  
    *You may need your ID and Password if your repo is private. 
-  **Make a virtual enviornment**
    ```
    mkvirtualenv --python=/usr/bin/python3.8 ENV_NAME
    ```
    replace the 3.8 with the version of your python in which the app is made (recommended 3.6 or higher) 
    - Use this command to check the version of your python
        ```
        python3 -V
        ```
    replace the ENV_NAME with the name of enviornment that you want to give.
- **Go to the directory of your app**
    ```
    cd NAME_OF_YOUR_PROJECT
    ```
-  **Installing all the dependencies**  
    If you have your requirements.txt file then run
    ```
    pip install -r requirements.txt
    ```
    otherwise you have to install all apps seperately.  
    After installing all packages run
    ```
    python manage.py check
    ```
    If you see any error then resolve then untll there is no error.
    After resolving all errors run (don't forget to setup your root to `staticfiles` if haven't done already.) 
    ```
    python manage.py collectstatic
    ```

## Go to the Web section
- create new app and then select manual configuration use the correct version of your python and then finish this small setup.
- set your virtual enviornment.
- open the `wsgi.py` file and erase everything and then paste the followoing code or you can do this manually accordingly.
    ```    
    # +++++++++++ DJANGO +++++++++++
    # To use your own django app use code like this:
    import os
    import sys
    #
    ## assuming your django settings file is at '/home/USERNAME/PROJECT_NAME/PROJECT_NAME/settings.py'
    ## and your manage.py is is at '/home/USERNAME/PROJECT_NAME/manage.py'
    path = '/home/USERNAME/PROJECT_NAME'
    if path not in sys.path:
        sys.path.append(path)
    #

    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'PROJECT_NAME.settings')

    #
    ## then:
    from django.core.wsgi import get_wsgi_application
    application = get_wsgi_application()
    ```
    - ### Setting static files
        paste these lines in

        | URL             | DIRECTORY                                      | DELETE        |
        | -------------   |:----------------------------------------------:|:-------------:|
        | `/static/`      | `/home/shivshanker/portfolio/staticfiles/`     |

    That's it now click on reload your app will be live if you have followed everything accordingly.