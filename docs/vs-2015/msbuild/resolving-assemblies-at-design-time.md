---
title: Tasarım zamanında derlemeleri çözme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 920e7222b3b425cbb13c962ff8c2e1e2fc551bd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159239"
---
# <a name="resolving-assemblies-at-design-time"></a>Tasarım Zamanında Derlemeleri Çözme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Başvuru Ekle iletişim kutusunun .NET sekmesi aracılığıyla bir derlemeye bir başvuru eklediğinizde, başvuru bir ara başvuru derlemesine işaret eder, diğer bir deyişle, tüm tür ve imza bilgilerini içeren bir derleme, ancak herhangi bir kod içermesi gerekmez. .NET sekmesi .NET Framework çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler. Ayrıca, üçüncü taraflar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerindeki çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler.  
  
## <a name="multi-targeting"></a>Çoklu Sürüm Desteği  
 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , ortak dil çalışma zamanı (CLR) sürüm 2,0 veya sürüm 4 ' te çalıştırılan .NET Framework sürümlerini hedeflemenizi sağlar. Buna 2,0, 3,0, 3,5, 4, 4,5, ve 4.5.1 sürümleri ve Silverlight sürümleri 1,0, 2,0 ve 3,0 dahildir .NET Framework. CLR sürüm 2,0 veya sürüm 4 ' ü temel alan yeni bir .NET Framework sürümü yayınlanmışsa, Framework bir hedefleme paketi kullanılarak yüklenebilir ve Visual Studio 'da otomatik olarak bir hedef olarak görünür.  
  
## <a name="how-type-resolution-works"></a>Tür Çözümlemesi Nasıl Çalışır?  
 Çalışma zamanında, CLR GAC 'ye, bin dizinine ve herhangi bir yoklama yoluna bakarak derlemedeki türleri çözümler. Bu, Fusion yükleyicisi tarafından işlenir. Ancak, Fusion yükleyici ne aradıklarını nasıl bilir? Bu, uygulama yapılandırıldığında tasarım zamanında yapılan bir çözüme bağlıdır.  
  
 Derleme sırasında derleyici, başvuru derlemelerini kullanarak uygulama türlerini çözümler. .NET Framework sürümleri 2,0, 3,0, 3,5, 4, 4,5 ve 4.5.1 sürümlerinde, .NET Framework yüklendiğinde başvuru derlemeleri yüklenir.  
  
 Başvuru derlemeleri, .NET Framework SDK 'nın ilgili sürümüyle birlikte gelen hedefleme paketi tarafından sağlanır. Framework yalnızca çalışma zamanı derlemelerini sağlar. Uygulama derlemek için hem .NET Framework hem de karşılık gelen .NET Framework SDK 'sını yüklemeniz gerekir.  
  
 Belirli bir .NET Framework hedeflediğinizde, yapı sistemi hedefleme paketindeki başvuru derlemelerini kullanarak tüm türleri çözümler. Çalışma zamanında, Fusion yükleyici, genellikle GAC 'de bulunan çalışma zamanı Derlemeleriyle aynı türleri çözümler.  
  
 Başvuru derlemeleri kullanılamıyorsa, derleme sistemi, derleme türlerini çalışma zamanı derlemelerini kullanarak çözer. GAC 'deki çalışma zamanı derlemeleri alt sürüm numaralarına göre ayırt olmadığından, yanlış derlemeye çözümlemenin yapılması mümkündür. Bu durum örneğin, 3,5 sürümü ' de sunulan yeni bir yönteme, sürüm 3,0 .NET Framework ' i hedeflerken başvuruluyorsa meydana gelebilir. Yapı başarılı olur ve uygulama derleme makinesinde çalışır, ancak sürüm 3,5 yüklü olmayan bir makineye dağıtıldığında başarısız olur.  
  
 Artık .NET Framework SDK ile birlikte sunulan hedefleme paketi, bu Framework sürümündeki, yeniden dağıtım (Redist) listesi olarak adlandırılan tüm çalışma zamanı derlemelerinin listesini içerir. Bu, derleme sisteminin, bütünleştirilmiş kodun yanlış sürümüne karşı türleri çözümlemesine olanaksız hale getirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
