# Intern_Innovators
Automatic_parking_system


The consisit of 
1.detect.py
2.front.ui
3.images
4.mainCar.py
5.mes.py


1.detect.py
          The provided Python script, named `detect.py`, is designed for license plate detection in images using the OpenCV library. The script performs several image processing steps to identify and extract potential license plate regions from the input image. Below is a summary of the key components and functionalities of the script:
      
      1. **Library Import:**
         - The script starts by importing the necessary libraries, primarily OpenCV (`cv2`) and NumPy.
      
      2. **Image Loading:**
         - The input image is loaded using OpenCV's `cv2.imread` function.
      
      3. **Preprocessing:**
         - The script converts the color image to grayscale (`cv2.cvtColor`) to simplify subsequent processing steps.
         - Gaussian blur (`cv2.GaussianBlur`) is applied to reduce noise in the image, which helps improve the accuracy of edge detection.
      
      4. **Edge Detection:**
         - The Canny edge detector (`cv2.Canny`) is used to identify edges in the image, highlighting potential boundaries of objects.
      
      5. **Contour Detection:**
         - Contours in the edged image are identified using `cv2.findContours`.
         - The contours are filtered based on their area, retaining only those within a specified range. This helps in identifying potential license plate regions.
      
      6. **License Plate Extraction:**
         - The script sorts the potential license plate contours based on their area in descending order.
         - It then loops through the top contours and creates a binary mask for each contour.
         - The original image is bitwise AND-ed with the mask to extract the region corresponding to the license plate.
      
      7. **Visualization:**
         - The script displays the original image with bounding boxes drawn around the potential license plate regions. This allows for visual verification of the detection results.
      
      8. **Saving Extracted Plates:**
         - The extracted license plate regions are saved as separate images (e.g., 'plate_1.png', 'plate_2.png').
      
      9. **Usage:**
         - The script is structured to be executed as the main program. The user needs to replace the placeholder image path (`'path_to_your_image.jpg'`) with the actual path of the image they want to process.
      
      10. **Adjustable Parameters:**
         - The script includes parameters such as area thresholds that can be fine-tuned based on specific image characteristics and requirements.
      
      therefore ,`detect.py` provides a foundation for license plate detection in images, leveraging OpenCV's capabilities for edge detection, contour analysis, and image manipulation. Users can adapt and extend this script based on their specific use cases and datasets, adjusting parameters and incorporating additional features as needed.
2.front.ui
    The provided XML code represents the structure of a user interface (UI) designed using the Qt framework. The UI is intended for a car parking management system, as indicated by the `<class>` element with the value "CarParkingManager." Let's break down the XML structure and its components.
    
    The UI is defined using version 4.0 of the Qt UI definition language. The main window is specified as a QMainWindow with a particular geometry, minimum size, maximum size, and window title ("Car Parking Manager"). The central widget is a QWidget, and within it, there is a QFrame named "frame" that serves as a container for various user interface elements.
    
    The frame has specific properties such as geometry, font, style sheet, frame shape, and frame shadow. It is set with a dark background color using a style sheet. Inside the frame, there are several QPushButton widgets (s1 to s16), each representing a parking spot. These buttons are styled with a green background color and a specific font.
    
    The labels for the parking spots range from 1 to 16 and are positioned at different coordinates within the frame. Each button has a specific geometry, font, focus policy, layout direction, style sheet, and text label.
    
    There is also a QLabel widget named "label" positioned above the parking spot buttons, displaying the text "CAR PARKING MANAGEMENT." It has a specific font, style sheet for text color, text content, and text alignment.
    
    Further down, there is a QLineEdit widget named "lineEdit," which is a single-line text input for entering the vehicle number. It has specific properties such as geometry, font, style sheet for border-radius, alignment, and a placeholder text.
    
    Two QPushButton widgets named "ENTRYBUTTON" and "EXITBUTTON" are present for handling entry and exit actions. They are styled with specific background colors, border-radius, and text color. The "ENTRYBUTTON" has a hover effect defined in its style sheet.
    
    Finally, there is another QLabel widget named "label_2" positioned below the buttons, which appears to be a status or information label. It has specific properties for font, style sheet, text color, text content, and text alignment.
    
    In summary, the provided XML defines a Qt-based UI for a car parking management system with buttons representing parking spots, an entry/exit interface, and labels for informational purposes. The UI is visually styled using fonts, colors, and style sheets to create an appealing and user-friendly interface for managing parking spaces.

3.images
  to upend the images for detected the car and the number plagte of the car.

4.mainCar.py
              The provided Python script is a simple parking management system implemented using PyQt5 for the graphical user interface and MySQL for data storage. Here's a summary of its functionality:
            
            ### Database Setup:
            - Connects to a MySQL database with credentials for host, user, password, and database name.
            - Creates five tables (`slot`, `entry`, `exits`, `duration`, `cost`) to store information related to parked cars, entry times, exit times, durations, and costs.
            
            ### GUI Setup:
            - Utilizes PyQt5 to create a graphical user interface for the parking management system.
            - GUI includes buttons for entry and exit operations (`ENTRYBUTTON` and `EXITBUTTON`), as well as slots (`s1` to `s16`) representing parking spaces.
            - The color of slots changes dynamically based on availability.
            
            ### Core Functions:
            1. **`xd` Function:**
               - Checks for duplicate car numbers in the database.
               - Calls `bla` function if the car number is not a duplicate.
            
            2. **`bla` Function:**
               - Checks if the car number is empty and calls the `blank` function.
               - Otherwise, calls the `entry` function.
            
            3. **`entry` Function:**
               - Assigns a parking slot to a car.
               - Updates the database with the car's entry information.
               - Updates the GUI to reflect the occupied parking slots.
            
            4. **`blank` Function:**
               - Displays "Empty" in the GUI label.
            
            5. **`exit` Function:**
               - Handles the exit of a car.
               - Calculates parking duration and cost based on entry and exit times.
               - Updates the database with exit information, duration, and cost.
               - Updates the GUI to reflect available parking slots.
            
            ### Main Function:
            - Initializes the PyQt application and displays the GUI.
            
            ### Note:
            - The function named `exit` should be renamed to avoid conflicts with the built-in `exit` function.
            
            This script provides a basic framework for a parking management system, and further customization or enhancements can be made based on specific project requirements.


5.mes.py

The provided Python script seems to be a part of a parking management system that sends messages for entry and exit events. Below is a summary of the key functionalities:

### Libraries:
- `re`: Regular expression library.
- `requests`: Used for making HTTP requests.
- `mysql.connector`: Handles MySQL database connections.
- `numpy`, `cv2`, `imutils`, `pytesseract`: Libraries for working with images and text extraction.
- `pandas`: Used for data manipulation.
- `time`: Provides time-related functions.

### Functions:
1. **`entryMessage` Function:**
    - Sends an entry message to the car owner.
    - Constructs a message with the car owner's name, allocated parking slot, and a link to view the parking map.
    - Uses the Fast2SMS API to send the message via SMS.
    - The message includes the car owner's name, allocated parking slot, and a link to the parking map.
  
2. **`exitMessage` Function:**
    - Sends an exit message to the car owner.
    - Constructs a message with the parking fee amount and a link for the car owner to pay using UPI.
    - Uses the Fast2SMS API to send the message via SMS.
    - The message includes the parking fee amount and a link for payment using UPI.

### Note:
- Hardcoded values such as the car owner's name, parking slot number, phone number, and UPI ID are used for demonstration purposes. In a real-world application, these values would likely come from database queries or user input.

### Actions:
- The script currently demonstrates the exit message functionality. To see the entry message functionality, uncomment the `entryMessage()` function call at the end of the script.
- The messages are sent using the Fast2SMS API. Ensure that the API key and other details are correctly configured for the messages to be sent successfully.

### Improvement:
- The script could benefit from additional error handling and validation, especially for the API responses.
- The use of hardcoded values should be replaced with dynamic data from the database or user input in a production environment.
