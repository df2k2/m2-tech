# Composer Tips and Tools

--------




## Automated Patching


### **Application and Usage**

To use the automated patch system, update your magento root project's `composer.json`:

**Step 1.** Add the following to the requires node:

```json
     "require": {
        // ...
        "vaimo/composer-patches": "~4.21"
        // ...
    },
```

**Step 2.** Add the *patches-search*, and set patcher to fail gracefully under `extra` node: 

```json
     "extra": {
        // ...
        "patches-search": "patches",
        "patcher": {
            "graceful": true
        },
    }
```

**Step 3.** Obtain patch, apply the proper meta, place file within the directory specified - our example is `./patches`:

See working patch example: [patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch](./patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch)

**Step 4.** Test locally: `composer update`:

```text
Generating autoload files
 - Applying patches for magento/project-community-edition (1)
    ~ magento/project-community-edition: patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch [MATCH]
      Patch for CVE-2022-24086 (https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-)

Writing patch info to install file

```

**Additional commands:**

* **composer patch:list**

```text
$ composer patch:list
magento/module-backend
~ magento/project-community-edition: patches/MDVA-40311_2.4.2-p2.patch [APPLIED]
MDVA-40311 (for Adobe Commerce and Magento Open Source >=2.4.2-p2 <2.4.4)-Fixes the issue where admin users
get the error message "Invalid security or form key. Please refresh the page" after login to the admin if
custom admin path is configured and secret key is enabled.

```


* **patch:apply**

```text
$ composer patch:apply
Processing patches configuration
 - Applying patches for magento/project-community-edition (1)
    ~ magento/project-community-edition: patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch [MATCH]
      Patch for CVE-2022-24086 (https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-)

Writing patch info to install file
```

* **patch:undo**

```text
$ composer patch:undo
Processing patches configuration
  - Resetting patches for ... (1)
Writing patch info to install file

```
* **patch:redo**

```text
- Applying patches for magento/project-community-edition (1)
    ~ magento/project-community-edition: patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch [MATCH]
      Patch for CVE-2022-24086 (https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-)
```

* **patch:validate**
