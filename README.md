# -Barcode-Encoder-and-Decoder

This project implements a simplified barcode generation and decoding system using basic computer vision concepts. The task simulates how barcodes are visually encoded from text and then reconstructed back into the original string by scanning the generated image. The system has two parts: an ENCODER that creates a barcode image from a given string, and a DECODER that reads the image and converts it back to the original text.
	1.	ENCODER (Image Generation)

The encoder receives a text string and transforms it into a barcode image following the assignment specification.

Canvas:
• The output is a blank image of size 400 x 800 pixels.
• Bars are drawn vertically across fixed height ranges:
– Normal bars: from row 10 to row 350
– Space bars (empty space): from row 150 to row 250

Bar Width Rules:
• Each bar is drawn starting at a fixed step size of 9 pixels horizontally.
• A space between characters is represented as a bar of width 1 pixel.
• Every alphabetic character (case-insensitive) is encoded as a bar whose width equals (alphabet index + 1).
Examples:
– ‘A’ or ‘a’ → 2 pixels
– ‘B’ or ‘b’ → 3 pixels
– ‘S’ or ‘s’ → 20 pixels

Encoding Process:
• The encoder loops through the string character by character.
• For each character:
– Determine bar width based on the rules above.
– Draw a vertical bar at the correct horizontal offset.
• The final image is saved as “Output.png” (PNG format only).
	2.	DECODER (Image Reconstruction)

The decoder reverses the encoding process and reconstructs the string by scanning the barcode.

Scanning Method:
• The decoder reads “Output.png”.
• It scans horizontally along the central row (row 200).
• It measures the width of each continuous black bar.

Decoding Logic:
• If the bar width equals 1 → this is a space → append “ “ to the output string.
• Otherwise:
– The character index is (width - 1).
– Convert this index back to its alphabet letter.
– Append the character to the output string.

Final Output:
• The decoded string (Str) must match the input text used to generate the barcode (case ignored).
	3.	Required Submissions

To Canvas:
A) The encode file (Python or MATLAB)
– encode(“Your Name”) generates Output.png

B) The decode file (Python or MATLAB)
– Str = decode(“Output.png”) reconstructs the original text

C) A screenshot of the submission page from the test website

To the test website:
• Generate your personalised test barcode from the link provided.
• Use your decoder to obtain the barcode string.
• Submit the decoded string online (up to 3 attempts).

Summary

Overall, this project simulates a basic computer-vision pipeline: image synthesis using geometric rules and image interpretation by pixel analysis. The encoder and decoder must mirror each other precisely so that the original text is recovered correctly from the generated barcode image.
