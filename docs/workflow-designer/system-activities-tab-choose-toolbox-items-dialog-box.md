---
title: System.Activities, Araç Kutusu Öğelerini Seçme
description: Bu İş Akışı Tasarımcısı System.Activities sekmesinde Windows Workflow Foundation (WF) etkinliklerinin, şablonların ve kullanılabilir öğelerin listesini nasıl görüntülemektedir?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 29074e32fb232af7e89581368a6067b9db668da1
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963775"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities sekmesi, Araç Kutusu Öğelerini Seç iletişim kutusu

Araç Kutusu Öğelerini **Seç iletişim** kutusunun bu sekmesi, Windows Workflow Foundation (WF) etkinliklerinin, şablonların ve öğelerin listesini görüntüler. Bu listeyi görüntülemek  için Araçlar menüsünden Araç Kutusu Öğelerini Seç'i seçin  veya Araç Kutusuna  sağ tıklar ve Öğeleri Seç'i seçerek Araç Kutusu Öğelerini Seç iletişim kutusunu görüntüleyin ve **ardından System.Activities** sekmesini seçin.   Listede System.Activities, System.ServiceModel.Activities ve System.Activities.Core.Presentation derlemelerinden iş akışı etkinlikleri yer almaktadır; ancak, yalnızca sistem tarafından sağlanan etkinlikler gösterilir ve Araç Kutusunda görüntülenen diğer derlemeler aracılığıyla **eklenen etkinlikler varsayılan** olarak denetlenir. Kısa süre önce eklenen etkinlikler otomatik olarak işaretlenir ve **iletişim kutusunda** Tamam'a tıklarken Araç Kutusunda görünür.  Ayrıca, bu öğeler **Araç Kutusunda** etkinliğin/öğenin/şablonun bulunduğu ad alanına karşılık gelen yeni bir kategori altında görünür.

> [!WARNING]
> Herhangi bir iş akışı etkinlikleri içeren bir derleme eklemeye çalışsanız, derlemenin herhangi bir etkinlik içere olmadığını açıklayan bir hata iletişim kutusu görüntülenir.

Bu iletişim kutusu projeden bağımsızdır ve bu nedenle **System.Activities** sekmesi tek başına XAML'de veya iş akışı olmayan bir proje türünde göstermeye devam eder.

Filtreleme her sekmede yapılır ve **.NET** Bileşeni sekmesi aracılığıyla iş akışı etkinlikleri eklemek mümkün değildir. Bunları **System.Activities sekmesinin kendisi** aracılığıyla ekleyin.

Araç Kutusunda görmek istemediklerin işaretini bu iletişim kutusu sekmesinden kaldırabilirsiniz veya alternatif olarak,  Araç Kutusu'nda Sağ  tıklamayı sil menü seçeneğini kullanarak bunu yapabilirsiniz ve bir derlemeye başvurulma, öğeyi Araç Kutusundan  kaldırmaz. 

Tasarımcıda sürükleyip bırakarak etkinliğin örneğini oluşturma, öğeyi içeren derlemeyi başvurulan derlemeler listesine otomatik olarak ekler. Ayrıca etkinlik bir C derlemeye başvurursa, başvurulan derleme listesine C eklemez. C derlemesi GAC'de veya B etkinliğiyle aynı dizinde olmalıdır. Tek başına durumda, derlemeNIN GAC'de veya VS'nin Yoklama yollarında olması gerekir. Ancak bundan sonra etkinliği iş akışı tasarımcısının yüzeyine sürükleyip bırakın.

**Araç kutusu** ayarları varsayılan olarak kullanıcı seçenekleri olarak kaydedilir, bu nedenle, **Araç** Kutusunu bir sonraki açsanız, özelleştirilmiş iş akışı etkinlikleri listenizi görüntüler. Bunun bir yan etkisi, Araç Kutusu Öğelerini Seç  iletişim kutusu  aracılığıyla araç kutusuna belirli etki alanı öğelerinizi eklediyebilirsiniz. Bu öğeleri bir İş Akışı Konsolu Uygulamasında çalışırken de görmeye devam edersiniz. Bunları görmek istemiyorsanız, sağ tıklama menüsünü kullanarak silin veya daha önce  belirtildiği gibi Araç Kutusu Öğelerini Seç iletişim kutusundan bu menülerin işaretini kaldırın.

Bu iletişim kutusundaki sütunlar aşağıdaki bilgileri içerir:

Ad\
Yerel makinenize kayıtlı olan iş akışı etkinliklerinin adlarını listeler.

Ad Alanı\
Etkinliğin yapısını tanımlayan .NET ad alanının hiyerarşisini görüntüler.

Derleme Adı\
Etkinliği içeren .NET derlemenin adını ve sürümünü görüntüler.

Dizin\
İş akışı etkinliklerini içeren .NET derlemenin konumunu görüntüler. Tüm derlemeler için varsayılan konum Genel Derleme Önbelleği'dir.

Listelenen bileşenleri sıralamak için herhangi bir sütun başlığı seçin.
