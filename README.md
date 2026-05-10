# User & Group Management Tool

A simple, interactive **Bash script** that provides a menu-driven interface (using **Whiptail**) to manage Linux users and groups. It allows system administrators to perform common user and group operations without memorizing individual shell commands.

---

## 📋 Features

- ➕ Add a new user
- ✏️ Modify (rename) an existing user
- ❌ Delete a user (along with their home directory)
- 📃 List all users
- ➕ Add a new group
- ✏️ Modify (rename) an existing group
- ❌ Delete a group
- 📃 List all groups
- 🔒 Disable (lock) a user account
- 🔓 Enable (unlock) a user account
- 🔑 Change a user's password
- ℹ️ About section
- 🚪 Exit option

---

## 🛠️ Prerequisites

Before running this script, make sure you have:

- A **Linux** operating system (Ubuntu, Debian, CentOS, Fedora, etc.)
- **Bash** shell (pre-installed on most Linux systems)
- **Whiptail** package (used to render the dialog menus)
- **Root / sudo privileges** (required for user and group management)

### Install Whiptail

**Debian / Ubuntu:**
```bash
sudo apt update
sudo apt install whiptail -y
```

**CentOS / RHEL / Fedora:**
```bash
sudo yum install newt -y
# or on newer versions:
sudo dnf install newt -y
```

---

## 🚀 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/abdallamohameed/Bash_Scripting.git
   cd <your-repo-name>
   ```

2. **Make the script executable:**
   ```bash
   chmod +x user_manager.sh
   ```

3. **Run the script with root privileges:**
   ```bash
   sudo ./user_manager.sh
   ```

---

## 💻 Usage

After running the script, an interactive menu will appear. Use the **arrow keys** to navigate and **Enter** to select an option. Press **Tab** to switch between buttons (OK / Cancel).

### Main Menu Options

| Option | Description |
|--------|-------------|
| **Add User** | Adds a new user to the system and prompts for a password. |
| **Modify User** | Renames an existing user account. |
| **Delete User** | Deletes a user and their home directory. |
| **List Users** | Displays the last 10 users from `/etc/passwd`. |
| **Add Group** | Creates a new group. |
| **Modify Group** | Renames an existing group. |
| **Delete Group** | Removes an existing group. |
| **List Groups** | Displays the last 10 groups from `/etc/group`. |
| **Disable User** | Locks a user account (prevents login). |
| **Enable User** | Unlocks a previously locked user account. |
| **Change Password** | Changes the password of an existing user. |
| **About** | Shows information about the program and the author. |
| **Exit** | Closes the script. |

---

## 🧠 How It Works

The script runs an infinite loop that displays the main menu using `whiptail --menu`. Each selection triggers a corresponding `if/elif` branch which:

1. Prompts the user for input via `whiptail --inputbox`.
2. Validates the input (e.g., checking if a user/group already exists using `id` or `getent`).
3. Executes the corresponding system command (`useradd`, `usermod`, `userdel`, `groupadd`, `groupmod`, `groupdel`, `passwd`).
4. Displays a success or error message via `whiptail --msgbox`.

The loop terminates when the user selects **Exit** or presses **Cancel** on the main menu.

---

## ⚠️ Notes & Warnings

- This script must be executed as **root** (or via `sudo`); otherwise, user and group management commands will fail.
- The **Delete User** option uses the `-r` flag, which **permanently removes the user's home directory** and mail spool. Use with caution.
- The **List Users** and **List Groups** options only display the **last 10 entries** because they use the `tail` command. You can replace `tail` with `cat` to display the full list.
- When renaming a user with `usermod -l`, the user's home directory is **not** automatically renamed. Use `usermod -d /home/newname -m` separately if needed.

---

## 👨‍💻 Author

**Abdalla Mohamed Aboulfotouh**

Built using **Bash + Whiptail**.

---

## 📜 License

This project is open-source. Feel free to use, modify, and distribute it.
You may add a license such as [MIT](https://opensource.org/licenses/MIT) by creating a `LICENSE` file in the repository.

---

## 🤝 Contributing

Contributions are welcome! If you find a bug or have a suggestion:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## ⭐ Show Your Support

If you find this project useful, please consider giving it a ⭐ on GitHub!
