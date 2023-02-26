# Proof of Value

## KAPE Temporary Folder Target

The KAPE target included with this repo will look at 3 different locations for temporary folders. Explanations on each folder can be found in the README on the top level. To demonstrate the effectiveness of the target, a file called "Evidence.txt" was placed in a user profile temp folder. If the KAPE target works as expected, it should recreate the folder structure and copy all the files in each temporary folder.

Note that the following screenshots have all other files blocked out of the image.

---

## Proof of Need

To demonstrate that KAPE does not currently have a target dedicated to temp folders, `grep` is run on the cloned KAPE repository searching for `C:\Windows\Temp`. The only two targets that pull this folder are dedicated to specific applications and do not pull all of the files in the temp folder - only very specific ones.

![Searching for temp folders in KAPE](./Images/Evidence_Of_Lack_Of_Dedicated_Target.png)

---

## Proof of Value Demo

First, `Evidence.txt` is placed in `C:\Users\<userprofile>\AppData\Local\Temp`.

![A test file is placed in the user's temp folder](./Images/Evidence_File_in_Temp.png)

Next, GKAPE is opened. Without the target, there is no "Temp Folder" target.

![GKAPE does not have any Temp Folder target](./Images/GKAPE_Without_Target.png)

After placing the `Temp Folders.tkape` target in the KAPE Targets directory, GKAPE now shows a "Temp Folder" target.

![GKAPE shows the Temp Folder target](./Images/GKAPE_With_Target.png)

After running KAPE with the Temp Folder target enabled, we can see that it has recreated the directory structure, starting at the C drive.

![KAPE recreated the file structure](./Images/KAPE_Output_Evidence.png)

Navigating to the user's local temp folder, the `Evidence.txt` file was successfully copied over.

![Evidence.txt is now in the KAPE output](./Images/KAPE_Evidence_file.png)

---

This demo shows that KAPE can now extract any files within one of the Windows temp folders. The other two folders work the same way and output each file to its respective folder (i.e. a file in `C:\Windows\Temp` will stay in the recreated `C\Windows\Temp` directory in the KAPE output rather than being combined with the user profile temp folder).