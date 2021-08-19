---
title: Visual Studio karşılaştırılan VBA ve Office çözümleri
description: Visual Studio Microsoft Visual Basic for Applications (VBA) ve Microsoft Office çözümleri arasındaki farklılıklar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c1ba6753c28bae5094e83f28be72632f25b82f7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147667"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Visual Studio karşılaştırılan VBA ve Office çözümleri
  Microsoft Visual Basic for Applications (VBA), Office uygulamalarıyla sıkı bir şekilde tümleştirilmiş yönetilmeyen kod kullanır. Visual Studio kullanılarak oluşturulan Microsoft Office projeler .NET Framework ve Visual Studio tasarım araçlarından yararlanmanızı sağlar.

 Visual Studio kullanarak oluşturabileceğiniz Office çözümlerin türleri hakkında daha fazla bilgi için bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Karşılaştırma
 aşağıdaki tabloda, Visual Studio içindeki VBA çözümleri ve Office çözümleri arasında temel bir karşılaştırma sunulmaktadır.

|VBA çözümleri|Visual Studio çözümleri Office|
|-------------------|---------------------------------------|
|Belirli bir belgeye bağlı ve kalıcı olan kodu kullanır.|belgeden (belge düzeyi özelleştirmeleri için) veya uygulama tarafından yüklenen bir derlemede (VSTO eklentileri için) ayrı olarak depolanan kodu kullanır.|
|Office nesne modelleri ve VBA apı 'leri ile birlikte kullanılır.|hem Office nesne modellerine hem de apı 'lere erişim sağlar [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Makro kaydı ve Basitleştirilmiş geliştirici deneyimi için tasarlanmıştır.|güvenlik, daha kolay kod bakımı ve tam Visual Studio tümleşik geliştirme ortamı (ıde) kullanma özelliği için tasarlanmıştır.|
|Office uygulamalarla sıkı bir tümleştirmeden faydalanabilir çözümler için iyi sonuç verir.|Visual Studio ve ' nin tam kaynaklarından faydalanabilir çözümler için iyi sonuç verir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|, Özellikle güvenlik ve dağıtım alanlarında bulunan, kuruluş için sınırlamalar içerir.|Kuruluşta kullanım için tasarlandı.|

 Daha hızlı bir şekilde VBA kullanarak daha kolay hale getiriyoruz. Özellikle, için VBA 'Yı kullanmaya devam etmek isteyebilirsiniz:

- Özel çalışma sayfası işlevleri.

- Makro kaydı.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Visual Studio kullanılarak oluşturulan VBA çözümlerini ve Office çözümlerini birleştirin
 Visual Studio kullanılarak oluşturulan Office çözümlerinden VBA kodunu çağırabilir ve ayrıca vba 'dan Visual Studio kullanılarak oluşturulan Office çözümlerinde kod çağırabilirsiniz. belirli bir teknik, Office çözümünüzün VSTO bir eklenti veya belge düzeyi özelleştirmesi olmasına bağlı olarak farklılık gösterir. daha fazla bilgi için bkz. [diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) ve [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
