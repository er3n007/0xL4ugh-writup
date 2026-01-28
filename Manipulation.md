Manipulation – Forensic Write-Up
The challenge provided a compressed file named Manipulation.7z.
I extracted the archive using a standard unzip tool, which revealed an image file.

Step 2: Analysis Using Autopsy
To analyze the image, I loaded it into Autopsy for forensic examination.
While reviewing the Data Artifacts section, I discovered an unusual file
<img width="1319" height="340" alt="image" src="https://github.com/user-attachments/assets/9f09395b-711a-4e7a-8228-f7b0e0d0788d" />
secret.txt:Zone.Identifier
This immediately stood out because Zone.Identifier is an NTFS Alternate Data Stream (ADS), often used to store metadata about a file’s origin (such as whether it was downloaded from the internet).
Step 3: Inspecting the Zone.Identifier
Upon examining the contents of secret.txt:Zone.Identifier, I noticed it contained an HTTP URL referencing GitHub.
This suggested that the original secret.txt file was downloaded from GitHub, and its source URL had been preserved inside the Zone.Identifier stream.
<img width="1312" height="186" alt="image" src="https://github.com/user-attachments/assets/b8dc9d09-ee10-4023-95ef-90b6718fd2be" />
Step 4: Understanding GitHub Attachments
GitHub allows users to upload files as attachments in:
Issues
Pull requests
Comments
These attachments are hosted using the following format:
https://github.com/user-attachments/files/{unique_id}/{filename},
https://github.com/user-attachments/files/846622427/secret.txt,
https://github.com/user-attachments/files/24846253/secret.txt.
From the Zone.Identifier data, I was able to extract the unique_id associated with secret.txt:Zone.Identifier
Step 5: Retrieving the File
Using the extracted unique_id, I constructed the GitHub attachment URL and downloaded the file directly from GitHub.
Inside the retrieved file, the flag was revealed.
<img width="1400" height="584" alt="image" src="https://github.com/user-attachments/assets/ffc3a0ad-de0d-4f95-9c1d-a43b7083730e" />
0xL4ugh{Disc1plin3d_0n_duty_Rel3ntless_0ff_1t}









