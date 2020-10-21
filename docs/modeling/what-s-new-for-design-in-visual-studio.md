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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "92299516"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017’de tasarıma yönelik yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

İstenmeyen bağımlılıkların kaldırılması, teknik borcunu yönetmenin önemli bir parçasıdır. Visual Studio, sorunlar hakkında kesin bilgiler de dahil olmak üzere bağımlılıklar için canlı doğrulama sağlar, örneğin nerede bulunur. Canlı bağımlılık doğrulaması, Hata Listesi ve düzenleyicideki yeni özelliklerin tam avantajlarından yararlanır.

![Canlı bağımlılık doğrulaması eylemde](media/dep-validation-whatsnew-01.png)

Yazma deneyimi, bağımlılık doğrulamasını daha keşfedilebilir ve daha erişilebilir hale getirmek üzere değiştirilmiştir. Terminoloji "katman diyagramı" iken "bağımlılık diyagramı" olarak değiştirildi.

**Mimari** menüsünde artık doğrudan bir bağımlılık diyagramı oluşturmak için bir komut bulunur:

![Mimari menüsünde canlı bağımlılık öğesi](media/dep-validation-whatsnew-02.png)

Katman özelliği adları ve açıklamaları daha anlamlı hale getirmek için değiştirilmiştir:

![Canlı bağımlılık güncelleştirilmiş özellik adları](media/dep-validation-whatsnew-03.png)

Her diyagramı her kaydedişinizde çözümdeki geçerli kod için analiz sonuçlarında yaptığınız değişikliklerin etkisini hemen görürsünüz. **Bağımlılıkları doğrula** komutunun tamamlanmasını beklemeniz gerekmez.

Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)bakın.

## <a name="uml-designers-have-been-removed"></a>UML tasarımcıları kaldırıldı

UML tasarımcıları Visual Studio 'dan kaldırılmıştır.

* UML diyagramları artık XML dosyaları olarak sunulmuştur
* UML Model Gezgini artık yok
* Bağımlılık doğrulaması için modelleme projesi başvuruları artık kullanılmıyor
* Çözüm Gezgini ' deki "Katman başvuruları" düğümü artık görüntülenmiyor
* Bağımlılık (katman) diyagramında "doğrulama" derleme eylemi artık kullanılmıyor; derleme görevi kaldırılmış
* Proje yapısı, sürümler arasında gidiş dönüşü için korunur
* Bağımlılık (katman) diyagramını XML olarak açmaya, oluşturmaya, düzenlemeye ve kaydetmeye devam edebilirsiniz
* Bir bağımlılık (katman) diyagramına bağlı TFS iş öğelerine tasarım yüzeyinde erişilemiyor
* ' Den DSL 'ye veya katmana geri bağlama artık desteklenmiyor
* Modelleme SDK 'sında UML genişletilebilirliği artık desteklenmiyor

.NET ve C++ kodu mimarisini görselleştirmeye yönelik destek [kod haritaları](map-dependencies-across-your-solutions.md)aracılığıyla kullanılabilir.

UML tasarımcılarının önemli bir kullanıcısı ise, UML gereksinimleriniz için alternatif bir araç üzerinde karar verirken Visual Studio 2015 veya önceki sürümlerini kullanmaya devam edebilirsiniz.

Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)bakın.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve modelleme araçları için sürüm desteği

Visual Studio çeşitli sürümlerde kullanılabilir. Bunların hepsi mimari ve modelleme araçları için destek sağlamaz. Aşağıdaki tabloda her aracın kullanılabilirliği gösterilmektedir.

|**Özellik**|**Kurumsal sürüm**|**Professional sürümü**|**Topluluk sürümü**|
|-|-|-|-|
|**Kod eşlemeleri**|Evet|Yalnızca kod eşlemelerini okumayı, kod eşlemelerini filtrelemeyi, yeni genel düğümleri eklemeyi ve bir seçimden yeni bir yönlendirilmiş grafik oluşturmayı destekler.|-|
|**Bağımlılık diyagramları**|Evet|Yalnızca bağımlılık diyagramlarını okumayı destekler.|Yalnızca bağımlılık diyagramlarını okumayı destekler.|
|**Yönlendirilmiş grafikler** (DGML diyagramları)|Evet|Evet|Evet|
|**Kod kopyası**|Evet|-|-|
