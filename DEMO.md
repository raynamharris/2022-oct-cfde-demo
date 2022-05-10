# CFDE/iHMP walkthrough - 2022 May CFDE Hackathon 

[![hackmd-github-sync-badge](https://hackmd.io/dW9EoOh3T42eed9q21NLJQ/badge)](https://hackmd.io/dW9EoOh3T42eed9q21NLJQ)

Permanent link: [github.com/ctb/2022-may-cfde-demo/DEMO.md](https://github.com/ctb/2022-may-cfde-demo/blob/main/DEMO.md)

## Contents:

[toc]

## Using the portal to find and export file information

(See [Jessica and Amanda's tutorial](https://hackmd.io/9EWhx5vYR3SDmd1Nl9rpyQ) for more detail!)

### Create a new personal collection

Go to [the CFDE data portal at app.nih-cfde.org/](https://app.nih-cfde.org/). 

Log in (upper right).

![](https://i.imgur.com/YVXgMVK.png)

Under your username (upper right), create a new personal collection. 


![](https://i.imgur.com/D2eEXg2.png)



For name, you can use "Tuesday demo" or anything else. You can leave description blank.

![](https://i.imgur.com/eNoJFep.png)


### Find some files

Go back to [the CFDE data portal main page](https://app.nih-cfde.org/). 

Select "File" (upper left).

![](https://i.imgur.com/nIlZ2Jw.png)

Use the facets on the left to select:
* Common Fund Program: HMP
* Project: "Longitudinal multi 'omics"
* "has persistent ID" - True
* Uncompressed size in Bytes - 50000000 to 60000000 (50 MB to 60 MB).

![](https://i.imgur.com/7SAZK0X.png)


![](https://i.imgur.com/9wOPGAY.png)


With these selections, the first result should have "Filename" of `SRR5935743_1.fastq`.

![](https://i.imgur.com/ULbqD7W.png)


### Add files to your personal collection

Click on the first result to get a detail view. Then add it to your personal collection:
* scroll down to "Part of personal collection" and click "Link records."
* Select your personal collection, click "Link" (upper right).

Click back in your browser, to get back to your filtered search.

Repeat linking to a collection with the third result (Filename: `SRR5950647_1.fastq`). Add it to the same personal collection.

:::info
For today, here are the direct links to the two files we'll be using:
* [file 1, `SRR5935743_1.fastq`](https://app.nih-cfde.org/chaise/record/#1/CFDE:file/nid=528892)
* [file 2, `SRR5950647_1.fastq`](https://app.nih-cfde.org/chaise/record/#1/CFDE:file/nid=531342)
:::

(Note, you could select any files you like, but these are small enough to work and I know what the results will be. So it's good for today's demo; I suggest trying new/different files as a Thursday exercise!)

### Export your personal collection

Go to your collection, and select "export" and choose "NCPI manifest format."

:::info
**What is NCPI?**
"NCPI" stands for "NIH Cloud Platform Interoperability", an effort by the NIH to convene around interoperation for cloud workbenches.
:::

### Examine the NCPI manifest file

You should now have a CSV file in your Downloads that, when examined with a spreadsheet program, looks like this:

![](https://hackmd.io/_uploads/HkshxgdLq.png)

The key piece of information in here is the `drs_uri` column, which provides a [Data Repository Service](https://ga4gh.github.io/data-repository-service-schemas/preview/release/drs-1.0.0/docs/) location from which to download the files.

## Connect to your AWS instance/on JupyterHub

We've [installed some software for you on AWS](https://hackmd.io/rrjnYcZ3QemfuDpt82oomw?view), and you should receive a Web link to your AWS instance Web site in zoom chat (during today's demo, at least ;).

### Log in to JupyterHub

You should see:

![](https://i.imgur.com/h0mXlZy.png)

Use username `cfde`. (We'll give you the sekret password in Zoom chat.)

You should now be at a JupyerHub console.

![](https://i.imgur.com/W3o8BlN.png)

### Open Jupyter notebook

Go to the `demo/` folder and open `demo-walkthrough.ipynb` by clicking on it.

![](https://i.imgur.com/mWTz7DF.png)

You can [also see a static version of the walkthrough](https://github.com/ctb/2022-may-cfde-demo/blob/main/demo-walkthrough.ipynb).

## Ideas for Thursday sessions

During the Thursday co-working sessions, we will provide AWS instances with all the software pre-installed.

Here are two ideas for things to do during that session:

* re-do this analysis!
* do the download and taxonomic analysis with new/different/bigger samples!
* tackle other kinds of metagenome analyses - happy to chat about your interests!
