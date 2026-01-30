येथे "FAANG System Design Interview: Design YouTube" या व्हिडिओचा मराठीतील तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** यूट्यूब (YouTube) सारख्या मोठ्या व्हिडिओ स्ट्रीमिंग प्लॅटफॉर्मची रचना करणे.
* **तज्ञ:** रवी (FAANG मधील सीनियर सॉफ्टवेअर इंजिनिअर, ११ वर्षांचा अनुभव).
* **मुख्य उद्देश:** व्हिडिओ अपलोड, वॉच आणि सर्च यांसारख्या मुख्य फिचर्ससाठी स्केलेबल सिस्टीम तयार करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक आणि अ-कार्यात्मक गरजा (Requirements): [[03:00](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=180)]**

* **कार्यात्मक:** व्हिडिओ अपलोड करणे, व्हिडिओ पाहणे आणि शोधणे (Search). [[01:50](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=110)]
* **अ-कार्यात्मक:** उच्च उपलब्धता (High Availability), स्केलेबिलिटी (Scalability), विश्वासार्हता (Reliability) आणि कमी लेटन्सी (Low Latency). [[03:15](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=195)]

**२. आकडेवारी आणि मोजमाप (Resource Estimation): [[05:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=340)]**

* **वापरकर्ते:** २ अब्ज एकूण युजर्स, ५०० दशलक्ष दररोज सक्रिय युजर्स (DAU). [[06:20](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=380)]
* **व्ह्यूव्हज:** दिवसाला साधारण २.५ अब्ज व्हिडिओ व्ह्यूव्हज. [[08:50](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=530)]
* **साठवणूक (Storage):** दिवसाला साधारण २०,००० टेराबाइट (TB) डेटा साठवण्याची गरज भासू शकते. [[12:20](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=740)]

**३. हाय-लेव्हल डिझाइन (High-Level Design): [[14:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=880)]**

* **API Gateway & Load Balancer:** सुरक्षितता (Authentication) आणि ट्रॅफिक विभागण्यासाठी. [[18:50](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1130)]
* **Upload Service:** व्हिडिओ अपलोड करण्यासाठी. [[19:30](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1170)]
* **Watch Service:** व्हिडिओ पाहण्यासाठी. [[29:10](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1750)]
* **Search Service:** व्हिडिओ शोधण्यासाठी. [[38:10](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2290)]

**४. व्हिडिओ अपलोड आणि ट्रान्सकोडिंग (Transcoding): [[24:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1480)]**

* **Blob Storage (S3):** प्रत्यक्ष व्हिडिओ फाइल्स साठवण्यासाठी. [[21:00](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1260)]
* **Transcoder Service:** मूळ व्हिडिओ वेगवेगळ्या फॉरमॅट्स आणि रिझोल्यूशनमध्ये (उदा. 360p, 720p, 1080p) रूपांतरित करण्यासाठी, जेणेकरून तो सर्व उपकरणांवर चालू शकेल. [[25:20](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1520)]
* **Metadata Store (SQL DB):** व्हिडिओचे नाव, टायटल आणि टॅग्ज साठवण्यासाठी. [[22:20](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1340)]

**५. व्हिडिओ स्ट्रीमिंग आणि कार्यक्षमता (Performance): [[31:00](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1860)]**

* **CDN (Content Delivery Network):** वापरकर्त्याच्या भौगोलिक स्थानानुसार जवळच्या सर्व्हरवरून व्हिडिओ जलद पोहोचवण्यासाठी. [[31:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1900)]
* **Adaptive Streaming:** युजरच्या इंटरनेट स्पीडनुसार व्हिडिओची क्वालिटी आपोआप बदलणे (उदा. स्पीड कमी झाल्यास आपोआप 480p वर येणे). [[35:10](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2110)]
* **Chunking:** व्हिडिओचे लहान तुकडे (Chunks) करणे जेणेकरून तो जलद लोड होईल. [[27:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=1660)]

**६. सर्च सिस्टीम (Search System): [[39:00](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2340)]**

* **Metadata Extraction:** व्हिडिओ अपलोड होतानाच त्याचे टायटल आणि टॅग्ज शोधून **Json** फाइलमध्ये साठवणे. [[39:10](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2350)]
* **Key-Value Store (Redis/DynamoDB):** कीवर्ड्स आणि त्याशी संबंधित व्हिडिओ आयडी साठवण्यासाठी, जेणेकरून सर्च जलद होईल. [[39:40](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2380)]
* **Fuzzy Search:** युजरने स्पेलिंग चुकले तरी योग्य व्हिडिओ सुचवण्यासाठी. [[41:30](http://www.youtube.com/watch?v=hqa2sfoGRlI&t=2490)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की यूट्यूबसारख्या प्रचंड मोठ्या प्लॅटफॉर्मसाठी **Transcoding** (वेगवेगळ्या उपकरणांसाठी व्हिडिओ तयार करणे), **CDN** (कमी लेटन्सीसाठी) आणि **Adaptive Bitrate Streaming** (इंटरनेटनुसार क्वालिटी बदलणे) हे घटक किती महत्त्वाचे आहेत. सिस्टीम स्केलेबल ठेवण्यासाठी डेटा रिप्लिकेशन आणि क्यूज (Queues) चा वापर करणे अनिवार्य आहे.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=hqa2sfoGRlI](https://www.youtube.com/watch?v=hqa2sfoGRlI)
