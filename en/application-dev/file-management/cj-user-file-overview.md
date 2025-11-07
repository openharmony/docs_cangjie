# User File Overview  

User Files: Files owned by users logged into the terminal device, including private images, videos, audio, documents, etc.  

1. User files are stored in the user directory and belong to the user logged into the device.  

2. User file storage locations are primarily divided into [Internal Storage](#internal-storage) and [External Storage](#external-storage).  

3. Applications must obtain user authorization in advance or require user operation to create, access, or delete user files.  

## User File Storage Locations  

### Internal Storage  

Internal storage refers to user files stored on the device's internal storage (space). The internal storage device cannot be removed. User files in internal storage mainly include:  

- **User-specific files**: These files belong to the user logged into the device. Different users can only see their own files after logging in. Based on file attributes and user/application usage habits, they can be categorized as:  
    - **Image/Video Media Files**  
        These files contain metadata such as capture time, location, rotation angle, width, and height. They are stored as media files in the system and are typically presented as "All Files" or "Albums" without revealing their exact storage path.  

    - **Audio Media Files**  
        These files contain metadata such as album, artist, and duration. They are stored as media files in the system and are usually presented as "All Files," "Albums," or "Artists" without displaying their specific storage location.  

    - **Other Files (collectively referred to as Document Files)**  
        These are stored as regular files in the system, including plain text files, compressed files, and even image/video or audio files stored as ordinary files. They are typically displayed in a directory tree structure.  

- **Multi-user Shared Files**: Users can place files in a shared storage area to enable access by multiple users.  
    Files in the shared storage area are also stored as regular files in the system and displayed in a directory tree structure.  

### External Storage  

External storage refers to user files stored on removable devices (e.g., SD cards, USB drives). Files on external storage devices, like those in the shared area of internal storage, are visible to all users logged into the system.  

All files on external storage devices are presented as regular files, similar to document files on internal storage, and are displayed in a directory tree structure.