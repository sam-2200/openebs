# OpenEBS

[![Releases](https://img.shields.io/github/release/openebs/openebs/all.svg?style=flat-square)](https://github.com/openebs/openebs/releases)
[![Slack channel #openebs](https://img.shields.io/badge/slack-openebs-brightgreen.svg?logo=slack)](https://kubernetes.slack.com/messages/openebs)
[![Twitter](https://img.shields.io/twitter/follow/openebs.svg?style=social&label=Follow)](https://twitter.com/intent/follow?screen_name=openebs)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/openebs/openebs/blob/master/CONTRIBUTING.md)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fopenebs%2Fopenebs.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fopenebs%2Fopenebs?ref=badge_shield)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/1754/badge)](https://bestpractices.coreinfrastructure.org/projects/1754)

https://openebs.io/

**Open** कुबेरनेट्स के लिए ओपन-सोर्स स्टोरेज समाधान का उपयोग करने के लिए सबसे व्यापक रूप से तैनात और आसान है।

**OpenEBS** भंडारण समाधान की श्रेणी का अग्रणी ओपन-सोर्स उदाहरण है जिसे कभी-कभी [कंटेनर अटैच्ड स्टोरेज](https://github.com/cncf/sig-storage/blob/master/CNCF%20Storage%20Landscape%20-%20White%20Paper.pdf) कहा जाता है। OpenEBS को हाइपरकॉन्वर्ड स्टोरेज सॉल्यूशंस के तहत [सी.एन.सी.एफ स्टोरेज लैंडस्केप व्हाइट पेपर](https://github.com/cncf/sig-storage/blob/master/CNCF%20Storage%20Landscape%20-%20White%20Paper.pdf) में एक ओपन-सोर्स उदाहरण के रूप में सूचीबद्ध किया गया है।

अन्य पारंपरिक भंडारण समाधानों की तुलना में OpenEBS को अलग बनाने वाले कुछ प्रमुख पहलू:
- माइक्रो सर्विसेज़ आर्किटेक्चर का उपयोग करके बनाया गया जैसे कि यह ऐप्लिकेशंस परोसता है। ओपनईबीएस खुद कुबेरनेट्स कार्यकर्ता नोड्स पर कंटेनरों के एक सेट के रूप में तैनात है। Kubernetes का उपयोग खुद को ऑर्केस्ट्रेट करने और OpenEBS घटकों को प्रबंधित करने के लिए करता है
- पूरी तरह से किसी भी ओएस / प्लेटफॉर्म पर चलाने के लिए अत्यधिक पोर्टेबल बनाने वाले यूजरस्पेस में निर्मित
- पूरी तरह से इरादों से प्रेरित, उन्हीं सिद्धांतों को विरासत में मिला है जो कुबेरनेट्स के साथ उपयोग की आसानी को चलाते हैं
- OpenEBS स्टोरेज इंजन की एक श्रृंखला का समर्थन करता है ताकि डेवलपर्स अपने एप्लिकेशन डिज़ाइन उद्देश्यों के लिए भंडारण तकनीक को उपयुक्त रूप से तैनात कर सकें। कैसेंड्रा जैसे वितरित अनुप्रयोगों में सबसे कम विलंबता के लिए लोकलपीवी इंजन का उपयोग किया जा सकता है। MySQL और PostgreSQL जैसे मोनोलिथिक अनुप्रयोगों को लचीलापन के लिए ZFS इंजन (cStor) का उपयोग कर सकते हैं। कफ़्का जैसे स्ट्रीमिंग एप्लिकेशन किनारे के वातावरण में सर्वश्रेष्ठ प्रदर्शन के लिए NVMe इंजन [Mayastor](https://github.com/openebs/Mayastor) का उपयोग कर सकते हैं। पूरे इंजन प्रकार, ओपनईबीएस उच्च उपलब्धता, स्नैपशॉट, क्लोन और प्रबंधन क्षमता के लिए एक सुसंगत ढांचा प्रदान करता है।

OpenEBS स्वयं अपने मेजबान पर केवल एक अन्य कंटेनर के रूप में तैनात किया जाता है और भंडारण सेवाओं को सक्षम करता है, जिन्हें प्रति पॉड, एप्लिकेशन, क्लस्टर या कंटेनर स्तर पर निर्दिष्ट किया जा सकता है, जिसमें शामिल हैं:
- कुबेरनेट्स कार्यकर्ता नोड्स से जुड़े भंडारण के प्रबंधन को स्वचालित करें और स्टोरेज को डायनामिक रूप से ओपनईबीएस पीवी या स्थानीय पीवी के प्रावधान के लिए उपयोग करने की अनुमति दें।
- नोड्स के पार डेटा दृढ़ता, नाटकीय रूप से उदाहरण के लिए कैसंड्रा के छल्ले के पुनर्निर्माण में लगने वाले समय को कम करना।
- उपलब्धता क्षेत्रों और क्लाउड प्रदाताओं में डेटा का सिंक्रनाइज़ेशन, उपलब्धता में सुधार और उदाहरण के लिए अटैच / डिटैच समय को कम करना।
- एक आम परत तो यह है कि आप AKS पर चल रहे हैं, या आपकी नंगी धातु, या GKE, या AWS - भंडारण सेवाओं के लिए आपका वायरिंग और डेवलपर का अनुभव उतना ही संभव है।
- S3 और अन्य लक्ष्यों के लिए और से tiering का प्रबंधन।

पूरी तरह से कुबेरनेट्स मूल समाधान होने का एक अतिरिक्त लाभ यह है कि प्रशासक और डेवलपर्स ओपनएबीएस का प्रबंधन और प्रबंधन कर सकते हैं जो कुबेरनेट्स, कुबेटल, हेल्म, प्रोमेथियस, ग्रेफाना, वीव स्कोप, आदि जैसे सभी अद्भुत टूलिंग का उपयोग करते हैं।

**हमारी दृष्टि** सरल है: निरंतर कार्यभार के लिए भंडारण और भंडारण सेवाओं को पूरी तरह से पर्यावरण में एकीकृत किया जाना चाहिए ताकि प्रत्येक टीम और कार्यभार नियंत्रण और कुबेरनेट्स के मूल व्यवहार से लाभ हो।

#### *इसे [अन्य भाषाओं में पढ़ें](translations/TRANSLATIONS.md).।*

[🇩🇪](translations/README.de.md)
[🇷🇺](translations/README.ru.md)
[🇹🇷](translations/README.tr.md)
[🇺🇦](translations/README.ua.md)
[🇨🇳](translations/README.zh.md)
[🇫🇷](translations/README.fr.md)

## स्केलेबिलिटी

OpenEBS एक बड़े पैमाने पर कंटेनरीकृत भंडारण नियंत्रकों को शामिल करने का पैमाना बना सकता है। Kubernetes का उपयोग इन्वेंट्री के लिए etcd जैसे मौलिक टुकड़े प्रदान करने के लिए किया जाता है। OpenEBS अपने कुबेरनेट्स तराजू की सीमा तक।

## स्थापना और आरंभ करना

OpenEBS को कुछ आसान चरणों में स्थापित किया जा सकता है। आप कुबेरनेट्स नोड्स पर ओपन-इस्की स्थापित करके और कुबेटेल का उपयोग करके ओपनिब्स-ऑपरेटर को चलाकर कुबेरनेट्स क्लस्टर की अपनी पसंद पर जा सकते हैं।

**ऑपरेटर का उपयोग करके OpenEBS सेवाएँ प्रारंभ करें**
```bash
# apply this yaml
kubectl apply -f https://openebs.github.io/charts/openebs-operator.yaml
```

**helm का उपयोग करके OpenEBS सेवा प्रारंभ करें**
```bash
helm repo update
helm install --namespace openebs --name openebs stable/openebs
```

आप हमारे [QuickStart Guide](https://docs.openebs.io/docs/overview.html) का भी अनुसरण कर सकते हैं।

OpenEBS को किसी भी Kubernetes क्लस्टर पर तैनात किया जा सकता है - या तो क्लाउड में, ऑन-प्रिमाइसेस या डेवलपर लैपटॉप (minibube)। ध्यान दें कि OpenEBS के रूप में आवश्यक कर्नेल में अंतर्निहित परिवर्तन नहीं हैं, जो कि यूजरस्पेस में संचालित होता है। कृपया हमारे [OpenEBS सेटअप](https://docs.openebs.io/docs/overview.html) प्रलेखन का पालन करें। इसके अलावा, हमारे पास वैग्रैंट वातावरण उपलब्ध है जिसमें एक नमूना कुबेरनेट्स परिनियोजन और सिंथेटिक लोड शामिल है जिसका उपयोग आप ओपनईबीएस के प्रदर्शन को अनुकरण करने के लिए कर सकते हैं। आपको [लिटमस](https://litmuschaos.io) नामक संबंधित प्रोजेक्ट दिलचस्प भी लग सकता है, जो kubernetes पर स्टेटफुल वर्कलोड के लिए अराजकता इंजीनियरिंग के साथ मदद करता है।

## स्थिति

OpenEBS उद्योग में सबसे व्यापक रूप से इस्तेमाल और परीक्षण किए गए कुबेरनेट्स भंडारण अवसंरचनाओं में से एक है। मई 2019 के बाद से एक सीएनसीएफ सैंडबॉक्स परियोजना, ओपनएबीएस, दोनों आधारों और क्लाउड सिस्टमों पर कई बैकएंड (स्थानीय, एनएफ़एफ़, ज़ेफ़मे, एनवीएमई) पर सॉफ्टवेयर-परिभाषित भंडारण क्षमताओं का एक निरंतर सेट प्रदान करने वाली पहली और एकमात्र भंडारण प्रणाली है स्टेटफुल वर्कलोड, [लिटमस प्रोजेक्ट] (https://litmuschaos.io) के लिए अपने स्वयं के कैओस इंजीनियरिंग फ्रेमवर्क को खोलने के लिए पहला स्रोत, जो समुदाय स्वचालित रूप से तत्परता पर निर्भर करता है OpenEBS संस्करणों के मासिक ताल का आकलन करता है। एंटरप्राइज़ ग्राहक 2018 से उत्पादन में OpenEBS का उपयोग कर रहे हैं और परियोजना 2.5M + docker को एक सप्ताह खींचती है।

विभिन्न स्टोरेज इंजनों की स्थिति जो कि ओपन ईबीएस कंटीन्यूअस वॉल्यूम को बिजली प्रदान करती है। स्थितियों के बीच का महत्वपूर्ण अंतर नीचे संक्षेप में प्रस्तुत किया गया है:
- **alpha:** एपीआई बिना किसी नोटिस के बाद के सॉफ़्टवेयर रिलीज़ में असंगत तरीकों में बदल सकता है, केवल अल्पकालिक परीक्षण समूहों में उपयोग करने के लिए अनुशंसित है, बग के बढ़ते जोखिम और दीर्घकालिक समर्थन की कमी के कारण।
- **beta**: समग्र सुविधाओं के लिए समर्थन नहीं छोड़ा जाएगा, हालांकि विवरण बदल सकते हैं। संस्करणों के बीच उन्नयन या माइग्रेट करने के लिए समर्थन प्रदान किया जाएगा, या तो स्वचालन या मैनुअल चरणों के माध्यम से।
- **stable**: विशेषताएँ कई बाद के संस्करणों के लिए जारी किए गए सॉफ़्टवेयर में दिखाई देंगी और अधिकांश संस्करणों में सॉफ़्टवेयर स्वचालन के साथ संस्करणों के उन्नयन के लिए समर्थन प्रदान किया जाएगा।


| Storage Engine | Status | Details |
|---|---|---|
| Jiva | stable | Best suited for running Replicated Block Storage on nodes that make use of ephemeral storage on the Kubernetes worker nodes |
| cStor | beta | A preferred option for running on nodes that have Block Devices. Recommended option if Snapshot and Clones are required |
| Local Volumes | beta | Best suited for Distributed Application that need low latency storage - direct-attached storage from the Kubernetes nodes. |
| Mayastor | alpha | A new storage engine that operates at the efficiency of Local Storage but also offers storage services like Replication. Development is underway to support Snapshots and Clones. |

अधिक जानकारी के लिए, कृपया [OpenEBS प्रलेखन](https://docs.openebs.io/docs/next/quickstart.html) देखें।

## योगदान दे रहा है

OpenEBS किसी भी रूप में आपकी प्रतिक्रिया और योगदान का स्वागत करता है।

- [Join OpenEBS community on Kubernetes Slack](https://kubernetes.slack.com)
   - पहले से ही साइन अप? [#Openebs](https://kubernetes.slack.com/messages/openebs/) पर हमारी चर्चाओं के प्रमुख
- एक मुद्दा उठाना चाहते हैं या सुधार और सुविधाओं के साथ मदद करना चाहते हैं?
   - देखें [खुले मुद्दे](https://github.com/openebs/openebs/issues)
   - देखें [योगदान मार्गदर्शिका](./ CONTRIBUTING.md)
   - हमारी योगदानकर्ता सामुदायिक बैठकों में शामिल होना चाहते हैं, [इसे देखें](./community/README.md).।
- हमारे OpenEBS सीएनसीएफ मेलिंग सूचियों में शामिल हों
   - OpenEBS प्रोजेक्ट अपडेट के लिए, [OpenEBS घोषणाएँ](https://lists.cncf.io/g/cncf-openebs-announcements) की सदस्यता लें
   - अन्य OpenEBS उपयोगकर्ताओं के साथ बातचीत करने के लिए, [OpenEBS उपयोगकर्ता](https://lists.cncf.io/g/cncf-openebs-users) की सदस्यता लें |
   
## मुझे कोड दिखाएं

यह OpenEBS के लिए एक मेटा-रिपॉजिटरी है। कृपया पिन किए गए रिपॉजिटरी के साथ या [OpenEBS Architecture](./contribute/design/README.md) दस्तावेज़ के साथ शुरू करें।

## लाइसेंस

OpenEBS को परियोजना स्तर पर [Apache लाइसेंस 2.0](https://github.com/openebs/openebs/blob/master/LICENSE) लाइसेंस के तहत विकसित किया गया है। परियोजना के कुछ घटक अन्य खुले स्रोत परियोजनाओं से प्राप्त होते हैं और उनके संबंधित लाइसेंस के तहत वितरित किए जाते हैं।

OpenEBS सीएनसीएफ प्रोजेक्ट्स का हिस्सा है।

[![CNCF Sandbox Project](https://raw.githubusercontent.com/cncf/artwork/master/other/cncf-sandbox/horizontal/color/cncf-sandbox-horizontal-color.png)](https://landscape.cncf.io/selected=open-ebs)
   
  ## वाणिज्यिक प्रस्ताव

यह तृतीय-पक्ष कंपनियों और व्यक्तियों की एक सूची है जो OpenEBS से संबंधित उत्पाद या सेवाएं प्रदान करते हैं। OpenEBS एक सीएनसीएफ परियोजना है जो किसी भी कंपनी का समर्थन नहीं करती है। सूची को वर्णमाला क्रम में प्रदान किया गया है।
  
- [Clouds Sky GmbH](https://cloudssky.com/en/)
- [CodeWave](https://codewave.eu/)
- [Gridworkz Cloud Services](https://gridworkz.com/)
- [MayaData](https://mayadata.io/)
