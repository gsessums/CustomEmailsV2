# CustomEmailsV2
## Description: 
CustomEmailsV2 is similar to CustomEmails except that is written in Bash. It uses AWK and SED (stream editor) to produce email files suitable for sending personalized emails **only** to customers with an **owe amount** greater than **paid amount**. 

### Several files are included for testing:
* customer.txt
    * File containing sample input containing one customer per line
    * Each customer line contains:
        * \<email\>,\<full name\>, \<title\>,\<paid amount\>,\<owed amount\>
        * For example: 
            * petem@xyz.net,Pete Moss,Mr.,10580.00,100
            * pcorn@abc.net,Pop Corn,Col.,50,200
* template.txt
    * File containing references to variable (all caps) which should be substituted with values for each customer meeting the criteria mention above.
    * For Example:
        * EMAIL - customer email address (1st attribute)
        * TITLE - customer title (3rd attribute)
        * FULLNAME - full customer name
        * NAME - customer name 
        * AMOUNT - owe amount
        * DATE - date the payment must be received. (passed as a parameter to customEmails.pl)
    * Sample:
        MAIL FROM:<bill.king@croc.com>
        RCPT TO:<EMAIL>
        DATA
        From: "Bill King" <bill.king@croc.com>
        To: "FULLNAME" <EMAIL>
        Subject: Payment is Due

        Dear TITLE NAME,
        We appreciate your business with Completely Reliable Outlet Corp.  You 
        would be an even more valued customer if you will pay us $AMOUNT.  If 
        you don't pay us by DATE, we will double the amount you owe us. 

        If you have any questions regarding your account, please contact
        me at 222-555-1234.

        Bill King
        Collections Manager
        . 

## Installation
Clone the repository wherever you like (e.g. `~/Projects/CustomEmailsV2`):
```bash
git clone https://github.com/gsessums/CustomEmailsV2.git
```

## Usage
To execute enter the following command with date (payment deadline), then follow the on screen prompts.
```bash
./customEmailsV2.pl mm/dd/yyyy 
```

## Credits
Author: [Geoffrey Sessums](http://www.geoffreysessums.com)

## License
MIT License

Copyright (c) 2018 Geoffrey Sessums

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
