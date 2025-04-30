# John-the-Ripper

## Objective
I wanted to utilize John the Ripper to do some testing on password hashes in Kali Linux. For this I want to break a some hashes for user passwords using John and a pre-installed wordlist on Kali. I also want to be able to crack a locked zip file that is password protected.

## Skills Learned
- Ability to find hashes for user passwords
- Knowledge in using John the Ripper to crack hashes
- Understanding of bypassing a password on a zipped file

## Tools Used
- Virtualbox
- Kali Linux
- John the Ripper

## Steps

1. First I created one user named david with an easy password of password123 to test on first. I went to /etc/shadow as root and scrolled down the bottom to copy the password hash for david. This inforamtion will be pasted into a file called hash.txt .  ![Screenshot 2025-04-29 155910](https://github.com/user-attachments/assets/3c7c6fbd-b0e2-4eeb-afe5-13bee22d383a)
![Screenshot 2025-04-29 160010](https://github.com/user-attachments/assets/d52225f3-9eea-4131-8672-b1bb915594b0)

2. Next we are going to use a pre-installed wordlist on Kali Linux called rockyou.txt in /usr/share/wordlists directory to test davids password hash. Going to run   sudo john -format=crypt --wordlist=/usr/share/wordlist/rockyou.txt hash.txt    which will run John the Ripper using crypt foramt, since my hash starts with $y$, and using the rockyou.txt wordlist. The simple password was cracked in less than a second for david.
![Screenshot 2025-04-29 160550](https://github.com/user-attachments/assets/bfba4aab-ca75-45b1-b765-0e01240f1a13)

3. After my test run I wanted to try on password protected zip file to see if I could breach it using John. Made a secret.txt file and password protected the zip file made out of it into secret.zip.
![Screenshot 2025-04-29 160708](https://github.com/user-attachments/assets/e3cbf1f7-bd1e-423d-9a3d-8294cc3a78aa)
![Screenshot 2025-04-29 160949](https://github.com/user-attachments/assets/3cfac036-e53c-4df4-b4af-dfc1e8cae958)

4.  I used zip2john command to get a hash out of zip file first. Then I put a few random passowrds with the real one into my own list(passwords.txt. to use to see if I can get my own list to work. Then same command as earlier, but slightly different with  sudo john --wordlist=passwords.txt zip.hash  to run through the hash and match it with the correct one on my list. 
![Screenshot 2025-04-29 161253](https://github.com/user-attachments/assets/5575044b-4eab-4581-8276-43769ea38bd1)
![Screenshot 2025-04-29 161635](https://github.com/user-attachments/assets/6852d5d9-05d6-41ba-8680-e3edd9d6f59b)
