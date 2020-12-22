# **Email-PDFs**
The purpose of this script is to generate a PDF report based on sales numbers of cars. Then to email that PDF report as an attachment.

## **Structure**
The following outlines the general structure of the script. It also outlines the steps taken to get to the desired results.

### **Summarize Data**

Before generating a report, must calculate some numbers to summarize total sales.

**1.)** calculate the car model that had the most sales and format results as a string like the following:
```
"The {car model} had the most sales: {total sales}"
```
**2.)** calculate the most popular car year for each car make/model and for every year and format the results as a string like the following:
```
"The most popular year was {year} with {total sales in that year} sales."
```

### **PDF and Email**
Once data is properly summarized, can now generate a PDF report based on the sales data of cars and send an Email containing that PDF report as an attachment.

To generate PDF:
* use reports.generate() function
* report should be named as **cars.pdf** and placed in the folder **/tmp/**.
* content of PDF should have summary paragraph of sales numbers and a table of the information organized by ID number.

To send email:
* use emails.generate() and emails.send() methods
* use following details in emails.generate() method: 'From': automation@example.com, 'To': <user>@example.com, 'Subject line': Sales summary for last month, 'E-mail Body': The same summary from the PDF but using '\n' between the lines, 'Attachment': Attach the PDF path

## **Example**
Included is an example script 'example.py' that provides an example of how to invoke both the 'reports.py' and 'emails.py' scripts to generate a PDF report and send that PDF as an attachment in an email. This assumes that both scripts mentioned above are in the same working directory as the script that is calling them.
```python
reports.generate(filename, title, additional_info, table_data)
sender = "sender@example.com"
receiver = "receiver@example.com".format(os.environ.get('USER'))
subject = "Subject"
body = "Body ..."
message = emails.generate(sender, receiver, subject, body, attachment_filename)
emails.send(message)
```
