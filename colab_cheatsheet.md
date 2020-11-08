# Colab Cheatsheet
1. [Import custom modules or packages from Google Drive](#import-custom-modules-or-packages-from-google-drive)

### Import custom modules or packages from Google Drive
Ref: [StackOverflow](https://stackoverflow.com/questions/48905127/importing-py-files-in-google-colab/48919022)  
1. Suppose I want to use [Deep Attention Sampling](https://github.com/idiap/attention-sampling).
    ```
    attention-sampling-master
    ├─ats
    │  ├─core
    │  ├─data
    │  ├─ops
    │  │  ├─cmake
    │  │  └─extract_patches
    │  └─utils
    ├─docs
    │  ├─css
    │  └─img
    ├─scripts
    └─tests
        ├─core
        ├─data
        ├─ops
        └─utils
    ```
1. Upload the root folder of the package on your Google Drive.  
I chose `Google Drive/attention-sampling-master`.
1. Mount your Google Drive.
    ```python
    from google.colab import drive
    drive.mount('/content/gdrive/')
    ```
1. Add the directory of the desired module or package.  
    ```python
    import sys
    sys.path.append('/content/gdrive/My Drive/attention-sampling-master')
    ```
1. Now, you can import anything in that directory.
    ```python
    import ats
    ```
