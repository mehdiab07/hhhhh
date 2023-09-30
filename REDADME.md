import time
import configparser

# Function to read configuration settings from a file
def read_config():
    config = configparser.ConfigParser()
    config.read('config.ini')
    return config['WelcomeBot']

# Function to send a welcome message
def send_welcome_message():
    config = read_config()
    welcome_message = config.get('welcome_message', 'Welcome to the Coding Bot!')
    delay = config.getint('delay', 2)

    print(welcome_message)
    print("I'm here to help you with your coding tasks.")
    print("Feel free to ask me any questions or request assistance.")

    time.sleep(delay)

if __name__ == "__main__":
    send_welcome_message()
