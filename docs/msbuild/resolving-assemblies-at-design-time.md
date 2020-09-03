---
title: Tasarım zamanında derlemeleri çözme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f5ba2627e2d659665fa0bd3fbf706f9cad5573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632569"
---
# <a name="resolve-assemblies-at-design-time"></a>Tasarım zamanında derlemeleri çözümleyin

Başvuru **Ekle** iletişim kutusunun **.net** sekmesi aracılığıyla bir derlemeye başvuru eklediğinizde, başvuru bir ara başvuru derlemesine işaret eder; diğer bir deyişle, tüm tür ve imza bilgilerini içeren, ancak herhangi bir kod içermesi gerekmeyen bir derlemedir. **.Net** sekmesi .NET Framework çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler. Ayrıca, üçüncü taraflar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerindeki çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler.

## <a name="multi-targeting"></a>Çoklu hedefleme

 Visual Studio, .NET Framework birden çok sürümünde çalışan .NET Framework sürümlerini hedeflemenizi sağlar. Yeni bir .NET Framework sürümü yayınlandığında, Framework bir hedefleme paketi kullanılarak yüklenebilir ve Visual Studio 'da otomatik olarak bir hedef olarak görünür.

## <a name="how-type-resolution-works"></a>Tür çözümlemenin çalışması

 Çalışma zamanında, CLR GAC 'ye, *bin* dizinine ve herhangi bir yoklama yoluna bakarak derlemedeki türleri çözümler. Bu, Fusion yükleyicisi tarafından işlenir. Ancak, Fusion yükleyici ne aradıklarını nasıl bilir? Bu, uygulama yapılandırıldığında tasarım zamanında yapılan bir çözüme bağlıdır.

 Derleme sırasında derleyici, başvuru derlemelerini kullanarak uygulama türlerini çözümler. .NET Framework sürümleri 2,0, 3,0, 3,5, 4, 4,5 ve 4.5.1 sürümlerinde, .NET Framework yüklendiğinde başvuru derlemeleri yüklenir.

 Başvuru derlemeleri, .NET Framework SDK 'nın ilgili sürümüyle birlikte gelen hedefleme paketi tarafından sağlanır. Framework yalnızca çalışma zamanı derlemelerini sağlar. Uygulama derlemek için hem .NET Framework hem de karşılık gelen .NET Framework SDK 'sını yüklemeniz gerekir.

 Belirli bir .NET Framework hedeflediğinizde, yapı sistemi hedefleme paketindeki başvuru derlemelerini kullanarak tüm türleri çözümler. Çalışma zamanında Fusion yükleyici, genellikle GAC 'de bulunan çalışma zamanı Derlemeleriyle aynı türleri çözümler.

 Başvuru derlemeleri kullanılamıyorsa, derleme sistemi, derleme türlerini çalışma zamanı derlemelerini kullanarak çözer. GAC 'deki çalışma zamanı derlemeleri alt sürüm numaralarına göre ayırt olmadığından, yanlış derlemeye çözümlemenin yapılması mümkündür. Bu durum örneğin, 3,5 sürümü ' de sunulan yeni bir yönteme, sürüm 3,0 .NET Framework ' i hedeflerken başvuruluyorsa meydana gelebilir. Yapı başarılı olur ve uygulama derleme makinesinde çalışır, ancak sürüm 3,5 yüklü olmayan bir makineye dağıtıldığında başarısız olur.

 Artık .NET Framework SDK ile birlikte sunulan hedefleme paketi, bu çerçevenin bu sürümündeki çalışma zamanı derlemelerinin tümünün bir listesini içerir. yeniden dağıtım (Redist) listesi denir ve derleme sisteminin derlemeleri yanlış sürüme karşı çözümlemesini olanaksız hale getirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
