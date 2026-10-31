# Algorithm for File Updates in Python
## Removing Unauthorized IP Addresses from an Allow List

**Portfolio category:** Python scripting / Security automation  
**Programming language:** Python

## Project description

As part of access management at a healthcare organization, I was asked to update a file containing IP addresses permitted to access a restricted subnetwork. A separate remove list identifies IP addresses that should no longer have access because the associated employees are no longer authorized to work with restricted patient records. I developed a Python algorithm to read the allow-list file, compare its entries with the remove list, remove matching IP addresses, and write the revised list back to the file. This automates a repetitive access-maintenance task and supports the principle of least privilege.

## Complete code

The following is a typed version of the code for Tasks 2–7 of the *Create another algorithm* lab. It can be included instead of screenshots; if the course reviewer expects screenshots, capture the corresponding sections from your completed lab and insert them beneath the explanations.

```python
# Identify the file that contains the approved IP addresses.
import_file = "allow_list.txt"

# Open the file and read its contents.
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Convert the string of IP addresses into a list.
ip_addresses = ip_addresses.split()

# remove_list contains the IP addresses that must be removed.
# It is assumed to have been defined earlier in the lab.
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)

# Convert the updated list back into a newline-separated string.
ip_addresses = "\n".join(ip_addresses)

# Open the file in write mode and save the revised allow list.
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

> **Note:** The code assumes that `remove_list` has already been defined and contains the IP addresses to revoke. The activity focuses on processing that list, so its contents are not invented here.

## 1. Open the file that contains the allow list

### Code

```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    ip_addresses = file.read()
```

### Explanation

- `import_file` stores the name of the file to be accessed.
- `open()` is a Python function used to open a file. It takes the file name and a mode as arguments.
- The `"r"` mode opens the file for reading.
- The `with` statement manages the file while the indented block runs. It automatically closes the file when the block finishes, including if an exception occurs.
- `as file` assigns the opened file object to the variable `file`, which can be used inside the block.

Using `with open(...)` is good practice because it manages file closure without requiring a separate `file.close()` call.

## 2. Read the file contents

### Code

```python
with open(import_file, "r") as file:
    ip_addresses = file.read()
```

### Explanation

- `.read()` is a file method that reads the contents of the open file.
- The returned content is stored in `ip_addresses` as a string.
- At this stage, the IP addresses are text, rather than separate list elements.
- Reading the file into a variable makes it possible to process the contents before writing an updated version.

## 3. Convert the string into a list

### Code

```python
ip_addresses = ip_addresses.split()
```

### Explanation

- `.split()` is a string method that separates a string into a list.
- When no separator is supplied, `.split()` separates the text at whitespace, including spaces, tabs, and newline characters.
- This is useful because the allow-list file stores IP addresses on separate lines.
- The resulting variable is a list, making it possible to check for and remove individual addresses.

## 4. Iterate through the remove list

### Code

```python
for element in remove_list:
```

### Explanation

- `for` starts a loop that processes items in an iterable one at a time.
- `remove_list` contains IP addresses that must be removed from the allow list.
- `element` is the loop variable. During each iteration, it holds the current IP address from `remove_list`.
- The indented statements beneath the loop header execute once for each element.

## 5. Remove IP addresses that are on the remove list

### Code

```python
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```

### Explanation

- `if` begins a conditional statement.
- `element in ip_addresses` checks whether the current address from `remove_list` is present in the allow list.
- If the condition is true, `.remove(element)` removes that matching item from `ip_addresses`.
- If the address is not present, the condition is false and the loop continues without attempting removal. This avoids a `ValueError` from trying to remove a missing item.

**Why `.remove()` is appropriate here:** The lab scenario specifies that there are no duplicate IP addresses in `ip_addresses`. Therefore, removing the matching element removes the one occurrence of that IP address. If duplicates were possible, `.remove()` would remove only the first occurrence, so additional handling would be needed to remove every duplicate.

## 6. Update the file with the revised list of IP addresses

### Code

```python
ip_addresses = "\n".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(ip_addresses)
```

### Explanation

- `"\n"` represents a newline character.
- `.join(ip_addresses)` combines the list elements into one string, placing a newline between each IP address. This restores the one-address-per-line format.
- The second `with` statement opens the same file using `"w"` mode.
- `"w"` means write mode. It replaces the existing file contents, so the updated list is written over the previous allow list.
- `.write(ip_addresses)` writes the revised string to the open file.
- The `with` statement automatically closes the file after writing is complete.

**Important operational consideration:** Write mode overwrites the existing file. In a production environment, I would validate the resulting list, retain an appropriate backup or version history, and follow the organization's approval and change-management process before updating an access-control file.

## Summary

This algorithm automates the removal of IP addresses that are no longer authorized to access a restricted subnetwork. It uses `open()` with a `with` statement to safely access the allow-list file and `.read()` to load its contents. The `.split()` method converts the text into a list, and a `for` loop checks each address in `remove_list`. An `if` statement ensures that only addresses present in the allow list are removed using `.remove()`. Finally, `.join()` rebuilds the newline-separated text, and `.write()` saves the revised list to the original file.

## Security relevance

This task demonstrates how a small Python script can support access-control maintenance. Removing outdated entries helps reduce unnecessary access to restricted systems and supports least privilege. In a real healthcare environment, changes to access lists should be authorized, logged, tested, and recoverable so that legitimate staff are not accidentally locked out and changes can be audited.

## Portfolio evidence checklist

- [ ] Add a screenshot of the file-opening code from Task 2, if screenshots are required.
- [ ] Add a screenshot of the `.read()` operation from Task 3, if screenshots are required.
- [ ] Add a screenshot of the `.split()` operation from Task 4, if screenshots are required.
- [ ] Add a screenshot of the `for` loop from Task 5, if screenshots are required.
- [ ] Add a screenshot of the membership check and `.remove()` operation from Task 6, if screenshots are required.
- [ ] Add a screenshot of `.join()` and `.write()` from Task 7, if screenshots are required.
- [ ] Confirm that `remove_list` is defined in the lab before running the complete code.
- [ ] Test the algorithm on a safe copy of the file before using it on an operational access-control list.

---

*Coursework note: This document explains the algorithm requested in the activity. No actual employee records, IP address values, or execution results were supplied, so none have been fabricated.*
