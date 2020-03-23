---
title: Tasarım Zamanında Montajları Çözme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632569"
---
# <a name="resolve-assemblies-at-design-time"></a>Tasarım zamanında montajları çözme

**Başvuru Ekle** iletişim kutusunun **.NET** sekmesi aracılığıyla bir derlemeye başvuru eklediğinizde, başvuru bir ara başvuru derlemesine işaret; diğer bir şey, tüm tür ve imza bilgilerini içeren, ancak herhangi bir kod içermemesi gereken bir derlemedir. .NET sekmesi, **.NET** Framework'deki çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler. Ayrıca, üçüncü şahıslar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerinde çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler.

## <a name="multi-targeting"></a>Çok hedefleme

 Visual Studio, .NET Framework'ün birden çok sürümünde çalışan .NET Framework sürümlerini hedeflemenizi sağlar. Yeni bir .NET Framework sürümü yayımlandığında, Framework bir hedefleme paketi kullanılarak yüklenebilir ve visual studio'da otomatik olarak hedef olarak gösterilebilir.

## <a name="how-type-resolution-works"></a>Tür çözünürlüğü nasıl çalışır?

 Çalışma zamanında, CLR GAC, *depo gözü* dizini ve herhangi bir sondalama yollarına bakarak derlemedeki türleri çözer. Bu füzyon yükleyici tarafından işlenir. Ama füzyon yükleyicisi ne aradığını nasıl biliyor? Uygulamanın ne zaman oluşturulduğuna göre tasarım zamanında yapılan bir çözünürlüğe bağlıdır.

 Yapı sırasında derleyici başvuru derlemelerini kullanarak uygulama türlerini çözer. .NET Framework sürümlerinde 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1 sürümlerinde,.NET Framework yüklendiğinde başvuru derlemeleri yüklenir.

 Referans derlemeleri, .NET Framework SDK'nın ilgili sürümüyle birlikte gönderen hedefleme paketi tarafından sağlanır. Çerçeve'nin kendisi yalnızca çalışma zamanı derlemelerini sağlar. Uygulamaları oluşturmak için hem .NET Framework'u hem de ilgili .NET Framework SDK'yı yüklemeniz gerekir.

 Belirli bir .NET Framework hedeflediğinizde, yapı sistemi hedefleme paketindeki başvuru derlemelerini kullanarak tüm türleri çözer. Çalışma zamanında, füzyon yükleyici genellikle GAC bulunan çalışma zamanı derlemeleri, bu aynı türleri çözer.

 Başvuru derlemeleri kullanılamıyorsa, yapı sistemi çalışma zamanı derlemelerini kullanarak derleme türlerini çözer. GAC'deki çalışma zamanı derlemeleri küçük sürüm numaralarıyla ayırt edilmeyince, çözüm yanlış derlemeye yapılsa da mümkündür. Bu durum, örneğin.NET Framework sürüm 3.5'te tanıtılan yeni bir yöntem, sürüm 3.0'ı hedeflenirken başvurulursa olabilir. Yapı başarılı olur ve uygulama yapı makinesinde çalışır, ancak sürüm 3.5 yüklü olmayan bir makineye dağıtıldığında başarısız olur.

 Artık .NET Framework SDK ile birlikte gelen hedefleme paketi, yeniden dağıtım (redist) listesi olarak adlandırılan Framework'ün bu sürümündeki tüm çalışma zamanı derlemelerinin bir listesini içerir ve yapı sisteminin türleri yanlış olana karşı çözmesini imkansız hale getirir. derleme sürümü.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
