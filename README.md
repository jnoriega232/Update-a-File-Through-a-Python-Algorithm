# Update a File Through a Python Algorithm

## Project Description
In the hypothetical organization I've devised, regulated content access is managed via an IP address allow list. The ```"allow_list.txt"``` file serves to pinpoint these approved IP addresses. Correspondingly, a distinct roster, referred to as the remove list, compiles IP addresses necessitating access removal. To streamline this procedure, I devised an algorithm that automates the dynamic updating of the ```"allow_list.txt"``` file and the exclusion of IP addresses no longer authorized to access the content.

## Open the File that Contains the Allow List
To initiate the algorithm, I commenced by accessing the ```"allow_list.txt"``` file. Initially, I designated the file name as a string and assigned it to the variable ```import_file```:

<p align="center">
<img src="https://i.imgur.com/C0ERbcq.png" height="70%" width="70%" alt="Azure Free Account"/>

Subsequently, I employed a ```with``` statement to open the file:

<p align="center">
<img src="https://i.imgur.com/I1Alwi1.png" height="70%" width="70%" alt="Azure Free Account"/>

Within my algorithm, the ```with``` statement is employed in conjunction with the ```.open()``` function, operating in read mode. This facilitates the opening of the allow list file, enabling access to the stored IP addresses. This mechanism ensures efficient resource management by automatically closing the file upon exiting the ```with``` statement. The code snippet ```with open(import_file, 'r') as file:``` encompasses two parameters in the ```open()``` function. The initial parameter denotes the file to be imported, while the second specifies the intended action. In this instance, ```"r"``` signifies the intent to read the file. Additionally, the ```as``` keyword is utilized to assign the variable ```file```, which captures the output of the ```.open()``` function while I work within the ```with``` statement.

## Read the File Contents
To access the file's contents, I employed the ```.read()``` method, effectively converting it into a string format.

<p align="center">
<img src="https://i.imgur.com/lK9DRVp.png" height="70%" width="70%" alt="Azure Free Account"/>

When utilizing the ```.open()``` function with the ```"r"``` argument denoting "read", I can utilize the ```.read()``` function within the scope of the ```with``` statement. Employing the ```.read()``` method facilitates the transformation of the file content into a string, facilitating its readout. I invoked the ```.read()``` method on the ```file``` variable established within the ```with``` statement. Subsequently, I stored the string outcome of this method as the variable ```ip_addresses```.

In essence, this code snippet accomplishes the reading of ```"allow_list.txt"``` file content and converts it into a string format. This strategic conversion equips me to efficiently manipulate and extract data within my Python program at a later stage.

## Convert the String into a List
To facilitate the removal of individual IP addresses from the allow list, it was imperative to transform it into a list format. Consequently, I proceeded by employing the ```.split()``` method, effectively converting the ```ip_addresses``` string into a list:

<p align="center">
<img src="https://i.imgur.com/spDI8Ml.png" height="70%" width="70%" alt="Azure Free Account"/>

To activate the ```.split()``` function, one appends it to a string variable. This function operates by converting the content of a string into a list. The rationale behind fragmenting the ```ip_addresses``` into a list format lies in its facilitation of streamlined IP address removal from the allow list. As a default operation, the ```.split()``` function segregates the text using whitespace to generate list elements. In the context of this algorithm, the ```.split()``` function targets the data housed within the ```ip_addresses``` variable—a string consisting of individually spaced IP addresses. By executing this operation, the string is converted into a list format, which is subsequently re-assigned to the ```ip_addresses``` variable for storage.

## Iterate Through the Remove List
A pivotal component of my algorithm entails traversing through the IP addresses, which are encompassed as elements within the ```remove_list.``` To facilitate this procedure, I seamlessly integrated a ```for``` loop:

<p align="center">
<img src="https://i.imgur.com/SKcF19q.png" height="70%" width="70%" alt="Azure Free Account"/>

In Python, the ```for``` loop executes designated code for a predetermined sequence. Within the context of a Python algorithm such as this, the ```for``` loop is employed to implement designated code statements across all elements within a sequence. The ```for``` keyword initiates the loop, followed by the loop variable ```element``` and the ```in``` keyword. The ```in``` keyword signifies the iteration through the ```ip_addresses``` sequence, subsequently assigning each value to the loop variable ```element```. This overarching mechanism orchestrates the iterative execution of code for every element within the sequence.

## Remove IP Addresses that are on the Remove List
My algorithm necessitates the removal of any IP address from the "allow list" (```ip_addresses```) that also exists within the ```remove list```. Given the absence of duplicates within ```ip_addresses```, I could adeptly deploy the subsequent code to fulfill this task:

<p align="center">
<img src="https://i.imgur.com/B1Oxddm.png" height="70%" width="70%" alt="Azure Free Account"/>

Within the confines of my ```for``` loop, I instituted a conditional assessment to determine whether the loop variable ```element``` existed within the ```ip_addresses``` list. This strategic step was taken as a precaution, as utilizing ```.remove()``` on elements absent within ```ip_addresses``` could potentially trigger an error.

Subsequently, within this conditional framework, I executed ```.remove()``` on ```ip_addresses```. The loop variable ```element``` was furnished as the argument, ensuring the removal of each IP address present in the ```remove_list``` from the ```ip_addresses``` sequence.


## Update the File with the Revised List of IP Addresses
Concluding the algorithm, the last imperative was to refresh the "allow list" file with the amended roster of IP addresses. This entailed transforming the list back into string format. To achieve this, I harnessed the ```.join()``` method:

<p align="center">
<img src="https://i.imgur.com/Og3Utwg.png" height="70%" width="70%" alt="Azure Free Account"/>

The ```.join()``` method unifies all elements in an iterable, binding them into a single string. It is utilized by calling it on a string that contains the characters serving as separators between the iterable's elements once they are merged into a string. In the context of this algorithm, I employed the ```.join()``` method to construct a string from the ```ip_addresses``` list, a process integral for supplying the argument of the ```.write()``` method when composing the ```"allow_list.txt"``` file. The string (```"\n"```) was employed as the separator to instruct Python to allocate each element onto a fresh line.

Subsequently, I incorporated another ```with``` statement coupled with the ```.write()``` method to effectuate the file update:

<p align="center">
<img src="https://i.imgur.com/WaQ6M0S.png" height="70%" width="70%" alt="Azure Free Account"/>

On this occasion, I employed a second argument, ```"w"```, with the ```open()``` function within my ```with``` statement. This argument signifies the intent to open a file for writing, thereby overwriting its existing contents. By using ```"w"```, I was able to utilize the ```.write()``` function within the confines of the ```with``` statement's scope. The ```.write()``` function facilitates the writing of string data to the designated file, effectively replacing any preexisting content.

In this scenario, my objective was to write the modified allow list as a string into the file ```"allow_list.txt"```. This approach ensures that the restricted content remains inaccessible to any IP addresses that were excluded from the allow list. To update the file, I utilized the ```.write()``` function, which I appended to the file object named ```file``` that was established within the ```with``` statement. By passing the variable ```ip_addresses``` as an argument, I instructed the function to replace the contents of the file specified in the ```with``` statement with the data contained in the ```ip_addresses``` variable.


## Summary
I devised an algorithm aimed at eliminating IP addresses specified in a ```remove_list``` variable from the list of approved IP addresses stored in the ```"allow_list.txt"``` file. This algorithm encompassed several steps:

1. Opening the ```"allow_list.txt"``` file to access its content.
2. Converting the file content into a string to facilitate reading.
3. Transforming the string into a list and storing it in the ```ip_addresses``` variable.
4. Iterating through the IP addresses enlisted in the ```remove_list```.
5. For each iteration, assessing if the current IP address existed within the ```ip_addresses``` list.
6. If present, applying the ```.remove()``` method to eliminate the IP address from the ```ip_addresses``` list.
7. Subsequently, utilizing the ```.join()``` method to convert the ```ip_addresses``` list back into a string format.
8. Employing the ```.write()``` method within a ```with``` statement to overwrite the contents of the ```"allow_list.txt"``` file with the modified list of IP addresses.

By executing these sequential actions, the algorithm efficiently accomplishes the task of removing designated IP addresses from the ```"allow_list.txt"``` file.
