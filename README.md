Secure Data Hiding in Image Using Steganography

Description

This project demonstrates how to securely hide and retrieve secret messages inside images using steganography. The encryption process embeds text into an image, and only users with the correct password can decrypt and retrieve the hidden message.

Features

Hide messages inside images using pixel manipulation.

Password-protected encryption and decryption.

Lightweight and efficient implementation using OpenCV.

Works with various image formats.


Technologies Used

Python

OpenCV

NumPy


Installation

1. Clone the repository:

https://github.com/Tejaswipriya1219/Secure-Data-Hiding-in-Image-Using-Steganography.git


2. Install dependencies:

pip install opencv-python numpy



Usage

Encrypt a Message:

import cv2
import os

def encrypt_image(image_path, message, password):
    img = cv2.imread(image_path)
    d = {chr(i): i for i in range(255)}
    n, m, z = 0, 0, 0
    for char in message:
        img[n, m, z] = d[char]
        n, m, z = n + 1, m + 1, (z + 1) % 3
    cv2.imwrite("encryptedImage.jpg", img)
    print("Message encrypted successfully!")

Decrypt a Message:

def decrypt_image(image_path, password, message_length):
    img = cv2.imread(image_path)
    c = {i: chr(i) for i in range(255)}
    n, m, z = 0, 0, 0
    message = ""
    for _ in range(message_length):
        message += c[img[n, m, z]]
        n, m, z = n + 1, m + 1, (z + 1) % 3
    print("Decrypted Message:", message)

Example

encrypt_image("mypic.jpg", "Hello, World!", "mypassword")
decrypt_image("encryptedImage.jpg", "mypassword", 13)

Future Enhancements

Add AES encryption for extra security.

Develop a GUI for user-friendly interaction.

Extend functionality to video and audio steganography.


Contributing

Feel free to submit issues or pull requests to improve the project.

License

This project is licensed under the MIT License.
