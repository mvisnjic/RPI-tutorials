![google-auth-logo](https://imgs.search.brave.com/cVBBbILbEJQmNpcAZN1UBunpfS5VtRHdkCTe5Anhs50/rs:fit:299:299:1/g:ce/aHR0cHM6Ly9pMC53/cC5jb20vYXBwc2xv/dmEuY29tL3dwLWNv/bnRlbnQvdXBsb2Fk/cy8yMDE4LzAzL0dv/b2dsZS1BdXRoZW50/aWNhdG9yLWxvZ28u/anBn)

# Setup a google authenticator

1. Installing
   `sudo apt-get install libpam-google-authenticator`

2. Configure sshd_config
   `sudo nano /etc/ssh/sshd_config`
   Find `ChallengeResponseAuthentication` and change to `yes`

   Exit nano - Ctrl+x and y and hit enter

   ![screenshot-sshd-config](Screenshot%20from%202023-03-18%2011-27-36.png)

3. Navigate to `sudo nano /etc/pam.d/sshd` - [More about PAM](https://www.tecmint.com/configure-pam-in-centos-ubuntu-linux/)
   Add 2fa before @include common-auth. You need to enter 2fa code first, then your password.

   - `auth required pam_google_authenticator.so`
     ![screenshot-pam.d-sshd](Screenshot%20from%202023-03-18%2011-37-45.png)

4. `sudo systemctl restart ssh`

- Now when you configure these settings, you can type `google-authenticator` and follow on screen instruction.

  1. Time-based tokens - `y`
     1. Scan QR code or enter secret key in google authenticator app
     2. Enter code from a google auth
     3. Save your emergency codes on a safe place
  2. Update your /home/pi/.google_authenticator file - `y`
  3. Disallowing multiple uses of same token - `y`
  4. Poor synchronization adjustment - `n`
  5. Limit to 3 logins per 30 seconds - `y`

Try if it works

![check-google-auth](Screenshot%20from%202023-03-18%2011-53-14.png)

You have successfully setup a google-auth, if you want to setup a fail2ban check [this](https://github.com/mvisnjic/RPI-tutorials/tree/main/setup-fail2ban)
