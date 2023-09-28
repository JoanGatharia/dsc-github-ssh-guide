# Setting up an SSH token for a GitHub Account

The following guide is a concatenation of three different tutorials published by GitHub. The original tutorials are linked at the bottom of the document for reference.


In this document you will set up a [Secure Shell Protocol (SSH)](https://https://en.wikipedia.org/wiki/Secure_Shell) token to access GitHub securely over an unsecured network. When you create a SSH token pair you are using your computer to generate private and public SSH keys. The private key is added to the SSH agent on your local machine, and the public key is added to your GitHub account. When you clone repositories from GitHub using SSH, GitHub compares the public key to your private key to authenticate you as the correct user with the correct permissions. To get started using you will need a GitHub account, to create one [click here](https://github.com/signup)

GitHub's [Connect to SSH documentattion](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh).

Once you have an account, to set up SSH do the following:

1.   Open a terminal window
2.   Paste the following into terminal and replace the email with the email connected to your github account

  > `ssh-keygen -t ed25519 -C "your_email@example.com"`

  You should see an output that looks something like this:

  > `> Generating public/private ed25519 key pair.`

3. You will be prompted to enter a file location for saving the ssh key. Press ENTER which tells to computer to save the key in the default file location

  > `> Enter a file in which to save the key`
  > `(/Users/you/.ssh/id_ed25519): [Press enter]`

4. You will be prompted to enter a passphrase for the ssh key. Press ENTER which instructs the computer not to require a password when using the ssh key

  > `> Enter passphrase (empty for no passphrase): [Type a passphrase]`
  > `> Enter same passphrase again: [Type passphrase again]`

5. Run the following command:

  > `eval "$(ssh-agent -s)"`

6. Run the following in terminal
  * Mac computers
    > `pbcopy < ~/.ssh/id_ed25519.pub`
  * Windows computers
    > `clip < ~/.ssh/id_ed25519.pub`

7. Navigate to the [settings](https://github.com/settings) page on GitHub.

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh07.png/ssh07.png' alt="GitHub Settings" >

8. Select **SSH and GPG keys** from the left side bar.

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh08.png/ssh08.png' alt="GitHub sidebar SSH" >

9. Click **New SSH key** or **Add SSH key**.

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh09.png/ssh09.png' alt="New/Add GitHub SSH" >

10. In the "Title" field, add a descriptive label for the new key. Best to include something about the specific machine you’re working on, since the key should be unique to that environment. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

11. Step 6 stored the ssh key on your clipboard. Click into the **Key** text box and paste the key into the text box.

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh11.png/ssh11.png'  alt="GitHub SSH Textbox" >

12. Click **Add SSH key**

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh12.png/ssh12.png'  alt="GitHub Add SSH Key" >

13. If prompted, confirm your GitHub password.

  <img src= 'https://curriculum-content.s3.amazonaws.com/data-science/images/ssh13.png/ssh13.png'  alt="GitHub Confirm password to continue" >

14. Enter the following in a terminal window

  > `ssh -T git@github.com`

  Note: If you see the following message:

  > `> The authenticity of host 'github.com (IP ADDRESS)' can't be established.`
  > `> RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8`
  > `> Are you sure you want to continue connecting (yes/no)?`

  Enter `yes`

15. If you see the following message, you have successfully connect to github using an ssh key

  > `> Hi username! You've successfully authenticated, but GitHub does not`
  > `provide shell access`

16. Last step is to set ssh as the global authentication protocol by running the following line:

  > `git config --global url.ssh://git@github.com/.insteadOf`
  > `https://github.com`


