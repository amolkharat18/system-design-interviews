येथे "System Design Interview: Design Robinhood" या व्हिडिओचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** रॉबिनहूड (Robinhood) सारख्या स्टॉक ट्रेडिंग ॲपची सिस्टीम डिझाइन करणे.
* **तज्ञ:** जॉर्डन (माजी Google सॉफ्टवेअर इंजिनिअर).
* **मुख्य फोकस:** रिअल-टाइम स्टॉक किमती दाखवणे आणि ऑर्डर्स व्यवस्थापित करणे.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. प्राथमिक गरजा आणि व्याप्ती (Requirements & Scope): [[01:41](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=101)]**

* **कार्यात्मक गरजा:** ऑर्डर्स पाठवणे, वापरकर्त्यांच्या पोझिशन्स (Holdings) ट्रॅक करणे आणि सर्वात महत्त्वाचे म्हणजे स्टॉक/ऑप्शन्सच्या अचूक किमती रिअल-टाइममध्ये दाखवणे.
* **स्केल:** १०० दशलक्ष (100 Million) वापरकर्ते आणि प्रत्येक वापरकर्त्याकडे सरासरी १०० स्टॉक्स, म्हणजेच एकूण १० अब्ज पोझिशन्सचा डेटा हाताळणे. [[03:23](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=203)]

**२. सिस्टीमचे तीन मुख्य स्तर (Three-Layer Architecture): [[05:22](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=322)]**

* **Exchange Layer:** विविध एक्स्चेंजकडून डेटा गोळा करणे आणि त्यावर प्रक्रिया करणे.
* **User Layer:** वापरकर्त्यांच्या फोन किंवा कॉम्प्युटरशी संवाद साधणे.
* **Routing Layer:** एक्स्चेंज लेयर आणि युजर लेयर यांच्यातील दुवा म्हणून काम करणे.

**३. किमतीची गणना (Calculating NBBO): [[07:05](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=425)]**

* एक्स्चेंज थेट किंमत देत नाहीत, तर ते 'ऑर्डर बुक' (बिड आणि आस्क किमती) देतात.
* **NBBO (National Best Bid and Offer):** सर्व एक्स्चेंजमधील सर्वोत्तम खरेदी (Bid) आणि विक्री (Offer) किंमत शोधून त्यांची सरासरी काढून वापरकर्त्याला एकच किंमत दाखवली जाते. [[08:15](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=495)]
* यासाठी जॉर्डनने **Doubly Linked List** आणि **Hash Map** वापरून  वेळेत जुना डेटा काढणे आणि  मध्ये नवीन डेटा अपडेट करण्याचा अल्गोरिदम सुचवला आहे. [[12:35](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=755)]

**४. युजर लेयर आणि कनेक्टिव्हिटी (User Layer & WebSockets): [[15:51](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=951)]**

* वापरकर्त्याच्या फोनवर बॅटरी आणि डेटाचा कमीत कमी वापर व्हावा म्हणून **WebSockets** चा वापर केला जातो. [[17:34](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1054)]
* वेबसोकेट्स द्वि-मार्गी (Two-directional) संवाद साधतात, ज्यामुळे किमतीतील बदल त्वरित फोनवर दिसतात.
* **Load Balancing:** वापरकर्त्यांचा ताण विभागण्यासाठी 'Round Robin' पद्धतीचा वापर केला आहे. [[20:15](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1215)]

**५. राउटिंग आणि कम्युनिकेशन लेयर (Routing Layer): [[25:53](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1553)]**

* एक्स्चेंजकडून येणारा प्रचंड डेटा थेट युजर लेयरला न पाठवता **Redis Cache** चा वापर करून राउटिंग लेयरमध्ये साठवला जातो. [[26:46](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1606)]
* रेडिस हा इन-मेमरी डेटाबेस असल्याने तो अत्यंत वेगवान (Low Latency) असतो.

**६. दोष सहनशीलता (Fault Tolerance): [[27:48](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1668)]**

* जर एखादा पब्लिशर सर्व्हर डाऊन झाला, तर **State Machine Replication** वापरून बॅकअप सर्व्हर त्वरित काम हाती घेतो. [[29:10](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=1750)]
* **Zookeeper:** संपूर्ण सिस्टीममधील सर्व्हर्सच्या स्थितीवर लक्ष ठेवण्यासाठी (Coordination Service) याचा वापर केला जातो. [[36:47](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=2207)]

**७. ऑर्डर्स आणि पोझिशन्स (Orders & Positions Service): [[37:18](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=2238)]**

* ऑर्डर्स आणि ग्राहकांचा डेटा साठवण्यासाठी **MySQL** सारख्या रिलेशनल डेटाबेसचा वापर करणे पुरेसे आहे, कारण येथे 'अचूकता' (Consistency) महत्त्वाची आहे. [[38:29](http://www.youtube.com/watch?v=Zvr-ffhvw0Y&t=2309)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ स्टॉक ट्रेडिंग ॲपमधील तांत्रिक आव्हाने स्पष्ट करतो, विशेषतः हजारो एक्स्चेंजकडून येणारा डेटा मिलिसेकंदात कसा प्रोसेस करावा आणि तो करोडो वापरकर्त्यांपर्यंत सुरक्षितपणे कसा पोहोचवावा. **Sharding**, **Caching (Redis)**, आणि **WebSockets** हे या सिस्टीमचे कणा आहेत.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=Zvr-ffhvw0Y](https://www.youtube.com/watch?v=Zvr-ffhvw0Y)
