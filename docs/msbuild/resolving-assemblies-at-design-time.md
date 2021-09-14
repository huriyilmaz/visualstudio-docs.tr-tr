---
title: Tasarım Zamanında Derlemeleri Çözümleme | Microsoft Docs
description: Hedef MSBuild başvuru derlemelerini kullanarak tasarım zamanında derlemelere yapılan başvuruları nasıl çözümley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7033a842c9de61feb392cf145576cb27dacdf6fa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625557"
---
# <a name="resolve-assemblies-at-design-time"></a>Derlemeleri tasarım zamanında çözümleme

Başvuru Ekle iletişim kutusunun **.NET** sekmesi aracılığıyla  bir derlemeye başvuru eklerken, başvuru bir ara başvuru derlemeye işaret ediyor; yani, tüm tür ve imza bilgilerini içeren ancak herhangi bir kod içermesi gerek olmayan bir derlemedir. **.NET sekmesi,** uygulamanın çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini .NET Framework. Ayrıca, üçüncü taraflar tarafından kullanılan kayıtlı AssemblyFoldersEx klasörlerinde çalışma zamanı derlemelerine karşılık gelen başvuru derlemelerini listeler.

## <a name="multi-targeting"></a>Çoklu hedefleme

 Visual Studio, uygulamanın birden çok .NET Framework üzerinde çalıştıran sürüm sürümlerini hedeflemenizi .NET Framework. Yeni bir .NET Framework sürümü yayım olduğunda, Framework bir hedefleme paketi kullanılarak yüklenir ve çerçevede otomatik olarak bir hedef olarak Visual Studio.

## <a name="how-type-resolution-works"></a>Tür çözümlemesi nasıl çalışır?

 Çalışma zamanında CLR GAC'ye, bin dizinine ve herhangi  bir yoklama yoluna bakarak derlemenin türlerini çözümler. Bu, fusion yükleyicisi tarafından idare edildi. Peki Fusion yükleyicisi ne istediğini nasıl biliyor? Uygulamanın ne zaman inşa edildikleri, tasarım zamanında yapılan bir çözüme bağlıdır.

 Derleme sırasında, derleyici başvuru derlemelerini kullanarak uygulama türlerini çözümler. .NET Framework 2.0, 3.0, 3.5, 4, 4.5 ve 4.5.1 sürümlerinde, başvuru derlemeleri .NET Framework yüklenir.

 Başvuru derlemeleri, .NET Framework SDK'sı'nın ilgili sürümüyle birlikte gelen hedefleme paketi tarafından sağlanır. Framework yalnızca çalışma zamanı derlemelerini sağlar. Uygulama derlemek için hem .NET Framework hem de ilgili .NET Framework SDK'sı yüklemeniz gerekir.

 Belirli bir derlemeyi .NET Framework derleme sistemi, hedefleme paketinde başvuru derlemelerini kullanarak tüm türleri çözümler. Çalışma zamanında, fusion yükleyicisi bu türleri genellikle GAC'de bulunan çalışma zamanı derlemelerine çözümler.

 Başvuru derlemeleri kullanılamıyorsa, derleme sistemi derleme türlerini çalışma zamanı derlemelerini kullanarak çözümler. GAC'de çalışma zamanı derlemeleri küçük sürüm numaralarıyla ayırt edici olamaysa da, yanlış derlemeye çözümleme yapmak mümkündür. Örneğin, sürüm 3.0'.NET Framework 3.5'i hedeflerken yeni bir yönteme başvurulsa bu durum ortaya olabilir. Derleme başarılı olur ve uygulama derleme makinesi üzerinde 3.5 sürümünün yüklü olduğu bir makineye dağıtıldığında başarısız olur.

 Artık .NET Framework SDK ile birlikte verilen hedefleme paketi, Çerçeve'nin bu sürümündeki tüm çalışma zamanı derlemelerinin bir listesini içerir ve yeniden dağıtım (redist) listesi olarak adlandırılır ve derleme sisteminin türleri derlemenin yanlış sürümüne göre çözümlemesini imkansız hale gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
