येथे "Amazon System Design Mock Interview: Design a Phone Company Billing System" या व्हिडिओचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** एका टेलिफोन कंपनीसाठी बिलिंग सिस्टीम (Billing System) डिझाइन करणे.
* **तज्ञ:** टिम (माजी Senior SWE, Amazon).
* **मुख्य उद्देश:** मोठ्या प्रमाणावरील डेटा हाताळून ग्राहकांसाठी अचूक बिल तयार करणारी सिस्टीम तयार करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक गरजा (Functional Requirements): [[01:43](http://www.youtube.com/watch?v=i_RCwKflp3I&t=103)]**

* ग्राहकांनी महिनाभरात केलेल्या फोन कॉल्सचा डेटा गोळा करणे.
* या डेटाच्या आधारे प्रत्येक ग्राहकासाठी मासिक बिल तयार करणे.
* बिल जनरेशनची प्रक्रिया मुख्यत्वे फोन कॉल्सवर आधारित असणे (डेटा युसेज किंवा पेमेंट व्यवहार यात समाविष्ट नाहीत). [[03:51](http://www.youtube.com/watch?v=i_RCwKflp3I&t=231)]

**२. स्केल आणि डेटाचे मोजमाप (Metrics & Scale): [[05:10](http://www.youtube.com/watch?v=i_RCwKflp3I&t=310)]**

* **ग्राहक संख्या:** ५० दशलक्ष (50 Million). [[05:25](http://www.youtube.com/watch?v=i_RCwKflp3I&t=325)]
* **कॉल व्हॉल्यूम:** प्रत्येक ग्राहक दिवसाला सरासरी १० बिल करण्यायोग्य कॉल्स करतो, असे मानल्यास दिवसाला ५०० दशलक्ष कॉल्स होतात. [[09:07](http://www.youtube.com/watch?v=i_RCwKflp3I&t=547)]
* **मासिक डेटा:** दरमहा साधारण १५ अब्ज कॉल रेकॉर्ड्सवर प्रक्रिया करावी लागेल. [[09:38](http://www.youtube.com/watch?v=i_RCwKflp3I&t=578)]
* **वेळ:** बिलिंग सायकल संपल्यानंतर २४ तासांच्या आत बिल उपलब्ध होणे आवश्यक आहे. [[10:39](http://www.youtube.com/watch?v=i_RCwKflp3I&t=639)]

**३. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[12:48](http://www.youtube.com/watch?v=i_RCwKflp3I&t=768)]**

* **दोन मुख्य डेटाबेस:**
1. **Call Records Database:** यामध्ये कॉल करणाऱ्याचा नंबर, ज्याला कॉल केला तो नंबर आणि कॉलचा कालावधी साठवला जातो. [[14:12](http://www.youtube.com/watch?v=i_RCwKflp3I&t=852)]
2. **Customer Database:** यामध्ये ग्राहकाचे नाव, पत्ता आणि त्यांच्या फोन प्लॅनची माहिती असते. [[15:08](http://www.youtube.com/watch?v=i_RCwKflp3I&t=908)]


* **Billing Service:** ही सर्व्हिस वरील दोन्ही डेटाबेसवरून माहिती घेऊन बिल तयार करते. [[17:17](http://www.youtube.com/watch?v=i_RCwKflp3I&t=1037)]
* **Billing Statement Database:** तयार झालेली बिले येथे साठवली जातात, जिथून ग्राहक ती पोर्टलवर पाहू शकतात. [[18:55](http://www.youtube.com/watch?v=i_RCwKflp3I&t=1135)]

**४. डेटाबेस निवड आणि विभागणी (Database & Sharding): [[26:02](http://www.youtube.com/watch?v=i_RCwKflp3I&t=1562)]**

* बिलिंग डेटासाठी **NoSQL (Document Store)** डेटाबेस वापरण्याचा सल्ला दिला आहे, कारण तो स्केलेबल आहे. [[26:22](http://www.youtube.com/watch?v=i_RCwKflp3I&t=1582)]
* **Sharding:** १५ अब्ज रेकॉर्ड्समधून विशिष्ट ग्राहकाचा डेटा शोधण्यासाठी **'Phone Number'** किंवा **'Area Code'** नुसार डेटाची विभागणी (Sharding) करणे सुचवले आहे. [[29:16](http://www.youtube.com/watch?v=i_RCwKflp3I&t=1756)]

**५. स्केलेबिलिटी आणि परफॉर्मन्स (Scalability & Performance): [[34:33](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2073)]**

* बिलिंग सर्व्हिस ही केवळ एक इन्स्टन्स नसून अनेक **Worker Instances** चा संच असेल. [[34:42](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2082)]
* **Orchestrator:** हा घटक कामाचा लोड तपासेल आणि आवश्यकतेनुसार वर्कर इन्स्टन्सेसची संख्या कमी-जास्त करेल (Elastic Scaling). [[38:29](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2309)]
* **Queue System:** बिल तयार करण्याच्या कामांची एक रांग (Queue) लावली जाईल, जेणेकरून २४ तासांचे उद्दिष्ट पूर्ण होईल. [[39:27](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2367)]

**६. सुरक्षा आणि उपलब्धता (Security & Availability): [[43:24](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2604)]**

* **Availability:** डेटा गमावू नये म्हणून प्रत्येक डेटाबेसच्या किमान दोन प्रती (Replication) ठेवणे आवश्यक आहे. [[44:00](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2640)]
* **Security:** ग्राहकांची वैयक्तिक माहिती सुरक्षित ठेवण्यासाठी डेटा एनक्रिप्शन (Encryption) आणि फायरवॉलचा वापर करणे. [[46:55](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2815)]
* ग्राहक पोर्टलसाठी **Reverse Proxy Server** वापरणे, जेणेकरून अंतर्गत सिस्टीम सुरक्षित राहील. [[47:42](http://www.youtube.com/watch?v=i_RCwKflp3I&t=2862)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की जेव्हा आपल्याला अब्जावधी रेकॉर्ड्सवर प्रक्रिया करायची असते, तेव्हा **Batch Processing**, **Database Sharding** आणि **Elastic Worker Queues** किती महत्त्वाचे ठरतात. ॲमेझॉनसारख्या कंपन्यांमध्ये अशा प्रकारे जटिल सिस्टीमचे सोप्या घटकांमध्ये विभाजन करून डिझाइन केले जाते.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=i_RCwKflp3I](https://www.youtube.com/watch?v=i_RCwKflp3I)
