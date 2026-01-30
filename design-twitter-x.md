येथे "Twitter (X) System Design Interview" या व्हिडिओचा मराठीतील तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** ट्विटर (आताचे x.com) सारख्या 'मायक्रो-ब्लॉगिंग' प्लॅटफॉर्मची रचना करणे.
* **तज्ञ:** युजीन (सीनियर सॉफ्टवेअर इंजिनिअर आणि मॅनेजर).
* **मुख्य उद्देश:** ट्विट पोस्ट करणे, टाइमलाईन जनरेशन आणि युजर फॉलोअर्स या सिस्टीमचे डिझाइन.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. प्राथमिक गरजा आणि गृहितके (Requirements & Assumptions): [[03:30](http://www.youtube.com/watch?v=3yW856jAbZA&t=210)]**

* **Read Heavy System:** ट्विटरवर ट्विट वाचण्याचे प्रमाण लिहिण्यापेक्षा कितीतरी पटीने जास्त असते (उदा. १:२० गुणोत्तर). [[03:50](http://www.youtube.com/watch?v=3yW856jAbZA&t=230)]
* **Eventual Consistency:** ट्विट पोस्ट केल्यावर तो सर्व फॉलोअर्सना दिसण्यासाठी ३० ते ६० सेकंदांचा उशीर चालतो. [[04:30](http://www.youtube.com/watch?v=3yW856jAbZA&t=270)]
* **Scale:** १ अब्ज वापरकर्ते आणि दररोज साधारण १०० दशलक्ष ट्विट्स हाताळणे. [[07:20](http://www.youtube.com/watch?v=3yW856jAbZA&t=440)]

**२. आकडेवारी आणि क्षमता (Capacity Estimation): [[08:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=520)]**

* दररोज साधारण १० टेराबाइट (TB) डेटा तयार होतो. [[09:00](http://www.youtube.com/watch?v=3yW856jAbZA&t=540)]
* पीक टाइममध्ये दर सेकंदाला ६,००० ते १२,००० ट्विट्स पोस्ट होऊ शकतात. [[09:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=580)]
* **Fan-out:** प्रत्येक ट्विट सरासरी २० फॉलोअर्सना पाठवावा लागतो, म्हणजेच दर सेकंदाला १,००,००० 'फॅन-आऊट' मेसेजेस होतात. [[10:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=640)]

**३. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[21:30](http://www.youtube.com/watch?v=3yW856jAbZA&t=1290)]**

* **Tweet Processor:** ट्विट मिळाल्यावर तो डेटाबेसमध्ये साठवणे आणि पुढील प्रक्रियेसाठी **Kafka** सारख्या मेसेज क्यूमध्ये पाठवणे. [[31:50](http://www.youtube.com/watch?v=3yW856jAbZA&t=1910)]
* **Database:** डेटा साठवण्यासाठी **Cassandra** (NoSQL) चा वापर, कारण यामध्ये वेळानुसार डेटा सॉर्ट करणे सोपे जाते. [[22:20](http://www.youtube.com/watch?v=3yW856jAbZA&t=1340)]
* **Caching:** टाइमलाईन जलद दाखवण्यासाठी **Redis** चा वापर करून ती आधीच तयार (Pre-generate) केली जाते. [[27:00](http://www.youtube.com/watch?v=3yW856jAbZA&t=1620)]

**४. टाइमलाईन जनरेशन प्रक्रिया (Timeline Generation Flow): [[33:00](http://www.youtube.com/watch?v=3yW856jAbZA&t=1980)]**

* **Push Model:** जेव्हा एखादा युजर ट्विट करतो, तेव्हा एक प्रोसेसर तो ट्विट त्याच्या सर्व फॉलोअर्सच्या वैयक्तिक 'इन-मेमरी' (Redis) टाइमलाईनमध्ये ढकलतो. [[35:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=2140)]
* **Linked List:** Redis मध्ये टाइमलाईन 'Double Linked List' स्वरूपात साठवली जाते, ज्यामुळे नवीन ट्विट जोडणे आणि जुने काढणे अत्यंत वेगवान ( वेळात) होते. [[39:20](http://www.youtube.com/watch?v=3yW856jAbZA&t=2360)]

**५. सेलिब्रिटी युजर्सची समस्या (Popular Users Problem): [[47:20](http://www.youtube.com/watch?v=3yW856jAbZA&t=2840)]**

* जर एखाद्या युजरचे कोट्यवधी फॉलोअर्स असतील, तर वरील 'Push Model' काम करत नाही कारण एकाच वेळी इतक्या लोकांना ट्विट पाठवणे कठीण होते.
* **Hybrid Model:** अशा 'पॉवर युजर्स'साठी 'Pull Model' वापरले जाते. त्यांचा ट्विट त्यांच्या फॉलोअर्सच्या टाइमलाईनमध्ये ढकलला जात नाही, तर फॉलोअर जेव्हा आपली टाइमलाईन रिफ्रेश करतो, तेव्हा तो ट्विट स्वतंत्रपणे खेचून (Fetch) आणला जातो. [[48:20](http://www.youtube.com/watch?v=3yW856jAbZA&t=2900)]

**६. ट्विट आयडी जनरेशन (Unique Tweet ID): [[49:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=2980)]**

* प्रत्येक ट्विटला जागतिक स्तरावर एकच आयडी (Globally Unique) मिळण्यासाठी ६४-बिट आयडी वापरला जातो. यामध्ये वेळेचा संदर्भ (Timestamp) असतो, ज्यामुळे ट्विट्स क्रमाने लावणे सोपे जाते. [[50:40](http://www.youtube.com/watch?v=3yW856jAbZA&t=3040)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ शिकवतो की ट्विटरसारख्या जटिल सिस्टीममध्ये **Caching (Redis)** आणि **Asynchronous Processing (Kafka)** किती महत्त्वाचे आहेत. सामान्य युजर्ससाठी 'Push' आणि सेलिब्रिटींसाठी 'Pull' असा हायब्रिड दृष्टिकोन वापरून सिस्टीमची कार्यक्षमता राखली जाते.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=3yW856jAbZA](https://www.youtube.com/watch?v=3yW856jAbZA)
