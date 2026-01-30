येथे "Design Google Drive / Dropbox" या विषयावरील सिस्टीम डिझाइन मॉक इंटरव्ह्यूचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** गुगल ड्राइव्ह (Google Drive) किंवा ड्रॉपबॉक्स (Dropbox) सारखी फाइल शेअरिंग आणि सिंकिंग सिस्टीम डिझाइन करणे.
* **तज्ञ:** ॲलेक्स (Shopify मधील माजी इंजिनिअरिंग मॅनेजर).
* **मुख्य उद्देश:** फाइल अपलोड, डाउनलोड आणि विविध उपकरणांमध्ये (Devices) सिंकिंग प्रक्रिया कशी कार्य करते हे समजून घेणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक गरजा (Functional Requirements): [[03:58](http://www.youtube.com/watch?v=4_qu1F9BXow&t=238)]**

* **अपलोड आणि डाउनलोड:** वापरकर्त्यांना कोणत्याही प्रकारच्या फाइल्स अपलोड आणि डाउनलोड करता आल्या पाहिजेत.
* **सिंकिंग (Syncing):** एका उपकरणावर फाइल बदलल्यास ती इतर सर्व उपकरणांवर (Mobile, Desktop, Web) अपडेट झाली पाहिजे. [[02:12](http://www.youtube.com/watch?v=4_qu1F9BXow&t=132)]
* **नोटिफिकेशन:** फाइलमध्ये बदल झाल्यास इतर उपकरणांना त्याची सूचना मिळणे आवश्यक आहे.

**२. आकडेवारी आणि स्केल (Metrics & Scale): [[07:11](http://www.youtube.com/watch?v=4_qu1F9BXow&t=431)]**

* **वापरकर्ते:** १०० दशलक्ष नोंदणीकृत वापरकर्ते, ज्यापैकी १ दशलक्ष दररोज सक्रिय (DAU) आहेत. [[02:49](http://www.youtube.com/watch?v=4_qu1F9BXow&t=169)]
* **डेटा साठवणूक:** प्रत्येक वापरकर्त्याला १५ GB मर्यादा आहे. एकूण १.५ पेटाबाइट (PB) डेटा हाताळण्याची क्षमता. [[07:20](http://www.youtube.com/watch?v=4_qu1F9BXow&t=440)]
* **ट्रॅफिक:** दिवसाला सरासरी ५ टेराबाइट (TB) डेटा ट्रॅफिक. [[08:23](http://www.youtube.com/watch?v=4_qu1F9BXow&t=503)]

**३. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[10:59](http://www.youtube.com/watch?v=4_qu1F9BXow&t=659)]**

* **Load Balancer:** येणारा ट्रॅफिक विभागण्यासाठी (उदा. AWS ELB). [[11:29](http://www.youtube.com/watch?v=4_qu1F9BXow&t=689)]
* **API Servers:** ॲप्लिकेशन लॉजिक हाताळण्यासाठी. [[12:10](http://www.youtube.com/watch?v=4_qu1F9BXow&t=730)]
* **Cloud Storage (S3):** प्रत्यक्ष फाइल्स साठवण्यासाठी Amazon S3 चा वापर. हे 'Resumable Uploads' साठी उपयुक्त आहे. [[12:59](http://www.youtube.com/watch?v=4_qu1F9BXow&t=779)]
* **Metadata Database:** फाइलची माहिती (नाव, आकार, व्हर्जन) साठवण्यासाठी **MySQL** सारख्या रिलेशनल डेटाबेसचा वापर, कारण येथे 'Consistency' महत्त्वाची आहे. [[31:01](http://www.youtube.com/watch?v=4_qu1F9BXow&t=1861)]

**४. फाइल सिंकिंग आणि नोटिफिकेशन प्रक्रिया: [[32:17](http://www.youtube.com/watch?v=4_qu1F9BXow&t=1937)]**

* **Notification Service:** फाइल अपलोड झाल्यावर ही सेवा इतर उपकरणांना (Clients) सूचित करते. [[32:26](http://www.youtube.com/watch?v=4_qu1F9BXow&t=1946)]
* **Long Polling / Pub-Sub:** उपकरणांनी नवीन बदलांसाठी सर्व्हरशी कनेक्ट राहणे.

**५. कार्यक्षमता आणि सुरक्षा (Performance & Security): [[20:30](http://www.youtube.com/watch?v=4_qu1F9BXow&t=1230)]**

* **Client-side Compression:** फाइल अपलोड करण्यापूर्वी क्लायंटच्या बाजूला कॉम्प्रेस करणे, ज्यामुळे बँडविड्थ वाचते. [[20:58](http://www.youtube.com/watch?v=4_qu1F9BXow&t=1258)]
* **Client-side Encryption:** सुरक्षेसाठी फाइल क्लायंटच्या बाजूलाच एनक्रिप्ट करणे. [[41:03](http://www.youtube.com/watch?v=4_qu1F9BXow&t=2463)]
* **CDN (Content Delivery Network):** फाइल्स जलद डाउनलोड करण्यासाठी वापरकर्त्याच्या जवळच्या भौगोलिक क्षेत्रात डेटा कॅश करणे. [[39:24](http://www.youtube.com/watch?v=4_qu1F9BXow&t=2364)]

**६. प्रगत सुधारणा (Advanced Improvements): [[36:32](http://www.youtube.com/watch?v=4_qu1F9BXow&t=2192)]**

* **Regional Scaling:** विविध खंडांमध्ये (उदा. उत्तर अमेरिका, युरोप) स्वतंत्र सर्व्हर्स ठेवणे जेणेकरून लेटन्सी कमी होईल. [[36:52](http://www.youtube.com/watch?v=4_qu1F9BXow&t=2212)]
* **Conflict Resolution:** जर दोन उपकरणांवरून एकाच वेळी एकाच नावाच्या फाइलमध्ये बदल झाले, तर सिस्टीमने वेळेनुसार (Timestamp) किंवा डुप्लिकेट फाइल तयार करून तो संघर्ष सोडवला पाहिजे. [[46:45](http://www.youtube.com/watch?v=4_qu1F9BXow&t=2805)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की फाइल शेअरिंग सिस्टीममध्ये केवळ डेटा साठवणे महत्त्वाचे नाही, तर **Metadata Management** आणि **Notification Service** द्वारे सिंकिंग अचूक ठेवणे अत्यंत आवश्यक आहे. तसेच, S3 आणि MySQL सारख्या विश्वसनीय साधनांचा वापर करून सिस्टीमची 'Trust' आणि 'Availability' वाढवता येते.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=4_qu1F9BXow](https://www.youtube.com/watch?v=4_qu1F9BXow)
