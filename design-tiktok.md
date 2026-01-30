येथे "Google System Design Interview: Design TikTok" या व्हिडिओचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** टिक-टॉक (TikTok) सारख्या जागतिक स्तरावरील शॉर्ट-व्हिडिओ प्लॅटफॉर्मची सिस्टीम डिझाइन.
* **तज्ञ:** मार्क (माजी Google इंजिनिअरिंग मॅनेजर).
* **मुख्य फोकस:** व्हिडिओ अपलोड आणि स्ट्रीमिंग (Viewing) साठी बॅक-एंड सिस्टीम तयार करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. सिस्टीमची व्याप्ती आणि स्केल (Scope & Scale): [[03:00](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=180)]**

* **वापरकर्ते:** १ अब्ज वापरकर्ते, १५० देशांमध्ये पसरलेले.
* **व्हिडिओ:** दरवर्षी १० अब्ज व्हिडिओ अपलोड आणि दररोज १ अब्ज व्हिडिओ व्ह्यूज. [[03:10](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=190)]
* **यशस्वीतेचे निकष (Success Metrics):** "Time in app" (वापरकर्ता ॲपमध्ये किती वेळ घालवतो) हे वाढवणे, जे सध्या सरासरी १ तास आहे. [[05:20](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=320)]

**२. आकडेवारी आणि साठवणूक (Metrics & Storage): [[08:40](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=520)]**

* **व्हिडिओ आकार:** सरासरी १० सेकंदाचा व्हिडिओ = १ MB. [[09:10](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=550)]
* **एकूण डेटा:** दरवर्षी १० पेटाबाइट (PB) कच्चा डेटा. प्रतिकृती (Replication) आणि वेगवेगळ्या फॉरमॅट्सचा विचार करता १०० PB/year साठवणूक लागेल. [[11:30](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=690)]
* **डेटाबेस:** व्हिडिओ फाइल्ससाठी **AWS S3 (Blob Storage)** आणि व्हिडिओच्या माहितीसाठी (Metadata) **NoSQL (DynamoDB)** वापरण्याचा सल्ला दिला. [[12:00](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=720)]

**३. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[20:00](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=1200)]**

* **दोन मुख्य सेवा:**
1. **Upload Service:** व्हिडिओ S3 मध्ये पाठवण्यासाठी आणि मेटाडेटा अपडेट करण्यासाठी. [[34:10](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=2050)]
2. **App Service:** वापरकर्त्याला फीड दाखवण्यासाठी.


* **CDN (Content Delivery Network):** लोकप्रिय व्हिडिओ वापरकर्त्याच्या जवळच्या भौगोलिक क्षेत्रात कॅश (Cache) करण्यासाठी, ज्यामुळे स्ट्रीमिंग वेगवान होते. [[29:30](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=1770)]

**४. 'For You' फीड जनरेशन (Recommendation Algorithm): [[35:40](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=2140)]**

* टिक-टॉकचे मुख्य वैशिष्ट्य म्हणजे त्याचा अल्गोरिदम. मार्कने येथे **Machine Learning (ML)** सिस्टीम सुचवली आहे.
* ही सिस्टीम वापरकर्त्याचे प्रोफाइल, मागील पसंती (Likes), भाषा आणि स्थान यानुसार व्हिडिओ आयडीची यादी तयार करते. [[39:10](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=2350)]
* **Exclusion Profile:** वापरकर्त्याने एखादा कंटेंट नाकारला तर तो त्वरित फीडमधून काढण्यासाठी 'Rule-based filter' वापरणे. [[56:30](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=3390)]

**५. अडथळे आणि निराकरण (Bottlenecks & Solutions): [[58:50](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=3530)]**

* **Real-time Performance:** वापरकर्त्याने स्क्रोल केल्यावर लगेच व्हिडिओ सुरू होण्यासाठी **"Read-ahead"** तंत्र वापरले जाते, जिथे पुढचे १०-२० व्हिडिओ आधीच बॅकग्राउंडला लोड केले जातात. [[01:01:00](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=3660)]
* **Computing Bottleneck:** 'For You' फीड जनरेट करणे हे खूप 'Compute heavy' काम आहे. हे कमी करण्यासाठी काही प्रक्रिया थेट वापरकर्त्याच्या फोनवर (On-device GPU वापरून) हलवण्याचा विचार केला जाऊ शकतो. [[01:02:10](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=3730)]

**६. खर्चाचे नियोजन (Cost Optimization): [[24:00](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=1440)]**

* **Tiered Storage:** जुन्या किंवा कमी पाहिलेल्या व्हिडिओंना 'Cold Storage' मध्ये हलवणे, ज्यामुळे साठवणुकीचा खर्च कमी होतो. [[24:40](http://www.youtube.com/watch?v=NHqdG-aZxOk&t=1480)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की टिक-टॉकसारख्या प्रचंड मोठ्या प्लॅटफॉर्मसाठी केवळ व्हिडिओ साठवणे पुरेसे नाही, तर **ML-आधारित फीड जनरेशन** आणि **CDN द्वारे वेगवान डिलिव्हरी** हे यशाचे मुख्य घटक आहेत. डिझाइनमध्ये साध्या (Rule-based) आणि जटिल (ML-based) दोन्ही पद्धतींचा वापर करून वापरकर्त्याचा अनुभव सुधारता येतो.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=NHqdG-aZxOk](https://www.youtube.com/watch?v=NHqdG-aZxOk)
