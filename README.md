
Install Splunk 9.1.0.2 Linux Cent OS

To install the operating system for Splunk
In all the research and tests done between DB and RPM and Windows
The best case is the first Cent OS
Install Cent Linux without graphics for more security and compatibility with Splunk.
Visit the Splunk website, create an account, and download the latest version for your system from the Splunk download page. RPM packages are available for RedHat, CentOS and similar versions of Linux, in case of restrictions and sanctions, if there is a problem, let me know and I will send you the download link.
Start with the command code below

آموزش نصب Splunk در cent OS 

برای نصب سیستم عامل Splunk
در تمام تحقیقات و تست های انجام شده بین DB و RPM و ویندوز
بهترین حالت سیستم عاملOS Cent است
برای امنیت بیشتر و سازگاری با Splunk، Cent Linux را بدون گرافیک نصب کنید.
به وب سایت Splunk مراجعه کنید، یک اکانت ایجاد کنید و آخرین ورژن موجود برای سیستم خود را از صفحه دانلود Splunk دریافت کنید. پکیج های RPM برای RedHat, CentOS و ورژن های مشابه لینوکس موجود هستند ,  در صورت محدودیت ها و تحریم ها در صورت وجود مشکل اعلام کنید لینک دانلود براتون بفرستم.
 همانند کد دستوری زیر شروع کنید 


Download the .rpm file

****** # wget https://fdn.digiboy.ir/dlir-s3/splunk-9.1.0.2-b6436b649711.x86_64.rpm

Once the package is downloaded, install the Splunk Enterprise RPM in the default /opt/splunk directory using the RPM command as shown below.
به محض اینکه پکیج دانلود شد،‌ Splunk Enterprise RPM را در دایرکتوری پیش فرض /opt/splunk با استفاده از دستور RPM همانند زیر نصب کنید.

****** # rpm -i splunk-9.1.0.2-b6436b649711.x86_64.rpm

warning:  splunk-9.1.0.2-b6436b649711.x86_64.rpm: Header V4 DSA/SHA1 Signature, key ID 653fb112: NOKEY
useradd: cannot create directory /opt/splunk
complete 

Then use the Splunk Enterprise command interface to start the service.
 سپس از اینترفیس کامندی Splunk Enterprise برای استارت کردن سرویس استفاده کنید.
 ***** # /opt/splunk/bin/./splunk start 

Read the Splunk Software License Agreement (SPLUNK SOFTWARE LICENSE AGREEMENT) by pressing Enter, as soon as you finish reading it, you will be asked to accept this license. Enter Y to continue.
 توافق نامه لایسنس نرم افزار Splunk را (SPLUNK SOFTWARE LICENSE AGREEMENT) با فشردن Enter بخوانید، به محض اینکه مطالعه آنرا تمام کردید از شما خواسته میشود که این لایسنس را بپذیرید. برای ادامه Y را وارد کنید.
 
Do you agree with this license? [y/n]: y 
سپس برای اکانت administrator پسورد بسازید، پسورد شما باید شامل حداقل 8 کاراکتر ASCII قابل پرینت باشد.
Then create a password for the administrator account, your password must contain at least 8 printable ASCII characters.
Create credentials for the administrator account.
Characters do not appear on the screen when you type the password.
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password:
Please confirm new password:
 اگر همه فایل های نصب شده سالم باشند و چک های اولیه پاس شوند سرویس splunkd استارت خواهد شد. یک RSA private key که 2048 بیت میباشد ایجاد خواهد شد و شما قادر خواهید بود که اینترفیس وب Splunk دسترسی داشته باشید.
If all the installed files are healthy and the initial checks are passed, the splunkd service will start. An RSA private key of 2048 bits will be generated and you will be able to access the Splunk web interface.

All preliminary checks passed.

Starting splunk server daemon (splunkd)...  
Generating a 2048 bit RSA private key
......................+++
.....+++
writing new private key to 'privKeySecure.pem'
-----
Signature ok
subject=/CN=tecmint/O=SplunkUser
Getting CA Private Key
writing RSA key
Done
                                                           [  OK  ]

Waiting for web server at http://127.0.0.1:8000 to be available............. Done


If you get stuck, we're here to help.  
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://localhost:8000 
سپس پورت 8000 را که سرور Splunk روی آن listten میکند در فایروال خود با استفاده از دستور firewall-cmd باز کنید.
Then open the port 8000 on which the Splunk server listens in your firewall using the firewall-cmd command.

****# firewall-cmd --add-port=8000/tcp --permanent
****# firewall-cmd --reload 

Open a web browser and type the following url to access the Splunk web interface.
http://SERVER_IP:8000 
برای لاگین، یوزر admin و پسوردی که در طول پروسه نصب ساختید را وارد کنید.
To login, enter the admin user and the password you created during the installation process.

 مراحل تمام است 
 فقط درصورتی که نیاز به جداسازی نرم افزار دارید و یا میخواهید دسته بندی یا گروه بندی کنید َ بعد از دانلود و قبل از نصب این دستورات زیر را اجرا کنید و بعد اقدام به نصب کنید .
 The steps are complete
  Just in case you need to separate the software or you want to categorize or group it, after downloading and before installing it, run the following commands and then install it.

 
***** # groupadd splunk useradd -d /opt/splunk -m -g splunk splunk

Create the following directory
***** # mkdir /opt/installers

Copy the downloaded .rpm file to the new directory
***** # Cp splunk-9.1.0.2-b6436b649711.x86_64.rpm /opt/installers/

Change ownership
***** # chown -R splunk: /opt/splunk/ /opt/installers

Switch user
***** # su – splunk

 Change directory
***** # cd /opt/installers

 Install Splunk
***** # rpm -i splunk-9.1.0.2-b6436b649711.x86_64.rpm

Start Splunk quickly (accept license automatically)
***** # /opt/splunk/bin/splunk start –accept-license

Enter an administrator username
Please enter an administrator username:

Enter and confirm a password
Password must contain at least: * 8 total printable ASCII character(s). Please enter a new password: Please confirm new password:

 Enable at boot
***** #  /opt/splunk/bin/splunk enable boot-start

END




