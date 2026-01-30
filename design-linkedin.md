येथे "Design LinkedIn" या विषयावरील सिस्टीम डिझाइन मॉक इंटरव्ह्यूचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** LinkedIn सारख्या मोठ्या व्यावसायिक नेटवर्कसाठी 'जॉब सर्च' सिस्टीम डिझाइन करणे.
* **तज्ञ:** मार्क (माजी Google इंजिनिअरिंग मॅनेजर) आणि शियाली (Amazon मधील सीनियर सॉफ्टवेअर इंजिनिअर).
* **मुख्य फोकस:** AI-आधारित जॉब शोधणे आणि रँकिंग करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. कार्यात्मक आवश्यकता (Functional Requirements): [[03:26](http://www.youtube.com/watch?v=ICu8g9auh8E&t=206)]**

* वापरकर्त्याने स्वतःचे प्रोफाइल तयार करणे.
* विविध फिल्टर्स (उदा. स्थान, भूमिका, अनुभव) वापरून जॉब शोधणे.
* AI च्या मदतीने वापरकर्त्याला सर्वात संबंधित जॉब शिफारसी (Recommendations) मिळणे.

**२. अ-कार्यात्मक आवश्यकता (Non-Functional Requirements): [[07:21](http://www.youtube.com/watch?v=ICu8g9auh8E&t=441)]**

* **कमी लेटन्सी (Low Latency):** शोध निकाल २०० मिलिसेकंदच्या आत मिळणे आवश्यक आहे. [[07:33](http://www.youtube.com/watch?v=ICu8g9auh8E&t=453)]
* **उपलब्धता (Availability):** सिस्टीम नेहमी उपलब्ध असावी आणि बिघाड झाल्यास ती सावरता आली पाहिजे (Fault Tolerance).
* **सुसंगतता (Consistency):** येथे 'इव्हेंच्युअल कन्सिस्टन्सी' (Eventual Consistency) पुरेशी आहे; म्हणजे नवीन जॉब पोस्टिंग लगेच दिसले नाही तरी चालेल. [[08:33](http://www.youtube.com/watch?v=ICu8g9auh8E&t=513)]

**३. स्केल आणि मोजमाप (Scale & Capacity Planning): [[09:23](http://www.youtube.com/watch?v=ICu8g9auh8E&t=563)]**

* **वापरकर्ते:** १०० दशलक्ष दैनंदिन सक्रिय वापरकर्ते (DAU). [[09:37](http://www.youtube.com/watch?v=ICu8g9auh8E&t=577)]
* **ट्रॅफिक:** दिवसाला अंदाजे ४० दशलक्ष जॉब सर्च रिक्वेस्ट्स, ज्याचे पीक टाइममध्ये ५,००० ते २०,००० TPS (Transactions Per Second) पर्यंत रूपांतर होऊ शकते. [[11:32](http://www.youtube.com/watch?v=ICu8g9auh8E&t=692)]
* **डेटा:** सुमारे १० दशलक्ष सक्रिय जॉब्सचा डेटा हाताळणे. [[13:24](http://www.youtube.com/watch?v=ICu8g9auh8E&t=804)]

**४. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[20:01](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1201)]**

* **API Gateway:** लोड बॅलन्सिंग आणि रेट लिमिटिंगसाठी. [[20:10](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1210)]
* **Elastic Search:** जलद आणि कार्यक्षम शोधासाठी (Search) याचा वापर केला गेला, कारण हे मजकूर आधारित शोधासाठी उत्तम आहे. [[25:40](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1540)]
* **DynamoDB (NoSQL):** जॉबची सर्व माहिती (Metadata) साठवण्यासाठी याचा वापर केला, कारण ते स्केलेबल आहे. [[25:17](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1517)]

**५. रँकिंग आणि पर्सनलायझेशन (Ranking & AI Integration): [[30:55](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1855)]**

* शोधलेले निकाल केवळ तारखेनुसार न दाखवता वापरकर्त्याच्या आवडीनुसार दाखवण्यासाठी **Ranking Service** चा वापर केला. [[31:11](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1871)]
* **Personalization Service:** वापरकर्त्याचे मागील क्लिक्स, अनुभव आणि कौशल्ये लक्षात घेऊन AI (उदा. LLM किंवा GenAI) च्या मदतीने संबंधित जॉब्सना 'स्कोर' देणे. [[32:14](http://www.youtube.com/watch?v=ICu8g9auh8E&t=1934)]

**६. कार्यक्षमता सुधारणे (Performance Optimization): [[39:32](http://www.youtube.com/watch?v=ICu8g9auh8E&t=2372)]**

* **Caching:** वारंवार सर्च होणारे कीवर्ड्स (उदा. "AI Jobs") आणि वापरकर्त्याचे प्रोफाइल डेटा 'कॅश' (Redis सारख्या तंत्रज्ञानाने) केल्यास लेटन्सी कमी होते. [[40:34](http://www.youtube.com/watch?v=ICu8g9auh8E&t=2434)]
* **Fallback Logic:** जर AI आधारित रँकिंग सर्व्हिस फेल झाली, तर सिस्टीमने साध्या लॉजिकवर (उदा. नवीन जॉब्स आधी दाखवणे) स्विच व्हावे. [[43:12](http://www.youtube.com/watch?v=ICu8g9auh8E&t=2592)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ LinkedIn सारख्या जटिल सिस्टीममध्ये 'सर्च' आणि 'AI' चे एकत्रीकरण कसे करावे हे स्पष्ट करतो. मुलाखतीत तांत्रिक निर्णयांचे (उदा. Elastic Search किंवा NoSQL निवडणे) समर्थन करणे आणि सिस्टमची कार्यक्षमता वाढवण्यासाठी कॅशिंगचा वापर करणे किती महत्त्वाचे आहे, हे यातून शिकायला मिळते.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=ICu8g9auh8E](https://www.youtube.com/watch?v=ICu8g9auh8E)
