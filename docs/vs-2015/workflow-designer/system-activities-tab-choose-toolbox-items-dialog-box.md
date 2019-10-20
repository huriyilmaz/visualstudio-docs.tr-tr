---
title: System. Activities sekmesi, araç kutusu öğeleri Iletişim kutusunu seçin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655177"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities Sekmesi, Araç Kutusu Öğelerini Seç İletişim Kutusu
**Araç kutusu öğelerini Seç** iletişim kutusunun bu sekmesi, kullanabileceğiniz [!INCLUDE[wf](../includes/wf-md.md)] etkinliklerinin, şablonların ve öğelerin bir listesini görüntüler. Bu listeyi göstermek için **Araçlar** menüsünden **araç kutusu öğelerini Seç** ' i seçin **veya araç kutusuna** sağ tıklayıp **öğeleri seç** ' i seçerek **araç kutusu öğelerini Seç** iletişim kutusunu görüntüleyin ve sonra da **bunu seçin System. Activities** sekmesi. kutudan çıkar, listede System. Activities, System. ServiceModel. Activities ve System. Activities. Core. Presentation derlemelerinden iş akışı etkinlikleri bulunur; Ancak, yalnızca, **araç kutusunda** görüntülenen diğer derlemeler aracılığıyla eklenen ve yalnızca sistem tarafından sağlanmış etkinlikler, varsayılan olarak denetlenir. Son eklenen etkinlikler otomatik olarak denetlenir ve iletişim kutusunda **Tamam** ' a tıkladığınızda **araç** kutusunda görüntülenir. Ayrıca, bu öğeler etkinlik/öğe/şablonun bulunduğu ad alanına karşılık gelen yeni bir kategori altında **araç kutusunda** görüntülenir.

> [!WARNING]
> Herhangi bir iş akışı etkinliği içermeyen bir derleme eklemeye çalışırsanız, derlemenin hiç etkinlik içermediğini açıklayan bir hata iletişim kutusu görüntülenir.

 Bu iletişim kutusu proje agtik olur ve bu nedenle **System. Activities** sekmesi tek başına xaml 'de veya iş akışı olmayan bir proje türünde görünmeye devam eder.

 Filtreleme her sekmede yapılır. Bu, **.net bileşen** sekmesi aracılığıyla iş akışı etkinliklerini eklemenin mümkün olmadığı anlamına gelir. Bunlar, **System. Activities** sekmesinin kendisi tarafından eklenmeleri gerekir.

 **Araç** kutusunda bu iletişim kutusundan görmek istemediğiniz öğelerin işaretini kaldırın veya alternatif olarak, **araç kutusu** 'ndaki bağlam **Sil** menü seçeneğini kullanarak ve bir derlemeye yeniden başvuru yapan öğeyi  **Araç kutusu**.

 Tasarımcı üzerinde sürükleyip bırakarak etkinliğin örneklenmesi, öğeyi içeren derlemeyi otomatik olarak başvurulan derlemeler listesine ekler. Ayrıca, etkinlik bir derleme C 'ye başvuruyorsa, başvurulan derleme listesine C eklemez. Derleme C, GAC içinde veya etkinlik B ile aynı dizinde olmalıdır. Tek başına durumda, derleme GAC 'de veya VS 'nin araştırma yollarında olmalıdır. Etkinliği yalnızca iş akışı Tasarımcısı yüzeyine sürükleyip bırakabilirsiniz.

 **Araç kutusu** ayarları varsayılan olarak Kullanıcı seçenekleri olarak kaydedilir. bu nedenle, bir sonraki sefer, **araç kutusunu**açtığınızda özelleştirilmiş iş akışı etkinlikleri listesini görüntüler. Bunun yan etkisi, **araç kutusu öğelerini Seç** iletişim kutusunda belirli etki alanı öğelerinizi **araç** kutusuna eklediyseniz, yine de bir iş akışı konsol uygulamasında çalışırken bu öğeleri görmeye devam edersiniz. Bunları görmek istemiyorsanız, bağlam menüsünü kullanarak silin veya daha önce belirtildiği gibi **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak bunları kaldırın.

 Bu iletişim kutusundaki sütunlar aşağıdaki bilgileri içerir:

 Ad, şu anda yerel makinenizde kayıtlı olan iş akışı etkinliklerinin adlarını listeler.

 Ad alanı, etkinliğin yapısını tanımlayan .NET Framework sınıf kitaplığı ad alanının hiyerarşisini görüntüler.

 Bütünleştirilmiş kod adı, etkinliği içeren .NET Framework derlemesinin adını ve sürümünü görüntüler.

 Dizin, iş akışı etkinliklerini içeren .NET Framework derlemesinin konumunu görüntüler. Tüm derlemeler için varsayılan konum genel derleme önbelleğidir.

 Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.