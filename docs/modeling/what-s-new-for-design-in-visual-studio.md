---
title: Visual Studio 2017’de tasarıma yönelik yenilikler
description: 2017'de kullanılabilen canlı bağımlılık doğrulaması gibi kod tasarımına Visual Studio öğrenin.
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
ms.openlocfilehash: fc3c5d1daa0add2832f6e9d0adc032916f72521b360a682ba6e07eb555f30ac5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385691"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017’de tasarıma yönelik yenilikler

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

İstenmeyen bağımlılıkları kaldırmak, teknik borçlarınızı yönetmenin önemli bir parçası. Visual Studio, nerede olduğu gibi sorunlar hakkında kesin bilgiler de dahil olmak üzere bağımlılıkların canlı doğrulamasını sağlar. Canlı bağımlılık doğrulaması, Hata Listesi'nde ve düzenleyicide yer alan yeni özelliklerin tam avantajlarını alır.

![Canlı bağımlılık doğrulama işlemi](media/dep-validation-whatsnew-01.png)

Bağımlılık doğrulamasını daha keşfedilebilir ve daha erişilebilir hale etmek için yazma deneyimi değişmiştir. Terminoloji ,"Katman diyagramı" olan "Bağımlılık diyagramı" olarak değiştirilmiştir.

Mimari **menüsünde** artık doğrudan bağımlılık diyagramı oluşturmak için bir komut vardır:

![Mimari menüsündeki canlı bağımlılık öğesi](media/dep-validation-whatsnew-02.png)

Katman özellik adları ve açıklamaları daha anlamlı olacak şekilde değiştirilmiştir:

![Canlı bağımlılık güncelleştirilmiş özellik adları](media/dep-validation-whatsnew-03.png)

Diyagramı her kaydeden çözümde geçerli kod için analiz sonuçlarında değişikliklerinizin etkisini hemen görüyorsunuz. Bağımlılıkları Doğrula komutunun tamamlanmasını **beklemeye gerek** yok.

Diğer ayrıntılar için bu [blog gönderisi'ne bakın.](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)

## <a name="uml-designers-have-been-removed"></a>UML tasarımcıları kaldırıldı

UML tasarımcıları, Visual Studio.

* UML diyagramları artık XML dosyaları olarak sunulmaktadır
* UML Model Gezgini artık mevcut değil
* Proje başvurularını modelleme artık bağımlılık doğrulaması için kullanılmadı
* Veri kümesinde "Katman Başvuruları" Çözüm Gezgini artık görüntülenmez
* Bağımlılık (Katman) diyagramında "Doğrula" derleme eylemi artık kullanılmadı - Derleme görevi kaldırıldı
* Proje yapısı, sürümler arasında gidiş dönüş için korunur
* Bağımlılık (Katman) diyagramını xml olarak açmaya, oluşturmaya, düzenlemeye ve kaydetmeye devam edersiniz
* Bağımlılık (Katman) diyagramına bağlı TFS iş öğelerine tasarım yüzeyinde erişilemiyor
* DSL'den veya Katmandan geri bağlantı artık desteklenmiyor
* Modelleme SDK'sı'nda UML genişletilebilirliği artık desteklenmiyor

.NET ve C++ kodunun mimarisini görselleştirme desteği, kod eşlemeleri [aracılığıyla kullanılabilir.](map-dependencies-across-your-solutions.md)

UML tasarımcılarının önemli bir kullanıcısıysanız, UML 2015 veya Visual Studio 2015 veya önceki sürümleri kullanmaya devam ederken UML ihtiyaçlarınıza yönelik alternatif bir araç kullanmaya devam edin.

Diğer ayrıntılar için bu [blog gönderisi'ne bakın.](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve modelleme araçları için sürüm desteği

Visual Studio sürümleri mevcuttur. Bunların hepsi mimari ve modelleme araçları için destek sağlamamaktadır. Aşağıdaki tabloda her aracın kullanılabilirliği gösterir.

|**Özellik**|**Enterprise sürümü**|**Professional sürümü**|**Community sürümü**|
|-|-|-|-|
|**Kod eşlemeleri**|Yes|Yalnızca kod eşlemelerini okumayı, kod haritalarını filtrelemeyi, yeni genel düğümler eklemeyi ve seçimden yeni bir Graph oluşturmayı destekler.|-|
|**Bağımlılık diyagramları**|Yes|Yalnızca bağımlılık diyagramlarını okumayı destekler.|Yalnızca bağımlılık diyagramlarını okumayı destekler.|
|**Yönlendiren grafikler** (DGML diyagramları)|Yes|Yes|Yes|
|**Kod kopyalama**|Yes|-|-|
