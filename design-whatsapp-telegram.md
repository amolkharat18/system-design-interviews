येथे "System Design Mock Interview: Design WhatsApp or Telegram" या व्हिडिओचा तपशीलवार अहवाल आणि महत्त्वाचे मुद्दे (Key Takeaways) मराठीत दिले आहेत:

### **व्हिडिओ तपशील (Video Details):**

* **विषय:** टेलिग्राम (Telegram) किंवा व्हॉट्सॲप (WhatsApp) सारख्या मेसेजिंग ॲप्लिकेशनची सिस्टीम डिझाइन.
* **तज्ञ:** मार्क (माजी Google इंजिनिअरिंग मॅनेजर).
* **प्रमुख उद्दिष्ट:** मोठ्या प्रमाणावरील (High Scale) मेसेजिंग सिस्टीम कशी तयार करावी याचे तांत्रिक प्रात्यक्षिक.

---

### **महत्त्वाचे मुद्दे (Key Takeaways):**

**१. वापराच्या गरजा निश्चित करणे (Functional Requirements): [[02:10](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=130)]**

* मुलाखतीत मार्कने सुरुवातीलाच व्याप्ती मर्यादित केली. त्यांनी प्रामुख्याने **'वन-टू-वन' (1:1) मेसेज पाठवणे** आणि **मेसेज वाचणे** यावर लक्ष केंद्रित केले, तर ग्रुप चॅटला बाजूला ठेवले.

**२. स्केल आणि क्षमता नियोजन (Scale & Capacity Planning): [[04:40](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=280)]**

* दररोज **१० अब्ज मेसेज** हाताळण्याचे उद्दिष्ट ठेवण्यात आले. [[05:30](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=330)]
* गणिती आकडेमोड करून असे ठरवण्यात आले की, सिस्टीमला दर सेकंदाला साधारण **५ लाख (Peak) रिक्वेस्ट** हाताळाव्या लागतील. [[06:12](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=372)]
* डेटाच्या बाबतीत, दररोज साधारण **१ टेराबाइट (TB)** डेटा तयार होईल, जो ३ वर्षांत पेटाबाइटपर्यंत (PB) जाऊ शकतो. [[08:14](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=494)]

**३. डेटाबेस निवड (Database Selection): [[21:40](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1300)]**

* मार्कने **NoSQL** डेटाबेसचा (उदा. Amazon DynamoDB) वापर सुचवला. [[23:14](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1394)]
* **कारण:** NoSQL डेटाबेस प्रचंड डेटासाठी (Horizontal Scaling) उत्तम असतो आणि मेसेजिंगसाठी आवश्यक असलेली 'इव्हेंच्युअल कन्सिस्टन्सी' (Eventual Consistency) येथे पुरेशी असते. [[24:12](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1452)]

**४. हाय-लेव्हल आर्किटेक्चर (High-Level Design): [[18:04](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1084)]**

* **Load Balancer:** ट्रॅफिक सर्व्हरमध्ये समान विभागण्यासाठी. [[18:37](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1117)]
* **API Servers:** मेसेज प्रोसेसिंगसाठी साधारण ५० ते १०० सर्व्हरची गरज भासेल. [[19:43](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1183)]
* **Consistent Hashing:** डेटा वेगवेगळ्या सर्व्हरवर विभागण्यासाठी (Partitioning) या तंत्राचा उल्लेख केला. [[27:18](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=1638)]

**५. मेसेज डिलिव्हरी प्रक्रिया (Message Delivery Flow): [[39:37](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=2377)]**

* जेव्हा एखादा युजर ऑफलाइन असतो, तेव्हा मेसेज कसा पोहोचवायचा? यासाठी **'Message Distributor'** नावाचा घटक सुचवला. [[40:15](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=2415)]
* हा घटक डेटाबेसमध्ये 'Undelivered' स्टेटस असलेले मेसेज शोधतो आणि युजर ऑनलाइन येताच त्याला ते मेसेज 'Unread' यादीत पाठवतो. [[42:50](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=2570)]

**६. अडथळे आणि निराकरण (Bottlenecks & Solutions): [[44:20](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=2660)]**

* जसा मेसेजचा डेटा वाढत जाईल, तसा संपूर्ण डेटाबेस स्कॅन करणे कठीण होईल.
* **उपाय:** 'Delivered' आणि 'Undelivered' मेसेजेससाठी वेगळे टेबल वापरणे किंवा डेटाबेस फिल्टरिंग सुधारणे. [[45:10](http://www.youtube.com/watch?v=M6UZ7pVD-rQ&t=2710)]

---

### **निष्कर्ष (Summary):**

हा व्हिडिओ सिस्टीम डिझाइन मुलाखतीमध्ये तांत्रिक निर्णयांचे समर्थन कसे करावे (उदा. NoSQL का निवडावा), स्केलची गणना कशी करावी आणि संभाव्य तांत्रिक अडचणी (Bottlenecks) कशा ओळखाव्या याचे उत्तम मार्गदर्शन करतो.

**व्हिडिओ लिंक:** [https://www.youtube.com/watch?v=M6UZ7pVD-rQ](https://www.youtube.com/watch?v=M6UZ7pVD-rQ)
