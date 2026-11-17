# Riddle Registry

- **Platform:** picoCTF
- **Category:** Forensics
- **Difficulty:** Easy
- **Tools:** ExifTool, CyberChef

## Objective

Inspect the provided PDF file and find the hidden flag.

## Approach

1. I opened the PDF and noticed some hidden text on the page.
2. I copied the text into a text editor to inspect it more closely. However, it did not reveal anything useful. Even the last message said:

   `No flag here. Nice try though!`

3. Since the visible content did not help, I downloaded the PDF and decided to inspect its metadata.
4. I used ExifTool:

   ```bash
   exiftool confidential.pdf
   ```

5. In the output, I noticed something unusual in the `Author` field:

   ```text
   Author : YWNhZGVteXtwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV82MDZhMGJhOX0=
   ```

6. The string looked like Base64 because it ended with `=`.
7. I copied the string into CyberChef and used the **From Base64** operation.
8. CyberChef decoded the string and revealed the flag.

## Key Findings

- PDF files can contain metadata such as Author and Producer.
- ExifTool can extract metadata that is not visible in the document itself.
- The unusual Author value was Base64-encoded text.
- CyberChef's From Base64 operation revealed the hidden flag.

## Solution

Run ExifTool to inspect the PDF metadata:

```bash
exiftool confidential.pdf
```

Copy the value from the `Author` field and decode it using CyberChef's **From Base64** operation.

**Flag:** `academy{puzzl3d_m3tadata_f0und!_606a0ba9}`

## Lessons Learned

- Always inspect file metadata when investigating suspicious documents.
- PDF metadata can contain hidden information.
- Base64 is an encoding method, not encryption.
- ExifTool and CyberChef are useful tools for basic digital forensics.
