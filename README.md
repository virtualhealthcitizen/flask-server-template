# flask-server-template

[![Tests](https://github.com/squidmin/flask-server-template/actions/workflows/python-app.yml/badge.svg)](https://github.com/squidmin/flask-server-template/actions/workflows/python-app.yml)

Template for Flask server development.

Created using <a href = "https://www.python.org/downloads/release/python-3110/">Python v3.11</a>.

### Install Flask

`pip3 install Flask`

Read more about Flask installation <a href="https://flask.palletsprojects.com/en/2.2.x/installation/">here</a>.

### Building and Running the Docker Container

1. **Build the Docker Image**

   Navigate to the directory containing the Flask app and `Dockerfile`, and run:

   ```bash
   docker build -t flask-sample-app .
   ```

   This command builds a Docker image named `flask-sample-app` based on the instructions in the `Dockerfile`.

2. **Run the Docker Container**

   After the image has been successfully built, you can run your Flask app inside a Docker container using:

   ```bash
   docker run --rm -p 5000:5000 \
     -e GOOGLE_APPLICATION_CREDENTIALS=${GOOGLE_APPLICATION_CREDENTIALS} \
     -e PORT=5000 \
     -v $HOME/.config/gcloud:/root/.config/gcloud \
     -v $HOME/.m2:/root/.m2 \
     flask-sample-app
   ```

   This command runs the Flask application inside a Docker container, mapping port 5000 of the container to port 5000 on your host, allowing you to access the Flask app by visiting `http://localhost:5000` in your web browser.

### Using Podman

If you prefer using Podman, the commands are very similar:

1. **Build the Image**

   ```bash
   podman build -t flask-sample-app .
   ```

2. **Run the Container**

   ```bash
   podman run -p 5000:5000 flask-sample-app
   ```

### Running the application without containers

To run the app without containers, run this command In the project root directory:

`python3 -m flask run`

### Running the tests

```shell
python -m unittest test_app.py
```

You can find the Flask quickstart page <a href="https://flask.palletsprojects.com/en/2.2.x/quickstart/">here</a>.

---

<details>
  <summary>Installing virtualenv</summary>
  
  1. `cd` into the project root directory

  2. `python3 -m venv venv_name`

  The above steps create a `venv/` directory in your project where all dependencies are installed. The virtual environment needs to be activated in every terminal instance used for work in the project:

  `source venv/bin/activate`

  You should see a `(venv)` appear at the beginning of your terminal prompt indicating that you are working inside the `virtualenv`.
  
  Now when you install something like this:

  `pip install <package>`

  it will be installed to the `venv` folder and not conflict with dependencies in other projects.
</details>

<details>
  <summary>Leaving the virtual environment</summary>

  To leave the virtual environment, run:
  `deactivate`
</details>

<details>
  <summary>Run a script</summary>
  
  `python3 (script_name).py`
</details>

---

For more info about `virtualenv` and installation, see:

https://sourabhbajaj.com/mac-setup/Python/virtualenv.html


For more info about `virtualenv` installation issues, see:

https://stackoverflow.com/questions/31133050/virtualenv-command-not-found
