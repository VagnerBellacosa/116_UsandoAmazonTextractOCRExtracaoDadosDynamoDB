![Cover image for Amazon Textract with expense analyzing](https://res.cloudinary.com/practicaldev/image/fetch/s--pHg5PWAW--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4lgm5c0c87urzdvlqhjo.png)

[![AWS Community Builders  profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--3vA9CcCA--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/organization/profile_image/2794/88da75b6-aadd-4ea1-8083-ae2dfca8be94.png)](https://dev.to/aws-builders)[![Jones Zachariah Noel](https://res.cloudinary.com/practicaldev/image/fetch/s--qWBsYeMO--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/615180/12ee3aca-f67e-4f08-986f-1bdfd7ca384b.jpg)](https://dev.to/zachjonesnoel)

[Jones Zachariah Noel](https://dev.to/zachjonesnoel) for [AWS Community Builders](https://dev.to/aws-builders)

Posted on 17 de out.

# Amazon Textract with expense analyzing

[#textract](https://dev.to/t/textract)[#aws](https://dev.to/t/aws)[#machinelearning](https://dev.to/t/machinelearning)[#tutorial](https://dev.to/t/tutorial)

[Amazon Textract](https://aws.amazon.com/textract) now supports receipts and invoices processing which makes expense management systems analyze better with *only receipt's or invoice's* image or document.
Read more about the [announcement](https://aws.amazon.com/about-aws/whats-new/2021/07/amazon-textract-announces-specialized-support-automated-processing-invoices-receipts/).

#### Key takeaways from the blog

- [What is Textract?](https://dev.to/aws-builders/amazon-textract-with-expense-analyzing-516b#what-is-textract)
- [How Textract processes receipts and invoices](https://dev.to/aws-builders/amazon-textract-with-expense-analyzing-516b#receipts-and-invoices)
- [Implementing Textract with NodeJS SDK](https://dev.to/aws-builders/amazon-textract-with-expense-analyzing-516b#textract-implementation)

#### What is Textract?

[Amazon Textract](https://aws.amazon.com/textract) is a fully-managed Machine Learning service which extract textual information from documents and images. The Textract `DetectDocumentText` API is capable of detecting and extracting textual data which are handwritten or typed present either as texts, forms or tables in the document or image.

Common use-cases of Textract are -

- Data capture from forms.

- Automating certain processes similar to KYC process.

  > ![unknown tweet media content](https://res.cloudinary.com/practicaldev/image/fetch/s--hGPOi-lo--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://pbs.twimg.com/media/Em9AG0nVoAYV-YQ.jpg)
  >
  > ![Jeff Barr ☁️ (@ 🏠 ) 💉 profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--qv16LiyE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://pbs.twimg.com/profile_images/1368794503285383171/qoMhip1Z_normal.jpg)
  >
  > Jeff Barr ☁️ (@ 🏠 ) 💉
  >
  > @jeffbarr
  >
  > ![twitter logo](https://res.cloudinary.com/practicaldev/image/fetch/s--ir1kO05j--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-f95605061196010f91e64806688390eb1a4dbc9e913682e043eb8b1e06ca484f.svg)
  >
  > Cool demo video [@mikegchambers](https://twitter.com/mikegchambers) - Amazon Textract Handwriting Recognition (New) - [youtube.com/watch?v=Efbgai…](https://t.co/MXKDL4p8Pr) . Be sure to fill in those TPS Reports...
  >
  > 14:55 PM - 16 Nov 2020
  >
  > [![Twitter reply action](https://res.cloudinary.com/practicaldev/image/fetch/s--fFnoeFxk--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-reply-action-238fe0a37991706a6880ed13941c3efd6b371e4aefe288fe8e0db85250708bc4.svg)](https://twitter.com/intent/tweet?in_reply_to=1328351004903948288) [![Twitter retweet action](https://res.cloudinary.com/practicaldev/image/fetch/s--k6dcrOn8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-retweet-action-632c83532a4e7de573c5c08dbb090ee18b348b13e2793175fea914827bc42046.svg)](https://twitter.com/intent/retweet?tweet_id=1328351004903948288) [![Twitter like action](https://res.cloudinary.com/practicaldev/image/fetch/s--SRQc9lOp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-like-action-1ea89f4b87c7d37465b0eb78d51fcb7fe6c03a089805d7ea014ba71365be5171.svg)](https://twitter.com/intent/like?tweet_id=1328351004903948288)

  > ![unknown tweet media content](https://res.cloudinary.com/practicaldev/image/fetch/s--aeVGONp8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://pbs.twimg.com/media/E4wFsduWUAIwFaU.jpg)
  >
  > ![Danilo Poccia profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--uxE8Xk6S--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://pbs.twimg.com/profile_images/1322901525476331520/-8TMD1WC_normal.jpg)
  >
  > Danilo Poccia
  >
  > [@danilop](https://dev.to/danilop)
  >
  > ![twitter logo](https://res.cloudinary.com/practicaldev/image/fetch/s--ir1kO05j--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-f95605061196010f91e64806688390eb1a4dbc9e913682e043eb8b1e06ca484f.svg)
  >
  > Improve newspaper digitalization efficacy with a generic document segmentation tool using Amazon Textract [buff.ly/3xFEKnp](https://t.co/ObIlGsEhKs) [#AWS](https://twitter.com/hashtag/AWS) [#MachineLearning](https://twitter.com/hashtag/MachineLearning)
  >
  > 19:27 PM - 25 Jun 2021
  >
  > [![Twitter reply action](https://res.cloudinary.com/practicaldev/image/fetch/s--fFnoeFxk--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-reply-action-238fe0a37991706a6880ed13941c3efd6b371e4aefe288fe8e0db85250708bc4.svg)](https://twitter.com/intent/tweet?in_reply_to=1408507048111845386) [![Twitter retweet action](https://res.cloudinary.com/practicaldev/image/fetch/s--k6dcrOn8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-retweet-action-632c83532a4e7de573c5c08dbb090ee18b348b13e2793175fea914827bc42046.svg)](https://twitter.com/intent/retweet?tweet_id=1408507048111845386) [![Twitter like action](https://res.cloudinary.com/practicaldev/image/fetch/s--SRQc9lOp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/twitter-like-action-1ea89f4b87c7d37465b0eb78d51fcb7fe6c03a089805d7ea014ba71365be5171.svg)](https://twitter.com/intent/like?tweet_id=1408507048111845386)

  And more use-cases available on

   

  Amazon Textract documentation

  .

Textract exposes the following SDK APIs for developers to integrate -

- `AnalyzeDocument` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_AnalyzeDocument.html))
- `AnalyzeExpense` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_AnalyzeExpense.html))
- `DetectDocumentText` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_DetectDocumentText.html))
- `GetDocumentAnalysis` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_GetDocumentAnalysis.html))
- `GetDocumentTextDetection` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_GetDocumentTextDetection.html))
- `StartDocumentAnalysis` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_StartDocumentAnalysis.html))
- `StartDocumentTextDetection` ([documentation](https://docs.aws.amazon.com/textract/latest/dg/API_StartDocumentTextDetection.html))

With Textract, the processing of images or documents can be handled [synchronously](https://docs.aws.amazon.com/textract/latest/dg/sync.html) or [asynchronous](https://docs.aws.amazon.com/textract/latest/dg/async.html).
`StartDocumentAnalysis` / `GetDocumentAnalysis` and `StartDocumentTextDetection` / `GetDocumentTextDetection` are the asynchronous implementation of Amazon Textract and whenever the action start (`StartDocumentAnalysis` and `StartDocumentTextDetection`) is executed, it returns a `JobID` which is referred to when getting the data.

Textract APIs are flexible to take either document/image buffer data or the object stored on S3 to process and extract textual information.

Python samples are available in - [GitHub/awsdocs](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/textract)

## ![GitHub logo](https://res.cloudinary.com/practicaldev/image/fetch/s--i3JOwpme--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/github-logo-ba8488d21cd8ee1fee097b8410db9deaa41d0ca30b004c0c63de0a479114156f.svg) [aws-samples ](https://github.com/aws-samples)/ [amazon-textract-code-samples](https://github.com/aws-samples/amazon-textract-code-samples)

### Amazon Textract Code Samples

## Amazon Textract Code Samples

This repository contains example code snippets showing how Amazon Textract and other AWS services can be used to get insights from documents.

## Usage

python3 01-detect-text-local.py

For examples that use S3 bucket, upload sample images to an S3 bucket and update variable "s3BucketName" in the example before running it.

## Python Samples

| Argument                                                     | Description                                                |
| :----------------------------------------------------------- | :--------------------------------------------------------- |
| [01-detect-text-local.py](https://github.com/aws-samples/amazon-textract-code-samples./python/01-detect-text-local.py) | Example showing processing a document on local machine.    |
| [02-detect-text-s3.py](https://github.com/aws-samples/amazon-textract-code-samples./python/02-detect-text-s3.py) | Example showing processing a document in Amazon S3 bucket. |
| [03-reading-order.py](https://github.com/aws-samples/amazon-textract-code-samples./python/03-reading-order.py) | Example showing printing document in reading order.        |
| [04-nlp-comprehend.py](https://github.com/aws-samples/amazon-textract-code-samples./python/04-nlp-comprehend.py) | Example showing detecting entities and sentiment.          |
| [05-nlp-medical.py](https://github.com/aws-samples/amazon-textract-code-samples./python/05-nlp-medical.py) | Example showing detecting medical entities.                |
| [06-translate.py](https://github.com/aws-samples/amazon-textract-code-samples./python/06-translate.py) | Example showing translation of documents.                  |
| [07-search.py](https://github.com/aws-samples/amazon-textract-code-samples./python/07-search.py) | Example showing document indexing in Elasticsearch.        |
| [08-forms.py](https://github.com/aws-samples/amazon-textract-code-samples./python/08-forms.py) | Example showing form (key/value) processing.               |
| [09-forms-redaction.py](https://github.com/aws-samples/amazon-textract-code-samples./python/09-forms-redaction.py) | Example showing redacting information in document.         |
| [10-tables.py](https://github.com/aws-samples/amazon-textract-code-samples./python/10-tables.py) | Example showing table processing.                          |
| [11-tables-expense.py](https://github.com/aws-samples/amazon-textract-code-samples./python/11-tables-expense.py) | Example showing validation of table data.                  |
| [12-pdf-text.py](https://github.com/aws-samples/amazon-textract-code-samples./python/12-pdf-text.py) | Example showing PDF document processing.                   |

## .NET Usage

```
Usage: dotnet run [--switch]
To run this console
```

…

[View on GitHub](https://github.com/aws-samples/amazon-textract-code-samples)


NodeJS samples are in an open pull request -

# [![GitHub logo](https://res.cloudinary.com/practicaldev/image/fetch/s--i3JOwpme--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/github-logo-ba8488d21cd8ee1fee097b8410db9deaa41d0ca30b004c0c63de0a479114156f.svg) Added NodeJS samples #18](https://github.com/aws-samples/amazon-textract-code-samples/pull/18)

[![zachjonesnoel avatar](https://res.cloudinary.com/practicaldev/image/fetch/s--BEC0gOey--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://avatars.githubusercontent.com/u/12515425%3Fv%3D4)](https://github.com/zachjonesnoel)

**[zachjonesnoel](https://github.com/zachjonesnoel)** posted on [Sep 18, 2021](https://github.com/aws-samples/amazon-textract-code-samples/pull/18)

*Issue #, if available:*

*Description of changes:* Added NodeJS text detect samples.

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

[View on GitHub](https://github.com/aws-samples/amazon-textract-code-samples/pull/18)

#### How Textract processes receipts and invoices

Textract `AnalyzeExpense` API processes the data and extracts the key information from the document such as *Vendor names*, *Receipt number* or *Invoice number*. `AnalyzeExpense` API is available **only in the latest version of SDK**, as this is one of the new functions available now. So ensure, you have updated your SDK.

> Starting today, Amazon Textract adds the following capabilities for receipts and invoices: 1) Identifies Vendor Name - Amazon Textract can find the vendor name on a receipt even if it's only indicated within a logo on the page without an explicit label called “vendor”. It can also find and extract item, quantity, and prices that are not labeled with column headers for line items, 2) Enables consolidation of output from many documents - Textract normalizes keynames and column headers when extracting data from invoices and receipts, into a standard taxonomy. For example, it detects that “invoice no.” “invoice number” and “receipt #” are identical and outputs “INVOICE_RECEIPT_ID,” so that downstream applications can easily compare output from many documents, and 3) Extracts line item details, even when the column headers are missing - Textract extracts line items including items, quantities, and prices of individual goods purchased from an invoice or a receipt. If the table of line items does not include column headers, Textract now infers what the column headers are meant to be based on the table content.

As described in the [announcement](https://aws.amazon.com/about-aws/whats-new/2021/07/amazon-textract-announces-specialized-support-automated-processing-invoices-receipts/).

This makes it easier for systems which are integrating Textract to manage expense analysis with the consolidated information.

#### Implementing Textract with NodeJS SDK

In this walkthrough, we will be using the `AnalyzeExpense` and `AnalyzeDocument` API from Textract.

To get started, you can navigate to *Amazon Textract* AWS Console from where you will be able to run Textract on sample documents and view the response pretty-formatted on the console.

Image used for the demo -
[![Image used for the demo](https://res.cloudinary.com/practicaldev/image/fetch/s--pCxWYwzr--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6sb11vrufnvowmhv16nd.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--pCxWYwzr--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6sb11vrufnvowmhv16nd.png)

When using `AnalyzeDocument` from the console/ SDK API, you would have to use what type of feature you want to extract. From SDK API you would have to pass the input for `FeatureTypes` as `TABLES` or `FORMS`, if you are trying this from the console, you can additionally extract all the text as `RAW TEXT` also.
Raw text -
[![RAW TEXT](https://res.cloudinary.com/practicaldev/image/fetch/s--1vSzhe0n--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h870m55u4vvpe3vj7doh.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--1vSzhe0n--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h870m55u4vvpe3vj7doh.png)
Forms -
[![Forms](https://res.cloudinary.com/practicaldev/image/fetch/s--BpvF_Zmk--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2to2u7uufwxfck0dxqkj.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--BpvF_Zmk--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2to2u7uufwxfck0dxqkj.png)
Tables -
[![Tables](https://res.cloudinary.com/practicaldev/image/fetch/s--SE9z8l9P--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/quwjjls2amtzxa6zepnc.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--SE9z8l9P--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/quwjjls2amtzxa6zepnc.png)

```
   var params = {
        Document: { 
            S3Object: {
                Bucket: 'xxxxxx',
                Name: 'download.jfif',
            }

        },
        FeatureTypes: ["TABLES", "FORMS"]
    };
    let response = await textract.analyzeDocument(params).promise()
    return response
```



Response available on [GitHub Gist](https://gist.github.com/zachjonesnoel/c56763bdea593f0ad30e6d9246557401#file-analyzedocumentresponse-json)

For `AnalyzeExpense` API, from the console and SDK API, you will get the response with both `SummaryFields` and `LineItemFields`.
Summary fields -
[![SummaryFields](https://res.cloudinary.com/practicaldev/image/fetch/s--hry_XvtK--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l2vs16e31xblixe0gyww.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--hry_XvtK--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l2vs16e31xblixe0gyww.png)
Line item fields
[![LineItemFields](https://res.cloudinary.com/practicaldev/image/fetch/s--gdhjKRxw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fsszs6hc98gvda963upm.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--gdhjKRxw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fsszs6hc98gvda963upm.png)

```
    var params = {
        Document: { 
            S3Object: {
                Bucket: 'xxxxxx',
                Name: 'download.jfif',
            }

        },
    };
    let response = await textract.analyzeExpense(params).promise()
    return response
```



Response available on [GitHub Gist](https://gist.github.com/zachjonesnoel/c56763bdea593f0ad30e6d9246557401#file-analyzeexpenseresponse-json)

#### Pricing

Amazon Textract's pricing varies upon the API that is executed as internally it uses *OCR technology* to process and extract textual information. Also based on the feature type, it focuses to extract either `FORM` or `TABLE` data.
Detailed information on pricing is available [on Textract pricing page](https://aws.amazon.com/textract/pricing/).

#### Conclusion

Amazon Textract enables applications to integrate with SDK APIs so that the documents or images with textual data from various representations of text in form of raw text, forms, tables are easily extratable. Now with the expense analysis support, Textract goes a level ahead to consolidate the items and also extract key information from the invoice or receipts. Textract also provides the confidence level / percentage of the extracted text making it a choice for the integrating applications to either consider it or neglect it.