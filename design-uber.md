येथे "Uber System Design: Mock Interview" या व्हिडिओचा मराठीतील तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** उबेर (Uber) सारख्या 'राइड-हेलिंग' (Ride-hailing) सिस्टीमची रचना करणे.
* **तज्ञ:** डिमा कोरोलेव्ह (माजी Google इंजिनिअर) आणि मार्क.
* **मुख्य उद्देश:** ड्रायव्हर आणि रायडर यांना रिअल-टाइममध्ये जोडणारी स्केलेबल सिस्टीम तयार करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक गरजा (Functional Requirements): [[02:00](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=120)]**

* **रायडर (Rider):** गाडी बुक करणे, लोकेशन शेअर करणे, भाडे तपासणे आणि रेटिंग देणे. [[03:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=220)]
* **ड्रायव्हर (Driver):** स्वतःची उपलब्धता (Online/Offline) मार्क करणे, राईड स्वीकारणे किंवा नाकारणे आणि नेव्हिगेशन वापरणे. [[05:20](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=320)]
* **किंमत निश्चिती (Price Setting):** मागणीनुसार 'सर्ज प्राइसिंग' (Surge Pricing) लागू करणे. [[07:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=460)]

**२. अ-कार्यात्मक गरजा (Non-Functional Requirements): [[11:30](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=690)]**

* **उपलब्धता (Availability):** सिस्टीम कधीही डाऊन नसावी.
* **कमी लेटन्सी (Low Latency):** ड्रायव्हरला मॅच करण्याची प्रक्रिया अत्यंत वेगवान असावी.
* **रिअल-टाइम डेटा:** ड्रायव्हर आणि रायडरचे लोकेशन सतत अपडेट होणे आवश्यक आहे. [[12:00](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=720)]

**३. राईड मॅचिंग अल्गोरिदम (Ride Matching Algorithm): [[16:50](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1010)]**

* **Instant Book:** जे ड्रायव्हर्स ऑटो-एक्सेप्ट मोडमध्ये आहेत त्यांना प्राधान्य देणे. [[19:30](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1170)]
* **Sequential Requests:** सर्व ड्रायव्हर्सना एकाच वेळी विनंती न पाठवता, एकामागून एक ठराविक सेकंदांच्या (उदा. ७ सेकंद) अंतराने पाठवणे, जेणेकरून त्यांच्यात स्पर्धा होणार नाही. [[17:50](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1070)]

**४. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[23:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1420)]**

* **Load Balancer:** सुरुवातीला येणारा ट्रॅफिक विभागण्यासाठी. [[25:20](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1520)]
* **Geo-sharding:** शहरांनुसार (उदा. न्यूयॉर्क, बर्लिन) डेटाचे विभाजन करणे, जेणेकरून स्थानिक स्तरावर प्रक्रिया जलद होईल. [[28:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1720)]
* **API Gateway:** सुरक्षा आणि रेट लिमिटिंगसाठी. [[38:00](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2280)]

**५. डेटा सुसंगतता (Data Consistency): [[31:00](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1860)]**

* **Read Path:** केवळ माहिती पाहण्यासाठी (उदा. आसपासच्या गाड्या पाहणे) 'Eventual Consistency' वापरली जाते, जिथे थोडा उशीर चालतो. [[31:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1900)]
* **Write Path:** प्रत्यक्ष बुकिंग करताना 'Strong Consistency' आवश्यक असते, जेणेकरून एकच गाडी दोन लोकांना मिळणार नाही. [[32:30](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=1950)]

**६. रिअल-टाइम लोकेशन ट्रॅकिंग (Real-time Tracking): [[35:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2140)]**

* ड्रायव्हरचा फोन दर काही सेकंदांनी 'बीकन' (Beacon) किंवा 'कीप-अलाईव्ह' मेसेज पाठवून आपले लोकेशन सर्व्हरला कळवतो. [[36:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2200)]
* यासाठी हजारो विनंत्या प्रति सेकंद हाताळण्यासाठी वितरित सिस्टीम (Distributed System) वापरली जाते. [[37:20](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2240)]

**७. मॉनिटरिंग आणि मॅट्रिक्स (Monitoring & Metrics): [[41:30](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2490)]**

* रिअल-टाइम राईड्सची संख्या, ड्रायव्हरचे सरासरी अंतर आणि रायडरचा पिकअप वेळ यासारख्या गोष्टींवर लक्ष ठेवणे. [[42:40](http://www.youtube.com/watch?v=wL-Gx5XE9XE&t=2560)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की उबेरसारखी सिस्टीम डिझाइन करताना केवळ तंत्रज्ञान महत्त्वाचे नाही, तर 'प्रोडक्ट-फर्स्ट' विचार (उदा. पिकअप पॉइंट्स सुचवणे, ड्रायव्हरला व्यस्त ठेवणे) करणे खूप महत्त्वाचे आहे. डेटाबेस शार्डिंग आणि रिअल-टाइम ट्रॅकिंग या गोष्टी अशा सिस्टीमचे कणा आहेत.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=wL-Gx5XE9XE](https://www.youtube.com/watch?v=wL-Gx5XE9XE)
