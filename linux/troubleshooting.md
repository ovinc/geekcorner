# Troubleshooting

## Ubuntu does not wake up after remote session

Solution can be found here:
https://askubuntu.com/questions/1503522/logging-in-after-remoting-to-my-ubuntu-pc-shows-a-black-screen

In summary, the problem is that the remote *xrdp* session is not exited correctly and is still active on the computer, and *xrdp* does not allow 2 GUI users at the same time.
The solution is to kill the remote session by opening a non-GUI session on the computer.

0) The first thing to try is to do `Ctrl` `Alt` `F1` to wake-up the login screen on the computer, and try to log in. If it does not work, follow the steps below.

1) **Open non-GUI session**

    - Either log via SSH from another computer (not tested but should work)
    - Or go to the physical PC and type `Ctrl` `Alt` `F3` to enter a non-GUI session, and log in.

2) **List active sessions**
    ```bash
    loginctl list-sessions
    ```
    There will be one session that has nothing under "SEAT" or "TTY". Note the name of that session, e.g. `c2`.

3) **Kill the remote session**
    ```bash
    sudo loginctl kill-session c2
    ```
    (replace `c2` by the actual name of the session)

4) **Log out**
    ```
    logout
    ```
    (if one does not log out, the computer might still have trouble waking up).

5) **Log in with GUI**

    On the physical PC, type `Ctrl` `Alt` `F1` to go back to GUI login screen, and log in normally.