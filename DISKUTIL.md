# Fix unallocated disk space
Follow this Video: 
>[!tip] How to add unallocated space to C when Extend Volume is grayed out
>>https://www.youtube.com/watch?v=TTuRDL-guog&ab_channel=TechGuyCharlie

You can also follow the steps below in CMD/Powershell (*admin privilege might be required*):

- Enter the Service
>	Diskpart

- List available disks
>	List disk

- Use the selected disk
>	Select disk number of disk

- Lists available partitions on the selected disk
>	List partition

- Selects the given available partition for further use
>	Select partition < number of recovery partition >

- Forces the deletion of diskpart
>	Delete partition override

---
# Resize removeable volume
   
Watch this Video: 
> [!tip] How to Resize USB Flash Drive (Pendrive) Partition
>> https://www.youtube.com/watch?v=qqlVpKXB6OQ

You can also follow the steps below in CMD/Powershell (*admin privilege might be required):

- Enters the Service
>	Diskpart

- Lists available volumes
>	List volume

- Selects which of the available
>	Select <volume_name>

- Cleans the volume
>	Clean

---

