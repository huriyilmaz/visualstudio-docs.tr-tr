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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302954"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017’de tasarıma yönelik yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

İstenmeyen bağımlılıkları ortadan kaldırmak, teknik borcunuzu yönetmenin önemli bir parçasıdır. Visual Studio, bulundukları yer gibi sorunlar hakkında kesin bilgiler de dahil olmak üzere bağımlılıkların canlı doğrulanmasını sağlar. Canlı bağımlılık doğrulama, Hata Listesi'ndeki ve düzenleyicideki yeni özelliklerin tüm avantajlarını alır.

![Eylemde canlı bağımlılık doğrulaması](media/dep-validation-whatsnew-01.png)

Yazma deneyimi bağımlılık doğrulamayı daha erişilebilir ve daha erişilebilir hale getirmek için değişti. Terminoloji "Katman diyagramı"ndan "Bağımlılık diyagramı"na değiştirildi.

**Mimari** menüsü artık doğrudan Bağımlılık diyagramı oluşturmak için bir komut içerir:

![Mimari menüsünde canlı bağımlılık öğesi](media/dep-validation-whatsnew-02.png)

Katman özellik adları ve açıklamaları daha anlamlı hale getirmek için değiştirildi:

![Canlı bağımlılık güncelleştirilmiş özellik adları](media/dep-validation-whatsnew-03.png)

Diyagramı her kaydedişinizde çözümdeki geçerli kodun analiz sonuçlarındaki değişikliklerinizin etkisini hemen görürsünüz. **Bağımlılıkları Doğrula** komutunun tamamlanmasını beklemeniz gerekmez.

Daha fazla bilgi için [bu blog gönderisi](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)bakın.

## <a name="uml-designers-have-been-removed"></a>UML tasarımcıları kaldırıldı

UML tasarımcıları Visual Studio kaldırıldı.

* UML diyagramları artık XML dosyaları olarak sunulmuştur
* UML Model Explorer artık yok
* Modelleme proje başvuruları artık bağımlılık doğrulama için kullanılmaz
* Çözüm Gezgini'ndeki "Katman Başvuruları" düğümü artık görüntülenmiyor
* Bağımlılık (Katman) diyagramındaki "Doğrula" yapı eylemi artık kullanılmaz - Yapı görevi kaldırıldı
* Proje yapısı, sürümler arasında yuvarlak tripping için korunur
* Bağımlılık (Katman) diyagramını XML olarak açmaya, oluşturabilirsiniz, edebilirsiniz ve kaydedebilirsiniz
* Bağımlılık (Katman) diyagramına bağlı TFS iş öğelerine tasarım yüzeyinde erişilemez
* DSL veya Layer'a geri bağlantı artık desteklenmiş
* Modelleme SDK UML genişletilebilirlik artık desteklenir

.NET ve C++ kodunun mimarisini görselleştirme [desteğikod haritaları](map-dependencies-across-your-solutions.md)aracılığıyla kullanılabilir.

UML tasarımcılarının önemli bir kullanıcısıysanız, UML ihtiyaçlarınız için alternatif bir araç üzerinde karar verirken Visual Studio 2015 veya önceki sürümlerini kullanmaya devam edebilirsiniz.

Daha fazla bilgi için [bu blog gönderisi](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)bakın.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve modelleme araçları için sürüm desteği

Visual Studio çeşitli sürümleri mevcuttur. Bunların hepsi mimari ve modelleme araçları için destek sağlamaz. Aşağıdaki tablo, her aracın kullanılabilirliğini gösterir.

|**Özellik**|**Kurumsal sürüm**|**Profesyonel baskı**|**Topluluk sürümü**|
|-|-|-|-|
|**Kod haritaları**|Evet|Yalnızca kod eşlemlerini okumayı, kod eşlemlerini filtrelemeyi, yeni genel düğümler eklemeyi ve seçimden yeni bir Yönlendirilmiş Grafik oluşturmayı destekler.|-|
|**Bağımlılık diyagramları**|Evet|Yalnızca okuma bağımlılık diyagramlarını destekler.|Yalnızca okuma bağımlılık diyagramlarını destekler.|
|**Yönlendirilmiş grafikler** (DGML diyagramları)|Evet|Evet|Evet|
|**Kod klon**|Evet|-|-|
