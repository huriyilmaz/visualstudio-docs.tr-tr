---
title: Visual Studio 2017’de tasarıma yönelik yenilikler
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593518"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017’de tasarıma yönelik yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulama

İstenmeyen bağımlılık kaldırma, teknik borcun yönetimi, önemli bir parçasıdır. Visual Studio, sorunlar hakkında kesin bilgiler de dahil olmak üzere bağımlılıklar için canlı doğrulama sağlar, örneğin nerede bulunur. Canlı bağımlılık doğrulaması, Hata Listesi ve düzenleyicideki yeni özelliklerin tam avantajlarından yararlanır.

![Eylem Canlı bağımlılık doğrulama](media/dep-validation-whatsnew-01.png)

Yazma deneyimi, bağımlılık doğrulamasını daha keşfedilebilir ve daha erişilebilir hale getirmek üzere değiştirilmiştir. Terminoloji "katman diyagramı" iken "bağımlılık diyagramı" olarak değiştirildi.

**Mimarisi** menüsü artık, doğrudan bir bağımlılık diyagramı oluşturmak için bir komut içerir:

![Canlı bağımlılık öğede mimari menüsü](media/dep-validation-whatsnew-02.png)

Katman özelliği adları ve açıklamaları daha anlamlı hale getirmek için değiştirilmiştir:

![Canlı bağımlılık özelliği adları güncelleştirildi](media/dep-validation-whatsnew-03.png)

Her diyagramı her kaydedişinizde çözümdeki geçerli kod için analiz sonuçlarında yaptığınız değişikliklerin etkisini hemen görürsünüz. **Bağımlılıkları doğrula** komutunun tamamlanmasını beklemeniz gerekmez.

Daha fazla ayrıntı için [bu blog gönderisini](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML tasarımcılarına kaldırıldı

UML tasarımcıları Visual Studio 'dan kaldırılmıştır.

* UML diyagramları artık XML dosyaları olarak sunulur
* UML Model Gezgini artık yok
* Modelleme projesi başvuruları artık bağımlılık doğrulaması için kullanılır
* Çözüm Gezgini "Katman başvuruları" düğümünde artık görüntülenmez
* Bağımlılık (katman) diyagram üzerinde "Doğrula" derleme eylemi artık kullanılmamaktadır - derleme görevi kaldırıldı
* Proje yapısını sürümleri arasında gidiş dönüşü korunur
* Yine de açın, oluşturabilir, düzenleyebilir ve bir bağımlılık (katman) diyagramı XML olarak kaydetme
* TFS iş öğeleri için bir bağımlılık (katman) diyagramı tasarım yüzeyinde erişilebilir değil
* Geri gelen DSL veya katmanına bağlama artık desteklenmiyor
* UML Genişletilebilirlik modelleme SDK'sı, artık desteklenmiyor

.NET ve C++ kod mimarisini görselleştirmeye yönelik destek [kod haritaları](map-dependencies-across-your-solutions.md)aracılığıyla kullanılabilir.

UML tasarımcılarına önemli bir kullanıcı varsa, UML ihtiyaçlarınız için alternatif bir aracı üzerinde karar sırada Visual Studio 2015 veya önceki sürümlerini kullanmaya devam edebilirsiniz.

Daha fazla ayrıntı için [bu blog gönderisini](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve Modelleme Araçları sürüm desteği

Visual Studio çeşitli sürümlerde kullanılabilir. Bunların tümü, mimari ve Modelleme Araçları için destek sağlar. Aşağıdaki tabloda her bir aracı kullanılabilirliğini gösterir.

|**Özelliği**|**Enterprise edition**|**Professional sürümü**|**Community sürümü**|
|-|-|-|-|
|**Kod haritaları**|Evet|Yalnızca okuma kod haritalarını destekler, kod filtreleme, yeni genel düğüm ekleme ve seçimden yeni yönlendirilmiş grafik oluşturma eşler.|-|
|**Bağımlılık diyagramları**|Evet|Yalnızca bağımlılık diyagramlarını okuma destekler.|Yalnızca bağımlılık diyagramlarını okuma destekler.|
|**Yönlendirilmiş grafikleri** (DGML diyagramları)|Evet|Evet|Evet|
|**Kod kopyası**|Evet|-|-|
