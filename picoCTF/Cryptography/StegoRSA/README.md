# StegoRSA

- **Platform:** Verify before publishing
- **Category:** Cryptography / Steganography
- **Difficulty:** Not specified
- **Tools:** ExifTool, CyberChef, OpenSSL

## Objective

Decrypt `flag.enc` using the RSA private key hidden in `image.jpg`.

## Approach

Used ExifTool to inspect the image metadata and found a hexadecimal string in the comment field. Converted it from Hex to Base64 using CyberChef to recover the private key.

## Key Findings

The image metadata contained an encoded RSA private key.

## Solution

Saved the recovered key as `privkey.pem`, including the `BEGIN` and `END` markers, then decrypted the file:

```bash
openssl pkeyutl -decrypt -inkey privkey.pem -in flag.enc -out flag.txt
cat flag.txt
```

## Lessons Learned

Image metadata can contain hidden clues, and encoded data may reveal sensitive information such as a private key.

## References

- [ExifTool](https://exiftool.org/)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [OpenSSL Documentation](https://docs.openssl.org/)

## Flag

`academy{rs4_k3y_1n_1mg_3e14722a}`
