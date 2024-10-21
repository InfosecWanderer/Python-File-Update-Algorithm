# Algorithm for file updates in Python

## Project description
In my organization, access to restricted content is managed through an allowed list of IP addresses. The file **"allow_list.txt"** contains these IP addresses, while another list specifies the IP addresses that should be denied access. I developed an algorithm to automate the process of updating the **"allow_list.txt"** file by removing IP addresses that no longer require access.

## Open the file that contains the allow list
For the initial step of the algorithm, I assigned the file name **"allow_list.txt"** to the variable import_file as a string.

![image](https://github.com/user-attachments/assets/ec9e2197-9edf-4784-b1cc-755711d393d0)

 
Next, I used a with statement to open the file. In the algorithm, the with statement is employed with the **.open()** function in read mode to access the IP addresses stored in the allow list file. Using the with keyword ensures that the file is properly closed after exiting the with block. In the code with **open(import_file, "r") as file:,** the **open()** function takes two arguments: the first specifies the file to open, and the second, **"r"**, denotes that the file should be opened in read mode. The as keyword is used to assign the variable file, which holds the file object returned by the **.open()** function while working within the with block.
 
## Read the file contents
To read the contents of the file, I used the **.read()** method to convert it into a string.

![image](https://github.com/user-attachments/assets/abc34e0b-fb7b-40d9-830e-d275102d98f9)

When the **.open()** function is used with the **"r"** argument for **"read,"** the **.read()** method can be called within the with block. This method converts the file content into a string, making it accessible for reading. I applied the **.read()** method to the file variable defined in the with statement and then assigned the resulting string to the variable **ip_addresses**.
In summary, this code reads the contents of the **"allow_list.txt"** file into a string format, which can then be used to organize and extract data within the Python program.

## Convert the string into a list
To facilitate the removal of individual IP addresses from the allow list, I needed to convert it into a list format. To achieve this, I used the **.split()** method to transform the **ip_addresses** string into a list:

![image](https://github.com/user-attachments/assets/c77d7a1d-d9c8-420c-af17-0643794df481)

The **.split()** function is applied to a string variable and works by breaking the string into a list. The reason for splitting **ip_addresses** into a list is to simplify the process of removing IP addresses from the **allow list**. By default, **.split()** divides the string by whitespace into separate list elements. In this algorithm, the **.split()** function processes the **ip_addresses** string—where each IP address is separated by whitespace—and converts it into a list of IP addresses. I then reassigned this list back to the ip_addresses variable.

## Iterate through the remove list
A crucial part of my algorithm involves iterating through the IP addresses listed in the remove_list. To accomplish this, I used a for loop:

![image](https://github.com/user-attachments/assets/a128182c-0593-4f1b-a73f-46e2b0c81d7d)

In Python, a **for loop** executes code for each item in a specified sequence. In this algorithm, the for loop is used to apply particular code statements to every element in the sequence. The loop starts with the for keyword, followed by the loop variable element and the keyword in. The in keyword specifies that the loop should iterate through the sequence ip_addresses, assigning each value to the loop variable element.

## Remove IP addresses that are on the remove list
My algorithm needs to remove any IP address from the **ip_addresses** allow list that is also present in the **remove_list**. Since there were no duplicates in **ip_addresses**, I used the following approach:

![image](https://github.com/user-attachments/assets/f1a7b1ed-0d07-4975-8ada-6606cc84dbf7)
 
First, within the for loop, I implemented a condition to check whether the loop variable element was in the ip_addresses list. This was necessary because attempting to use **.remove()** on elements not present in ip_addresses would cause an error.
Inside this condition, I used the **.remove()** method on **ip_addresses**, passing the loop variable element as the argument. This ensured that each IP address found in the remove_list was removed from **ip_addresses**.

## Update the file with the revised list of IP addresses 
As the last step of my algorithm, I needed to update the allow list file with the revised IP addresses. To achieve this, I first converted the list back into a string using the **.join()** method:

![image](https://github.com/user-attachments/assets/e30bc26b-991d-4f7c-8f0b-ad5efc96dd9a)

The **.join()** method concatenates all items in an iterable into a single string. It is called on a string that defines the separator to be used between elements in the iterable. In this case, I used **.join()** to create a string from the **ip_addresses** list, with each element separated by a newline character **("\n")**. This formatted string was then used as an argument for the **.write()** method to update the file **"allow_list.txt"**.

Next, I used another with statement along with the **.write()** method to update the file:

![image](https://github.com/user-attachments/assets/9fb900fb-b6ab-4ca8-ada6-f331674a8411)

This time, I specified the **"w"** argument in the **open()** function within the with statement, which opens the file for writing and overwrites its contents. With this **"w"** argument, I could call the **.write()** method inside the with block. The **.write()** method writes the string data to the file, replacing any existing content. I used this method to write the updated allow list to **"allow_list.txt"**, ensuring that any removed IP addresses no longer had access to the restricted content. I appended the **.write()** method to the file object defined in the with statement and passed the **ip_addresses** variable as the argument to replace the file's contents with the updated data.

## Summary
I developed an algorithm to remove IP addresses listed in a **remove_list** variable from the **"allow_list.txt"** file, which contains approved IP addresses. The algorithm involved several steps: first, I opened the file and converted its contents into a string. This string was then transformed into a list stored in the **ip_addresses** variable. I iterated through the IP addresses in **remove_list** and checked if each one was present in the **ip_addresses** list. If an IP address was found, I used the **.remove()** method to delete it from **ip_addresses**. Finally, I applied the **.join()** method to convert the updated **ip_addresses** list back into a string, which was then used to overwrite the contents of the **"allow_list.txt"** file with the revised list of IP addresses.


