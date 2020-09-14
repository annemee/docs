---
title: Get Started
tab_group_main:
    weight: 20
---

## Enable Object Storage

Object Storage is not enabled for a Linode account by default. All that is required to enable Object Storage is to create a bucket or an Object Storage access key. To cancel Object Storage, see the [Cancel Object Storage](#cancel-object-storage) section.

{{< note >}}
Billing for Object Storage will start when it is enabled on your account, **regardless of how it is enabled**. For example, if you enable the service by creating an access key, but you have not yet created a bucket, the $5 monthly flat rate (prorated) for Object Storage will be charged for your account. [Cancelling Object Storage](#cancel-object-storage) will stop billing for it.
{{< /note >}}

## Object Storage Key Pair

1.  Log into the [Linode Cloud Manager](https://cloud.linode.com).

   {{< note >}}
Object Storage is not available in the Linode Classic Manager.
{{</ note >}}

1.  Click on the **Object Storage** link in the sidebar, click the **Access Keys** tab, and then click the **Create an Access Key** link.

   ![Click on the 'Access Keys' tab.](object-storage-access-keys-tab.png)

1.  A prompt will appear asking you to confirm that you'd like to enable Object Storage. Click **Enable Object Storage**.

   ![Enable Object Storage](object-storage-enable-object-storage.png)

2.  The **Create an Access Key** menu will appear.

   ![The 'Create an Access Key' menu.](object-storage-create-key.png)

3.  Enter a label for the key pair. This label will be how you reference your key pair in the Linode Cloud Manager. Then, click **Submit**.

4.  A window will appear that contains your access key and your secret key. Write these down somewhere secure. The access key will be visible in the Linode Cloud Manager, but **you will not be able to retrieve your secret key again once you close the window.**

   ![Your access key and secret key.](object-storage-access-keys.png)

   You now have the credentials needed to connect to Linode Object Storage.

## Create a Bucket

The Cloud Manager provides a web interface for creating buckets. To create a bucket:

1.  If you have not already, log into the [Linode Cloud Manager](https://cloud.linode.com).

1.  Click on the **Object Storage** link in the sidebar, and then click on **Add a Bucket**.

   ![The Object Storage menu.](object-storage-add-a-bucket.png)

   If you have not created an access key or a bucket before, you will be prompted to enable Object Storage.

1.  The **Create a Bucket** menu will appear.

   ![The Create a Bucket menu.](object-storage-create-a-bucket.png)

1.  Add a label for your bucket. See the [Bucket Name](#bucket-names) section for rules on naming your bucket.

1.  Choose a cluster location for the bucket to reside in.

   {{< content "object-storage-cluster-shortguide" >}}

1.  Click **Submit**. You are now ready to [upload objects to your bucket](#upload-objects-to-a-bucket).

## Upload an Object to a Bucket

1.  If you have not already, log into the [Linode Cloud Manager](https://cloud.linode.com).

1.  Click on the **Object Storage** link in the sidebar. You will see a list of all your buckets. Click on the bucket you'd like to begin uploading objects to.

   ![Select an Object Storage Bucket](select-bucket.png)

1. You will see your bucket's **Objects Listing Page**. In the example, the *my-example-bucket* does not yet contain any objects. You can use the **Upload Files Pane** to drag and drop a file from your computer to your object storage bucket.

   {{< note >}}
You can drag and drop multiple files to the **Upload Files Pane** at one time.
   {{</ note >}}

   ![Drag and drop an object to your bucket](drag-drop-image-bucket.png)

   You can also click on the **Browse Files** button to bring up your computer's file browser and select a file to upload to your bucket.

   ![Upload an object to your bucket using the file browser](upload-with-file-browser.png)

1.  When the upload has completed, your object will be visible on the **Objects Listing Page**.

   ![Successful upload of your object](successful-object-upload.png)

   {{< note >}}
Individual object uploads are limited to a size of 5GB each, though larger object uploads can be facilitated with multipart uploads. [s3cmd](#s3cmd) and [cyberduck](#cyberduck) will do this for you automatically if a file exceeds this limit as part of the uploading process.
{{< /note >}}

## Cancel Object Storage

1.  To cancel Object Storage, you must first delete all of your buckets. To delete a bucket, the bucket must be empty. For buckets that contain large amounts of objects, consider employing [lifecycle policies](/docs/platform/object-storage/lifecycle-policies/) to delete the objects.

   {{< caution >}}
If you have removed all of your buckets, but you have not also cancelled the Object Storage service, your account will continued to be billed at a flat rate of $5 per month (prorated) for the service. Make sure that you complete each step of this section to fully cancel the Object Storage service and to stop billing for it. For more information, see our [Pricing and Limitations](/docs/platform/object-storage/pricing-and-limitations/) guide.
{{< /caution >}}

1.  Once you've deleted all of your buckets, navigate to the **Account** page in the left-hand navigation. Click on the *Settings* tab. In the menu, you should see a setting for Object Storage:

   ![Cancel Object Storage](object-storage-cancel-object-storage.png)

1.  Click **Cancel Object Storage**. A prompt will appear asking you to confirm the cancellation. If you still have active buckets, you will be prompted to delete them.