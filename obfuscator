import requests
import subprocess
import tempfile
import os

def run_github_code(github_url):
    # Download the code from the GitHub repository
    response = requests.get(github_url)
    if response.status_code != 200:
        print(f"Failed to download code from {github_url}")
        return

    # Create a temporary directory to store the downloaded code
    temp_dir = tempfile.mkdtemp()
    temp_file_path = os.path.join(temp_dir, "code.py")

    # Save the downloaded code to a temporary file
    with open(temp_file_path, "w") as temp_file:
        temp_file.write(response.text)

    # Run the downloaded code using subprocess
    try:
        subprocess.run(["python", temp_file_path], check=True)
    except subprocess.CalledProcessError:
        print("Failed to run the code.")
    finally:
        # Clean up the temporary directory
        os.remove(temp_file_path)
        os.rmdir(temp_dir)

# Example usage
github_repo_url = "https://raw.githubusercontent.com/username/repo/main/code.py"
run_github_code(github_repo_url)
