येथे "Meta System Design Interview: Design Instagram" या व्हिडिओचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** इंस्टाग्राम (Instagram) सारख्या मोठ्या सोशल मीडिया प्लॅटफॉर्मची सिस्टीम डिझाइन करणे.
* **तज्ञ:** कार्तिकेय (माजी Meta डेटा इंजिनिअर) आणि मार्क.
* **मुख्य उद्देश:** फोटो अपलोड, न्यूज फीड, सर्च आणि फॉलो फिचर्ससाठी स्केलेबल सिस्टीम कशी तयार करावी.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक आणि अ-कार्यात्मक गरजा (Requirements): [[03:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=180)]**

* **कार्यात्मक:** फोटो अपलोड करणे, शोधणे (Search), एकमेकांना फॉलो करणे आणि न्यूज फीड पाहणे. [[01:45](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=105)]
* **अ-कार्यात्मक:** उच्च उपलब्धता (High Availability), जगभरातील वापरकर्त्यांसाठी कमी लेटन्सी (Latency < 1 sec for news feed), आणि डेटाची विश्वासार्हता (Reliability). [[04:10](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=250)]

**२. ट्रॅफिक आणि स्केलचे मोजमाप (Metrics & Scale): [[12:30](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=750)]**

* **वापरकर्ते:** १ अब्ज एकूण वापरकर्ते, ज्यापैकी २५० दशलक्ष दैनंदिन सक्रिय (DAU) आहेत. [[12:45](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=765)]
* **वाचन (Read):** दर सेकंदाला २५,००० विनंत्या (Requests per second) आणि ५ GB/s बँडविड्थ. [[15:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=900)]
* **लेखन (Write):** दर सेकंदाला २५० फोटो अपलोड. [[18:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1120)]
* **साठवणूक (Storage):** दररोज ५ टेराबाइट (TB) डेटा, जो वर्षाला १०० TB पर्यंत जाऊ शकतो. [[20:10](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1210)]

**३. डेटा मॉडेलिंग (Data Modeling): [[22:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1320)]**

* **User Table:** युजरची माहिती साठवण्यासाठी. [[22:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1360)]
* **Photo Metadata Table:** फोटोचे लोकेशन (URL), टायटल आणि अपलोडरची माहिती साठवण्यासाठी (Relational DB). [[24:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1440)]
* **News Feed Table:** युजरच्या फीडमधील फोटोंची यादी साठवण्यासाठी (NoSQL). [[26:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1600)]
* **User Activity Table:** युजर कधी लॉगिन झाला, त्याचे फॉलोअर्स किती आहेत, हे ट्रॅक करण्यासाठी. [[31:30](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=1890)]

**४. हाय-लेव्हल डिझाइन (High-Level Design): [[34:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2040)]**

* **Load Balancer & API Gateway:** ट्रॅफिक विभागण्यासाठी आणि सुरक्षा (Rate Limiting) सुनिश्चित करण्यासाठी. [[38:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2280)]
* **Media Service:** फोटो अपलोड/डाउनलोड हाताळण्यासाठी. येथे 'Asynchronous Processing' साठी **Message Queues** चा वापर केला आहे. [[39:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2380)]
* **Storage Strategy:** प्रत्यक्ष फोटो **Object Storage (S3)** मध्ये आणि मेटाडेटा **Relational DB** मध्ये साठवला जातो. [[41:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2460)]

**५. न्यूज फीड सिस्टीम (News Feed Architecture): [[49:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2980)]**

* **Pre-computation:** फीड जलद दाखवण्यासाठी ते आधीच तयार (Pre-populate) करून **Cache** मध्ये ठेवले जाते. [[51:30](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=3090)]
* **Power Users (Celebrities):** ज्यांचे लाखो फॉलोअर्स आहेत, त्यांच्यासाठी वेगळी रणनीती वापरली जाते जेणेकरून सिस्टीमवर ताण येणार नाही. [[54:00](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=3240)]

**६. स्केलिंग तंत्र (Scaling Techniques): [[01:00:20](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=3620)]**

* **Sharding:** डेटाबेसवरील ताण कमी करण्यासाठी युजर आयडीनुसार डेटाचे तुकडे (Sharding) करणे.
* **CDN (Content Delivery Network):** जगभरातील युजर्सना त्यांच्या जवळच्या सर्व्हरवरून फोटो जलद दाखवण्यासाठी. [[48:40](http://www.youtube.com/watch?v=DXpJCh5_KT4&t=2920)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ स्पष्ट करतो की इंस्टाग्रामसारखी सिस्टीम डिझाइन करताना केवळ डेटा साठवणे पुरेसे नाही, तर **Read-heavy** सिस्टीमसाठी कॅशिंग (Caching) आणि न्यूज फीड जनरेशनसाठी कार्यक्षम अल्गोरिदम वापरणे अत्यंत आवश्यक आहे. तसेच, सेलिब्रिटी युजर्स (Power Users) आणि सामान्य युजर्स यांच्यासाठी वेगवेगळी वागणूक (Handling) सिस्टीमला अधिक कार्यक्षम बनवते.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=DXpJCh5_KT4](https://www.youtube.com/watch?v=DXpJCh5_KT4)
