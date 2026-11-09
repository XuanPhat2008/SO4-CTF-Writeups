# Challenge Name: Scan Surprise

- **Platform:** picoCTF
- **Category:** Forensics
- **Difficulty:** Easy
- **Tools:** File Explorer, QR Code Scanner

## Objective

Find the hidden flag in the provided ZIP file.

## Approach

First, download and extract the ZIP file. Then, navigate through the directories until you reach the last folder, which contains an image.

Open the image and you will see a QR code. Scan it using your phone or an online QR code scanner to reveal the flag.

## Key Findings

The image contains a QR code that stores the flag.

## Solution

Scan the QR code to retrieve the flag:

`academy{p33k_@_b00_36769c4b}`

## Lessons Learned

QR codes can store text or other information. In forensic challenges, always check images for hidden or encoded data.

## References

- [QR Code](https://en.wikipedia.org/wiki/QR_code)
