---
title: System. Activities, araç kutusu öğelerini seçin
description: İş Akışı Tasarımcısı, System. activities sekmesinin bir Windows Workflow Foundation (WF) etkinlikleri, şablonları ve sizin için kullanılabilen öğelerin bir listesini nasıl görüntülediğini öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091987"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System. Activities sekmesi, araç kutusu öğeleri iletişim kutusu seçin

**araç kutusu öğelerini seç** iletişim kutusunun bu sekmesi, kullanabileceğiniz Windows Workflow Foundation (WF) etkinliklerinin, şablonlarının ve öğelerin bir listesini görüntüler. Bu listeyi göstermek için **Araçlar** menüsünden **araç kutusu öğelerini Seç** ' i seçin **veya araç kutusuna** sağ tıklayıp **öğeleri seç** ' i seçerek **araç kutusu öğelerini Seç** iletişim kutusunu görüntüleyin ve ardından **System. Activities** sekmesini seçin. Listenin dışında, listede System. Activities, System. ServiceModel. Activities ve System. Activities. Core. Presentation derlemelerinden iş akışı etkinlikleri bulunur; Ancak, yalnızca, **araç kutusunda** görüntülenen diğer derlemeler aracılığıyla eklenen ve yalnızca sistem tarafından sağlanmış etkinlikler, varsayılan olarak denetlenir. Son eklenen etkinlikler otomatik olarak denetlenir ve iletişim kutusunda **Tamam** ' a tıkladığınızda **araç** kutusunda görüntülenir. Ayrıca, bu öğeler etkinlik/öğe/şablonun bulunduğu ad alanına karşılık gelen yeni bir kategori altında **araç kutusunda** görüntülenir.

> [!WARNING]
> Herhangi bir iş akışı etkinliği içermeyen bir derleme eklemeye çalışırsanız, derlemenin hiç etkinlik içermediğini açıklayan bir hata iletişim kutusu görüntülenir.

Bu iletişim kutusu proje agtik olur ve bu nedenle **System. Activities** sekmesi tek başına xaml 'de veya iş akışı olmayan bir proje türünde görünmeye devam eder.

Filtreleme her sekmede yapılır ve **.net bileşen** sekmesi aracılığıyla iş akışı etkinliklerini eklemek mümkün değildir. Bunları **System. Activities** sekmesi aracılığıyla ekleyin.

**Araç** kutusunda bu iletişim kutusundan görmek istemediğiniz öğelerin işaretini kaldırın veya alternatif olarak, **araç kutusu** 'Ndaki sağ tıklama menüsünü **Sil** seçeneğini kullanarak bir derlemeye yeniden başvurmaz ve **araç kutusundan** öğeyi kaldırmaz.

Tasarımcı üzerinde sürükleyip bırakarak etkinliğin örneklenmesi, öğeyi içeren derlemeyi otomatik olarak başvurulan derlemeler listesine ekler. Ayrıca, etkinlik bir derleme C 'ye başvuruyorsa, başvurulan derleme listesine C eklemez. Derleme C, GAC içinde veya etkinlik B ile aynı dizinde olmalıdır. Tek başına durumda, derleme GAC 'de veya VS 'nin araştırma yollarında olmalıdır. Etkinliği yalnızca iş akışı Tasarımcısı yüzeyine sürükleyip bırakabilirsiniz.

**Araç kutusu** ayarları varsayılan olarak Kullanıcı seçenekleri olarak kaydedilir. bu nedenle, bir sonraki sefer, **araç kutusunu** açtığınızda özelleştirilmiş iş akışı etkinlikleri listesini görüntüler. Bunun yan etkisi, **araç kutusu öğelerini Seç** iletişim kutusunda belirli etki alanı öğelerinizi **araç** kutusuna eklediyseniz, yine de bir iş akışı konsol uygulamasında çalışırken bu öğeleri görmeye devam edersiniz. Bunları görmek istemiyorsanız, sağ tıklama menüsünü kullanarak silin veya daha önce belirtildiği gibi **araç kutusu öğelerini Seç** iletişim kutusunda bunları kaldırın.

Bu iletişim kutusundaki sütunlar aşağıdaki bilgileri içerir:

Ada
Yerel makinenizde kayıtlı olan iş akışı etkinliklerinin adlarını listeler.

Uzayına
Etkinliğin yapısını tanımlayan .NET ad alanı hiyerarşisini görüntüler.

Derleme adı \
Etkinliği içeren .NET derlemesinin adını ve sürümünü görüntüler.

Dizinden
İş akışı etkinliklerini içeren .NET derlemesinin konumunu görüntüler. Tüm derlemeler için varsayılan konum genel derleme önbelleğidir.

Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.
