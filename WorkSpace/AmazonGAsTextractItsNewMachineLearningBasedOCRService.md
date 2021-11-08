# Amazon GAs Textract, Its New Machine Learning-Based OCR Service

[Alex Woodie](https://www.datanami.com/author/alex/)

![img](https://2s7gjr373w3x22jf92z99mgm5w-wpengine.netdna-ssl.com/wp-content/uploads/2019/06/document_shutterstock_pling-300x206.jpg)

Companies that rely on optical character recognition (OCR) to digitize the content of printed forms may be interested in Textract, a new machine learning-based OCR service that just became available from Amazon Web Services. The OCR service can digitize simple text as well as more complex data contained in forms and tables.

OCR is rudimentary form of AI, and it isn’t new. In fact, organizations have been using the technology to bridge gap between the world of printed forms and digitized data since 1914, when the earliest OCR technology was developed.

Despite the decades of productive OCR use, there are drawbacks with standard implementations of the technology. One of the biggest disadvantages is the need to continually adapt the OCR rules to account for forms that change over time, not to mention configuring OCR to work with new forms.

This requires an investment in human programmers to maintain the extract rules that guide the OCR. Vendors in the space have made progress in minimizing the amount of OCR maintenance work, but it’s never been zero.

That’s the core area where AWS says it’s made improvements to OCR with Textract. The cloud giant says its technology can automatically detect the layout of a document, including where its key elements reside on the page, without any coding or configuration of templates. AWS also claims that Textract can “understand the data relationships” contained in embedded forms or tables, and maintain the context of the data as it converts it from a document into a digitized form.

The secret to all this automated understanding and maintaining of context, of course, is machine learning. AWS says that it has trained Textract’s machine learning algorithm on millions of documents across multiple industries, ranging from contracts, tax documents, and sales orders to enrollment forms, benefit applications, and insurance claims.

All that training helps to minimize the human maintenance required. The key question, of course, is how much human maintenance will be required to maintain a high level of OCR accuracy with Textract.

AWS claims there won’t be much human intervention required. “You no longer need to maintain code for every document or form you might receive or worry about how page layouts change over time,” the company says.[![img](https://2s7gjr373w3x22jf92z99mgm5w-wpengine.netdna-ssl.com/wp-content/uploads/2018/09/AWS.png)](https://2s7gjr373w3x22jf92z99mgm5w-wpengine.netdna-ssl.com/wp-content/uploads/2018/09/AWS.png)

However, the company isn’t guaranteeing 100% accuracy. The service comes with an “adjustable confidence thresholds” that allows users to configure the system to automatically flag content that Textract is not sure about.

“For instance, if you are extracting information from tax documents and want to ensure high accuracy, then you can create business logic to flag any extracted information with a confidence score lower than 95% to be reviewed by a human,” the company says.

Textract works with a range of document inputs, including scans from multi-function devices, PDFs, and photos. It’s default is to output the OCR extract in JSON format. It will automatically load the JSON into one of several AWS repositories, including Amazon DynamoDB, Amazon S3, Amazon Comprehend, or Amazon Elasticsearch Service.

AWS exposes two APIs with Textract, including the Detect Document Text API and the Analyze Document API. The first API works with textual data, while the second one is designed to work with data contained in simple forms and more complex tables.

The Analyze Document Text API can create key-value pairs from data contained in simple forms. The software automatically maintains the relationships between the individual pieces of source data, which retains the inherent context contained in the document so that it can be referenced later.

Similarly, when using the Analyze Document Text API to extract information from tables contained in more structured documents, such as financial or medical records, Textract gives users the option of loading the data into a pre-defined schema, which will be a useful for loading the data into existing applications or business intelligence reports.

Textract debuted last fall, when AWS CEO Andy Jassy [announced the beginning of beta testing](https://www.datanami.com/2018/11/28/aws-bolsters-machine-learning-services-at-reinvent/) for the service during the cloud giant’s Re:Invent conference. AWS announced last week that the testing is now done, and [customers can begin using the service](https://aws.amazon.com/about-aws/whats-new/2019/05/amazon-textract-now-generally-available/) on meaningful workloads. However, it’s only available in four AWS regions, including Northern Virginia, Ohio, Oregon, and Ireland.

For more information, see the [AWS Textract website](https://aws.amazon.com/textract).

**Related Items:**

[AWS Bolsters Machine Learning Services at Re:Invent](https://www.datanami.com/2018/11/28/aws-bolsters-machine-learning-services-at-reinvent/)

[This Week in Graph and Entity Analytics](https://www.datanami.com/2016/12/07/week-graph-entity-analytics/)

Tags: [amazon](https://www.datanami.com/tag/amazon-2/), [Amazon Elasticsearch](https://www.datanami.com/tag/amazon-elasticsearch/), [Amazon Web Services](https://www.datanami.com/tag/amazon-web-services/), [document database](https://www.datanami.com/tag/document-database/), [json](https://www.datanami.com/tag/json/), [key-value pairs](https://www.datanami.com/tag/key-value-pairs/), [machine learning](https://www.datanami.com/tag/machine-learning/), [OCR](https://www.datanami.com/tag/ocr/), [Textract](https://www.datanami.com/tag/textract/)