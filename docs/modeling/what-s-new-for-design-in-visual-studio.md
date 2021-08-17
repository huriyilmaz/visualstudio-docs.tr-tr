---
title: Visual Studio 2017’de tasarıma yönelik yenilikler
description: Visual Studio 2017 ' de bulunan canlı bağımlılık doğrulaması gibi kod tasarımına yönelik yeni özellikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 5fd93098ce569247774b6af5828b7696201b8835
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055282"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017’de tasarıma yönelik yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

İstenmeyen bağımlılıkların kaldırılması, teknik borcunu yönetmenin önemli bir parçasıdır. Visual Studio, sorunlar hakkında kesin bilgiler de dahil olmak üzere bağımlılıkların canlı olarak doğrulanmasını sağlar (örneğin nerede bulunur). Canlı bağımlılık doğrulaması, Hata Listesi ve düzenleyicideki yeni özelliklerin tam avantajlarından yararlanır.

![Canlı bağımlılık doğrulaması eylemde](media/dep-validation-whatsnew-01.png)

Yazma deneyimi, bağımlılık doğrulamasını daha keşfedilebilir ve daha erişilebilir hale getirmek üzere değiştirilmiştir. Terminoloji "katman diyagramı" iken "bağımlılık diyagramı" olarak değiştirildi.

**Mimari** menüsünde artık doğrudan bir bağımlılık diyagramı oluşturmak için bir komut bulunur:

![Mimari menüsünde canlı bağımlılık öğesi](media/dep-validation-whatsnew-02.png)

Katman özelliği adları ve açıklamaları daha anlamlı hale getirmek için değiştirilmiştir:

![Canlı bağımlılık güncelleştirilmiş özellik adları](media/dep-validation-whatsnew-03.png)

Her diyagramı her kaydedişinizde çözümdeki geçerli kod için analiz sonuçlarında yaptığınız değişikliklerin etkisini hemen görürsünüz. **Bağımlılıkları doğrula** komutunun tamamlanmasını beklemeniz gerekmez.

Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)bakın.

## <a name="uml-designers-have-been-removed"></a>UML tasarımcıları kaldırıldı

UML tasarımcıları Visual Studio kaldırılmıştır.

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

uml tasarımcılarının önemli bir kullanıcısı ise, uml gereksinimleriniz için alternatif bir araç üzerinde karar verirken Visual Studio 2015 veya önceki sürümlerini kullanmaya devam edebilirsiniz.

Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)bakın.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve modelleme araçları için sürüm desteği

Visual Studio çeşitli sürümlerde kullanılabilir. Bunların hepsi mimari ve modelleme araçları için destek sağlamaz. Aşağıdaki tabloda her aracın kullanılabilirliği gösterilmektedir.

|**Özellik**|**Enterprise sürümü**|**Professional sürümü**|**Community sürümü**|
|-|-|-|-|
|**Kod eşlemeleri**|Yes|yalnızca kod eşlemelerini okumayı, kod eşlemelerini filtrelemeyi, yeni genel düğümleri eklemeyi ve bir seçimden yeni bir yönlendirilmiş Graph oluşturmayı destekler.|-|
|**Bağımlılık diyagramları**|Yes|Yalnızca bağımlılık diyagramlarını okumayı destekler.|Yalnızca bağımlılık diyagramlarını okumayı destekler.|
|**Yönlendirilmiş grafikler** (DGML diyagramları)|Yes|Yes|Yes|
|**Kod kopyası**|Yes|-|-|
