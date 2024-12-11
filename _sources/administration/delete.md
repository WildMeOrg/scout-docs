# Delete Data


## Delete Users
At present, there is no way to delete users.

## Delete Images
At present, there is no way through the UI to delete images from the system. Instead, you must make edits to the mongoDB directly.

## Delete Tasks
When you delete a task, the associated annotations are removed from the system. When you delete a task that has been through ground truth, the ground truth confirmations are removed from the system, which can impact annotation export analysis. When you delete a task that has the last instance of a tag on it, the tag is not removed from the system. To remove tags, you must delete them individually.