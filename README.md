Image and Video Steganography in python.

• Image Steganography : As the name suggests, Image Steganography refers to the process of hiding data within an image file. The image selected for this purpose is called the cover-image and the image obtained after steganography is called the stego-image.
• Video Steganography : As the name suggests, Video Steganography refers to the process of hiding data within a Video file. The data is hidden inside a particular frame of the video file. In this OEP, we are going to use a method known as Least Significant Bit (LSB) transformation to hide the data inside a

Understanding the Process of Image Steganography

• How is it done? An image is represented as an NM (in case of greyscale images) or NM*3 (in case of colour images) matrix in memory, with each entry representing the intensity value of a pixel. In image steganography, a message is embedded into an image by altering the values of some pixels, which are chosen by an encryption algorithm. The recipient of the image must be aware of the same algorithm in order to known which pixels he or she must select to extract the message.

Every byte of data is converted to its 8-bit binary code using ASCII values. Now pixels are read from left to right in a group of 3 containing a total of 9 values. The first 8-values are used to store binary data. The value is made odd if 1 occurs and even if 0 occurs. For example : Suppose the message to be hidden is 'Hii'. Since the message is of 3-bytes, therefore, pixels required to encode the data is 3 x 3 = 9. Consider a 4 x 3 image with a total 12-pixels, which are sufficient to encode the given data.

[(27, 64, 164), (248, 244, 194), (174, 246, 250), (149, 95, 232), (188, 156, 169), (71, 167, 127), (132, 173, 97), (113, 69, 206), (255, 29, 213), (53, 153, 220), (246, 225, 229), (142, 82, 175)]

ASCII value of ‘ H ‘ is 72 whose binary equivalent is 01001000. Taking first 3-pixels (27, 64, 164), (248, 244, 194), (174, 246, 250) to encode. Now change the pixel to odd for 1 and even for 0. So, the modifies pixels are (26, 63, 164), (248, 243, 194), (174, 246, 250). Since we have to encode more data, therefore, the last value should be even. Similarly, ‘i‘ can be encoded in this image. The new image will look like :

[(26, 63, 164), (248, 243, 194), (174, 246, 250), (148, 95, 231), (188, 155, 168), (70, 167, 126), (132, 173, 97), (112, 69, 206), (254, 29, 213), (53, 153, 220), (246, 225, 229), (142, 82, 175)] • Detection of the message within the cover-image is done by the process of steganalysis . This can be done through comparison with the cover image, histogram plotting, or by noise detection. While efforts are being invested in developing new algorithms with a greater degree of immunity against such attacks, efforts are also being devoted towards improving existing algorithms for steganalysis, to detect exchange of secret information between terrorists or criminal elements.

Understanding the Process of Video Steganography

• Each time we deal with videos, we are actually dealing with the sequence of frames themselves. Each frame is just an image, which might be represented as an m x n array of pixels, where (m,n) is picture size. Each pixel might be represented as colour intensity, depending on which colour model we are using (gray-scale, RGB,BGR).

• For implementing Video Steganography, we took a frame from the input video (Frame 35). Frame 35 is selected by us, it can be any number but should be kept within the limit of total number of frames.

• The library used in this process is stegano. This library makes use of the LSB (Least Significant Bit) technique.

• As an example, suppose that we have three adjacent pixels (nine bytes) with the following RGB encoding: 10010101 00001101 11001001 10010110 00001111 11001010 10011111 00010000 11001011

• Now suppose we want to "hide" the following 9 bits of data (the hidden data is usually compressed prior to being hidden): 101101101. If we overlay these 9 bits over the LSB of the 9 bytes above, we get the following (where bits in bold have been changed): 10010101 00001100 11001001 10010111 00001110 11001011 10011111 00010000 11001011

ABOUT THE CODE

Libraries for Python like cv2 and Stegano have been used.
