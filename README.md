# Simple Blob Website

This is a simple Flask web application featuring animated blobs with an attractive design. It is ready for deployment on Azure App Services.

## Running Locally

1. Make sure you have Python 3.7+ installed.
2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the app:
   ```bash
   python app.py
   ```
5. Open your browser and navigate to `http://localhost:5000`.

## Deployment to Azure App Services (GUI)

1. **Create an Azure App Service:**
   - Log in to the [Azure Portal](https://portal.azure.com).
   - Click **Create a resource** > **Web App**.
   - Fill in the required details (Subscription, Resource Group, Name, Runtime stack: Python 3.9 or later).
   - Choose a region and pricing tier.
   - Click **Review + create** and then **Create**.

2. **Prepare your app for Azure:**
   - Ensure your app listens on the port provided by the environment variable `PORT` (Azure sets this).

   Modify `app.py` to use the port from environment variable:
   ```python
   import os
   
   if __name__ == '__main__':
       port = int(os.environ.get('PORT', 5000))
       app.run(host='0.0.0.0', port=port)
   ```

3. **Deploy your code:**
   - In the Azure Portal, go to your Web App.
   - Under **Deployment**, select **Deployment Center**.
   - Choose your source (e.g., GitHub, Local Git, ZIP Deploy).
   - Follow the instructions to connect your repository or upload your code.

4. **Configure startup command:**
   - In your Web App, go to **Configuration** > **General settings**.
   - Set the **Startup Command** to:
     ```
     python app.py
     ```

5. **Set environment variables (optional):**
   - If you have any environment variables, set them under **Configuration** > **Application settings**.

6. **Browse your app:**
   - Once deployment is complete, click **Browse** to open your live app.

## Notes

- This app uses only Flask and no database.
- The blobs are animated using CSS only.
- For production, consider using a production WSGI server like Gunicorn.

