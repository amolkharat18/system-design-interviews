येथे "Design Tiny URL / Bitly" या विषयावरील सिस्टीम डिझाइन ट्युटोरियलचा मराठीतील तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** TinyURL किंवा Bitly सारखी URL शॉर्टनर सिस्टीम डिझाइन करणे.
* **चॅनेल:** InterviewWithBunny.
* **मुख्य उद्देश:** मोठ्या प्रमाणावरील (High Scale) ट्रॅफिक हाताळण्यासाठी एक स्केलेबल आणि विश्वासार्ह सिस्टीम तयार करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. सिस्टीम डिझाइनचा ५-पाच टप्प्यांचा फ्रेमवर्क: [[03:17](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=197)]**
कोणत्याही सिस्टीम डिझाइन मुलाखतीत खालील पाच टप्पे पाळावेत:

1. गरजा गोळा करणे (Requirement Gathering).
2. मुख्य घटक ओळखणे (Identify Core Entities).
3. API तयार करणे (API Creation).
4. उच्च-स्तरीय डिझाइन (High-Level Design).
5. तपशीलवार डिझाइन (Low-Level Design).

**२. गरजांचे विश्लेषण (Functional & Non-Functional Requirements): [[04:28](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=268)]**

* **कार्यात्मक (Functional):** लांब URL चे संक्षिप्त रूपात रूपांतर करणे आणि शॉर्ट URL वरून मूळ URL वर रिडायरेक्ट करणे. [[04:41](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=281)]
* **अ-कार्यात्मक (Non-Functional):** कमी लेटन्सी (Low Latency < 200ms), उच्च उपलब्धता (High Availability) आणि शॉर्ट URL युनिक असणे. [[07:19](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=439)]
* **Scale:** १०० दशलक्ष दैनंदिन सक्रिय वापरकर्ते (DAU) आणि १ अब्ज शॉर्टन लिंक्स हाताळणे. [[09:34](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=574)]

**३. URL शॉर्टन करण्याची पद्धत (Encryption Logic): [[27:10](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=1630)]**

* **MD5/SHA-1:** या अल्गोरिदमचा वापर करून मूळ URL चे हॅशिंग करणे. मात्र, यात 'Collision' (दोन वेगवेगळ्या URL ला एकच शॉर्ट कोड मिळणे) होण्याची शक्यता असते. [[29:35](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=1775)]
* **Counter Approach:** प्रत्येक नवीन URL साठी एक स्वयंचलित वाढणारा क्रमांक (ID) वापरणे. परंतु वितरित सिस्टीममध्ये (Distributed System) सर्व सर्व्हरवर एकच काउंटर राखणे कठीण असते. [[39:52](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=2392)]

**४. प्रगत डिझाइन (Zookeeper & Snowflake ID): [[57:05](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=3425)]**

* **Zookeeper:** ही एक को-ऑर्डिनेशन सर्व्हिस आहे. ती प्रत्येक सर्व्हरला एक युनिक 'Worker ID' देते. [[01:02:40](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=3760)]
* **Snowflake ID:** ६४-बिटचा एक युनिक आयडी तयार करण्यासाठी 'Time Stamp' + 'Worker ID' + 'Local Counter' यांचा वापर केला जातो. यामुळे कोणत्याही बाह्य सर्व्हिसला कॉल न करता स्थानिक पातळीवर युनिक आयडी तयार होतो, ज्यामुळे लेटन्सी कमी होते. [[01:03:30](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=3810)]

**५. हायब्रिड सोल्यूशन (Optimal Design): [[01:09:16](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=4156)]**

* तयार केलेला युनिक 'Snowflake ID' पुन्हा हॅश (MD5) करून त्यातील पहिले ६-७ वर्ण वापरणे ही सर्वात प्रभावी पद्धत आहे. यामुळे डुप्लिकेशनची शक्यता शून्य होते.

**६. रिडायरेक्शन आणि डेटाबेस (Redirection & Database): [[01:14:37](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=4477)]**

* **301 Redirect:** हे 'कायमस्वरूपी' (Permanent) रिडायरेक्शन आहे. ब्राउझर हे कॅश करतो, ज्यामुळे सर्व्हरवर कमी ताण येतो. [[01:15:04](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=4504)]
* **302 Redirect:** हे 'तात्पुरते' (Temporary) रिडायरेक्शन आहे. हे ॲनालिटिक्स (उदा. किती लोकांनी क्लिक केले) ट्रॅक करण्यासाठी उपयुक्त आहे. [[01:15:36](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=4536)]
* **Caching:** डेटाबेसवरील ताण कमी करण्यासाठी **Redis** सारख्या कॅशिंग लेयरचा वापर करणे. [[54:28](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=3268)]
* **Database:** डेटा साठवण्यासाठी **MySQL** किंवा **PostgreSQL** वापरता येते, जिथे शॉर्ट URL वर 'Indexing' करणे आवश्यक आहे. [[01:17:42](http://www.youtube.com/watch?v=Y-BO_4XNw8c&t=4662)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की एका साध्या URL शॉर्टनरला स्केलेबल बनवण्यासाठी **Zookeeper**, **Snowflake ID** आणि **Redis Caching** यांसारखी प्रगत तंत्रे कशी वापरावीत. केवळ हॅशिंग करण्यापेक्षा 'Worker ID' आधारित युनिक आयडी तयार करणे हे मोठ्या सिस्टीम्ससाठी सर्वोत्तम सोल्यूशन आहे.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=Y-BO_4XNw8c](https://www.youtube.com/watch?v=Y-BO_4XNw8c)
