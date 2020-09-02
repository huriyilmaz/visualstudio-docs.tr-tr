---
title: Örnekleme veri değerlerini anlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145421"
---
# <a name="understanding-sampling-data-values"></a>Örnekleme Veri Değerlerini Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları *örnekleme* profili oluşturma yöntemi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] küme aralıklarında bilgisayar işlemcisini keser ve işlev çağrı yığınını toplar. *Çağrı yığını* , işlemcide yürütülen işlevlerle ilgili bilgileri depolayan dinamik bir yapıdır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Profil Oluşturucu analizi, işlemcinin hedef işlemde kod yürütmediğini belirler. İşlemci hedef işlemde kod yürütülemiyor, örnek atılır.  
  
  İşlemci hedef kodu yürütüp, profil oluşturucu çağrı yığınında her bir işlevin örnek sayılarını arttırır. Örneğin alındığı sırada, çağrı yığınında yalnızca bir işlev şu anda kodu yürütüyor. Yığındaki diğer işlevler, alt öğelerinin dönebilmeleri için bekleyen işlev çağrılarının hiyerarşisinde üstlerdir.  
  
  Örnek olay için, profil oluşturucu Şu anda yönergelerini yürüten işlevin *dışlamalı* örnek sayısını artırır. Dışlamalı bir örnek aynı zamanda işlevin toplam (*kapsamlı*) örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsamlı örnek sayısı da artırılır.  
  
  Profiler, Çağrı yığınındaki diğer tüm işlevlerin dahil edilen örnek sayısını artırır.  
  
## <a name="inclusive-samples"></a>Kapsamlı örnekler  
 Hedef işlevin yürütülmesi sırasında toplanan örneklerin toplam sayısı.  
  
 Bu, işlev kodunun doğrudan yürütülmesi sırasında toplanan örnekleri ve hedef işlev tarafından çağrılan alt işlevlerin yürütülmesi sırasında toplanan örnekleri içerir.  
  
## <a name="exclusive-samples"></a>Dışlamalı örnekler  
 Hedef işlevin yönergelerinin doğrudan yürütülmesi sırasında toplanan örneklerin sayısı.  
  
 Dışlamalı örnekler, hedef işlev tarafından çağrılan işlevlerin yürütülmesi sırasında toplanan örnekleri içermez.  
  
## <a name="inclusive-percent"></a>Kapsamlı yüzde  
 Profil oluşturma çalıştırmasında, işlevin veya veri aralığının kapsamlı örnekleri olan toplam kapsamlı örnek sayısının yüzdesi.  
  
## <a name="exclusive-percent"></a>Dışlamalı yüzde  
 Profil oluşturma çalıştırmasında, işlevin veya veri aralığının özel örnekleri olan toplam dışlamalı örnek sayısının yüzdesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)   
 [Performans Araçları Verilerini Analiz Etme](../profiling/analyzing-performance-tools-data.md)
