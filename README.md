# m2-tech
Magento2 Technical Tips and Tools

-----

## **[Automated Patch Application](./composer)**

Follow [these instructions](./composer)

**Note:** 

* Includes Patches for [APSB22-12](https://helpx.adobe.com/security/products/magento/apsb22-12.html) **updated 2022/02/17**
* Patches are located under [./composer/patches directory](./composer/patches)
* Patches are auto-applied in the proper order to applicable versions of magento on composer update/install. 
* Patches can be manually applied through `composer patch` commands

**Example:**

```text
$ composer update
...
Processing patches configuration
  - Applying patches for magento/project-community-edition (2)
    ~ magento/project-community-edition: patches/MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch [MATCH]
      Patch for CVE-2022-24086 (https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-)
    ~ magento/project-community-edition: patches/MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch [MATCH]
      Patch for CVE-2022-24087 (Magento 2.4.3 to 2.4.3-p1) (https://support.magento.com/hc/en-us/articles/4426353041293-Security-updates-available-for-Adobe-Commerce-APSB22-12-)
```

  

  
