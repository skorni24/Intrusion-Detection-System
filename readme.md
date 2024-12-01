# Setup Instructions for Flask Application with Model Training

## Prerequisites
Before you start, ensure you have the following installed:
- Python 3.x
- pip (Python package installer)

## Steps to Set Up

### 1. Create a Virtual Environment

To isolate dependencies for this project, we will use a Python virtual environment.

1. Navigate to the project directory in your terminal.
2. Create a virtual environment by running the following command:

   ```bash
   python3 -m venv venv
   ```

3. Activate the virtual environment:
   * On Windows:
     ```bash
     venv\Scripts\activate
     ```

   * On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

### 2. Install Required Packages
Once the virtual environment is activated, install the required dependencies for the project:

```bash
pip install -r requirements.txt
```

Ensure that your `requirements.txt` contains the necessary libraries, such as:
* Flask
* scikit-learn
* pandas
* numpy
* Jupyter (for running notebooks)
* other relevant libraries you may need

### 3. Run the Model Training (`main.ipynb`)
1. Navigate to the `models` folder.
2. Open the `main.ipynb` Jupyter notebook:

   ```bash
   jupyter notebook main.ipynb
   ```

3. Run all cells in the notebook to train the models and generate the model files (`kdd.pkl` and `sk.pkl`).
   * **Note**: Ensure that the training process completes without errors. The models will be saved in the `models` folder as `kdd.pkl` and `sk.pkl`.

### 4. Move Model Files to Main Directory
After training, you should see two model files in the `models` folder:
* `kdd.pkl`
* `sk.pkl`

Move these files to the main project directory:

```bash
mv models/kdd.pkl .
mv models/sk.pkl .
```

### 5. Run the Flask Application
Now that the models are in the main directory, you can start the Flask application.

1. Navigate to the main project directory if you are not already there.
2. Run the Flask application by executing the following command:

   ```bash
   flask run
   ```

   Alternatively, you can run it using the following command if you are using `app.py`:

   ```bash
   python app.py
   ```

3. The Flask application should now be running on `http://127.0.0.1:5000/` (default address). You can visit this URL in your web browser to interact with the app.

### 6. Deactivate the Virtual Environment (Optional)
Once you're done with the project, you can deactivate the virtual environment by running:

```bash
deactivate
```

This will return you to the system's default Python environment.

## Troubleshooting
* If you face issues related to missing dependencies or package versions, ensure that your `requirements.txt` file is up to date, and reinstall the dependencies using `pip install -r requirements.txt`.
* If there are errors in the model training (`main.ipynb`), check that all required datasets are present and correctly loaded in the notebook.




