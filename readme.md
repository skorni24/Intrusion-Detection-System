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



# Network Traffic Dataset Columns and Definitions

1. **Id**
   - **Definition**: A unique identifier for each record.
   - **Example**: 1, 2, 3, ..., 1000

2. **duration**
   - **Definition**: The duration of the connection in seconds.
   - **Example**: 0, 10, 25, 5 (higher values may indicate long-lasting connections)

3. **protocol_type**
   - **Definition**: The protocol used in the connection (e.g., TCP, UDP, ICMP).
   - **Example**: tcp, udp, icmp

4. **service**
   - **Definition**: The service that is being accessed (e.g., HTTP, FTP, SSH).
   - **Example**: http, ftp_data, smtp

5. **flag**
   - **Definition**: The status of the connection (e.g., SF, S0, REJ).
   - **Example**: SF, S0, REJ

6. **src_bytes**
   - **Definition**: The number of bytes sent from the source (client).
   - **Example**: 146, 232, 491

7. **dst_bytes**
   - **Definition**: The number of bytes received by the destination (server).
   - **Example**: 0, 8153, 420

8. **land**
   - **Definition**: Indicates whether the source and destination IP addresses are the same (used for certain attacks).
   - **Example**: 0 (normal), 1 (attack)

9. **wrong_fragment**
   - **Definition**: The number of wrong fragments in a packet.
   - **Example**: 0, 1, 2 (indicates an error in packet fragmenting)

10. **urgent**
    - **Definition**: The number of urgent packets.
    - **Example**: 0, 5, 10 (higher values might indicate urgent data, such as in attacks)

11. **hot**
    - **Definition**: The number of hot indicators, which may refer to abnormal behaviors or sensitive information.
    - **Example**: 0, 2, 5

12. **num_failed_logins**
    - **Definition**: The number of failed login attempts.
    - **Example**: 0, 1, 3 (higher values may indicate a brute-force attack)

13. **logged_in**
    - **Definition**: Indicates whether the user is logged in (1 if logged in, 0 if not).
    - **Example**: 1, 0 (1 indicates login, 0 indicates no login)

14. **num_compromised**
    - **Definition**: The number of compromised accounts in the session.
    - **Example**: 0, 1, 5 (higher numbers may indicate a breach)

15. **root_shell**
    - **Definition**: Whether the connection was given root access (1 for root access, 0 for no root access).
    - **Example**: 0, 1

16. **su_attempted**
    - **Definition**: Whether a "su" (superuser) command was attempted (1 if attempted, 0 if not).
    - **Example**: 1, 0

17. **num_root**
    - **Definition**: The number of root accesses.
    - **Example**: 0, 2, 10

18. **num_file_creations**
    - **Definition**: The number of files created during the session.
    - **Example**: 0, 5, 10

19. **num_shells**
    - **Definition**: The number of shells opened during the session.
    - **Example**: 0, 1, 2

20. **num_access_files**
    - **Definition**: The number of files accessed during the session.
    - **Example**: 0, 3, 10

21. **num_outbound_cmds**
    - **Definition**: The number of outbound commands (usually for malicious actions).
    - **Example**: 0, 1

22. **is_host_login**
    - **Definition**: Whether the login is a host login (1 for host login, 0 for not).
    - **Example**: 1, 0

23. **is_guest_login**
    - **Definition**: Whether the login is a guest login (1 for guest login, 0 for not).
    - **Example**: 0, 1

24. **count**
    - **Definition**: The number of connections to the same host in the past 2 seconds.
    - **Example**: 5, 10, 20

25. **srv_count**
    - **Definition**: The number of connections to the same service in the past 2 seconds.
    - **Example**: 3, 8, 15

26. **serror_rate**
    - **Definition**: The rate of connections that generated "SYN" errors.
    - **Example**: 0.0, 0.2, 0.5 (higher rates may indicate errors in communication)

27. **srv_serror_rate**
    - **Definition**: The rate of connections to the same service that generated "SYN" errors.
    - **Example**: 0.0, 0.1, 0.3

28. **rerror_rate**
    - **Definition**: The rate of connections that generated "REJ" errors (e.g., rejected connections).
    - **Example**: 0.0, 0.1, 0.4

29. **srv_rerror_rate**
    - **Definition**: The rate of connections to the same service that generated "REJ" errors.
    - **Example**: 0.0, 0.1, 0.5

30. **same_srv_rate**
    - **Definition**: The rate of connections to the same service.
    - **Example**: 1.0, 0.5, 0.2 (closer to 1 indicates similar service connections)

31. **diff_srv_rate**
    - **Definition**: The rate of connections to different services.
    - **Example**: 0.0, 0.1, 0.3

32. **srv_diff_host_rate**
    - **Definition**: The rate of connections to different hosts for the same service.
    - **Example**: 0.0, 0.1, 0.2

33. **dst_host_count**
    - **Definition**: The number of connections to the destination host.
    - **Example**: 100, 250, 50

34. **dst_host_srv_count**
    - **Definition**: The number of connections to the same service at the destination host.
    - **Example**: 10, 20, 50

35. **dst_host_same_srv_rate**
    - **Definition**: The rate of connections to the same service at the destination host.
    - **Example**: 0.8, 0.5, 0.9

36. **dst_host_diff_srv_rate**
    - **Definition**: The rate of connections to different services at the destination host.
    - **Example**: 0.2, 0.1, 0.3

37. **dst_host_same_src_port_rate**
    - **Definition**: The rate of connections from the same source port to the destination host.
    - **Example**: 0.5, 0.7, 0.9

38. **dst_host_srv_diff_host_rate**
    - **Definition**: The rate of connections to different destination hosts for the same service.
    - **Example**: 0.1, 0.05, 0.3

39. **dst_host_serror_rate**
    - **Definition**: The rate of connections to the destination host that generated SYN errors.
    - **Example**: 0.0, 0.1, 0.2

40. **dst_host_srv_serror_rate**
    - **Definition**: The rate of connections to the destination host that generated SYN errors for the same service.
    - **Example**: 0.0, 0.1, 0.3

41. **dst_host_rerror_rate**
    - **Definition**: The rate of rejected connections to the destination host.
    - **Example**: 0.0, 0.1, 0.4

42. **dst_host_srv_rerror_rate**
    - **Definition**: The rate of rejected connections to the destination host for the same service.
    - **Example**: 0.0, 0.1, 0.5

43. **labels**
    - **Definition**: The category label for each record (either normal or a specific attack type like neptune, smurf, etc.).
    - **Example**: normal, neptune, smurf, back, teardrop


