# Hosting static websites with Google Cloud Storage
In this post I would like to show you how you can host static websites on google cloud. I will create very simple html website with homepage, about us page and page for handling 404 error (page not found). The contents of the page are not import it's just to show the page works and how to deploy it. If you want you can also host this way pages created using react. Alright, let's get right into it and please comment if you find anything not clear.

## Prerequisits
Before we start let's make sure we got all the necessary prerequisits.
* Google Cloud Account - Go to https://cloud.google.com/ to create one
* gsutil - Go to https://cloud.google.com/sdk/docs/quickstarts and follow installation instruction for your system
* Website you want to host - you can use mine 

### Creating bucket on Google Cloud Storage
**The bucket name has to be valid domain name**. This is single most important thing otherwise you won't be able to setup website configuration. 
We will use samplepage.com as our bucket name for the purpose of this tutorial.

    gsutil mb gs://samplepage.com

Output:

### Upload website to Google Cloud Storage
Once our bucket is created let's copy website files from local directory.

    gsutil rsync -R . gs://samplepage.com

Output:


### Perform website configuration on the bucket
Finally we have to set entry point of the website and page to show when user tries to access non-existing page.

    gsutil web set -m index.html -e 404.html gs://samplepage.com

## FAQ
Q: I can't do website configuration for my google cloud storage bucket.
A: If you don't see website configuration in your bucket options it usually mean's that the name of your bucket is not correct domain name.
