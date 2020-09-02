---
title: Olay Görüntüleyici | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4cba043d8300d47ae5ffba1c175a19fcfa2e65ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330334"
---
# <a name="events-viewer"></a>Olay Görüntüleyicisi

Genel olaylar Görüntüleyicisi, modül yükü, iş parçacığı başlatma ve sistem yapılandırması gibi olayların bir listesi aracılığıyla uygulama etkinliğini gösterir. Bu görünüm, uygulamanızın Visual Studio Profiler içinde nasıl çalıştığını daha iyi tanılamanıza yardımcı olur.

## <a name="setup"></a>Kurulum

1. Visual Studio 'da performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **Olay Görüntüleyicisi** onay kutusunu seçin.

   ![Olay Görüntüleyicisi onay kutusu seçili](../profiling/media/eventsviewerselected.png "Olay Görüntüleyicisi onay kutusu seçili")

1. Aracı çalıştırmak için **Başlat** düğmesini seçin.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profile olan senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

   ![Durdur toplamayı gösteren pencere](../profiling/media/stopcollectioneventsviewer.png "Durdur toplamayı gösteren pencere")

Aracı nasıl daha verimli hale getirmek hakkında daha fazla bilgi için bkz. [profil oluşturma ayarlarını En Iyi duruma getirme](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Verilerinizi anlayın

![Olay Görüntüleyicisi izleme](../profiling/media/eventviewertrace.png "Olay Görüntüleyicisi izleme")

|Sütun adı|Description|
|----------|---------------------|
|Sağlayıcı Adı|Olay kaynağı|
|Olay Adı|Sağlayıcı tarafından belirtilen olay|
|Metin|Etkinliğin açıklaması, olay adı ve olay KIMLIĞI|
|Zaman damgası (MS)|Olay gerçekleştiği zaman|
|Sağlayıcı GUID 'Si|Olay sağlayıcısının KIMLIĞI|
|Olay Kimliği|Etkinliğin KIMLIĞI|
|İşlem Kimliği|Olayın gerçekleştiği işlem (biliniyorsa)|
|İşlem adı|İşlemin etkin bir şekilde çalıştığı bir adı|
|İş parçacığı KIMLIĞI|Olayın gerçekleştiği iş parçacığının KIMLIĞI (biliniyorsa)|

Herhangi bir sütun varsayılan olarak eksikse, mevcut sütun başlıklarındaki birine sağ tıklayın ve eklemek istediğiniz sütunu seçin.

![Olay Görüntüleyicisine sütun ekleme](../profiling/media/eventvieweraddcolumns.png "Olay Görüntüleyicisine sütun ekleme")

Bir olay seçtiğinizde, **ek özellikler** penceresi görüntülenir. **Ortak özellikler** , herhangi bir olay için görünecek özelliklerin listesini gösterir. **Yük özellikleri** , olaya özgü özellikleri gösterir. Bazı olaylar için **yığınları**da görüntüleyebilirsiniz.

![Yığınları gösteren Olay Görüntüleyicisi](../profiling/media/eventviewerstacks.png "Yığınları gösteren Olay Görüntüleyicisi")

## <a name="organize-your-data"></a>Verilerinizi düzenleme

**Metin** sütunu dışındaki tüm sütunlar sıralanabilir.

![Olay Görüntüleyicisi izleme](../profiling/media/eventviewertrace.png "Olay Görüntüleyicisi izleme")

Olay Görüntüleyicisi, her seferinde en fazla 20.000 olay görüntüler. İlgilendiğiniz olaylara odaklanmak için olay filtresini seçerek olayların görüntülenmesini filtreleyebilirsiniz. Ayrıca, her bir sağlayıcı için gerçekleşen toplam olay sayısının yüzdesini görebilirsiniz. Gösteren bir araç ipucunu görmek için tek bir olay filtresinin üzerine gelin:

- Olay adı
- Sağlayıcı
- GUID
- Toplam olay yüzdesi
- Olay sayısı

![Olay Görüntüleyicisi olay filtresi](../profiling/media/eventviewereventfilter.png "Olay Görüntüleyicisi olay filtresi")

Sağlayıcı filtresi, her bir sağlayıcı için gerçekleşen toplam olay sayısı yüzdesini gösterir. Sağlayıcı adı, toplam olay yüzdesi ve olay sayısı ile benzer bir araç ipucunu görmek için tek bir sağlayıcının üzerine gelin.

![Olay Görüntüleyicisi sağlayıcısı filtresi](../profiling/media/eventviewerproviderfilter.png "Olay Görüntüleyicisi sağlayıcısı filtresi")
