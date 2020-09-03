---
title: .NET bellek ayırmaları görünümü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3c24d8aa984ddc947d3c532020974a196192940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179073"
---
# <a name="net-memory-allocations-view"></a>.NET Bellek Ayırma Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayırmalar görünümü profil oluşturma çalışması sırasında oluşturulan türleri listeler. Her tür, tür ayırmaları ile sonuçlanan işlev yürütme yollarını görüntüleyen bir çağrı ağacının kök düğümüdür.  
  
 Bir tür satırındaki veriler, profil oluşturma çalıştırmasında oluşturulan türdeki toplam nesne sayısını ve bu türdeki nesneler için ayrılan toplam bayt sayısını görüntüler. Bir tür için kapsamlı ve dışlamalı değerler her zaman aynıdır.  
  
- Kapsamlı değerler, işlevin örneklerinde oluşturulan nesneler ve çağrı ağacındaki üst işlev tarafından çağrılan alt işlevleri içindir.  
  
- Dışlamalı değerler, ana işlev tarafından çağrıldıklarında doğrudan işlev tarafından oluşturulan nesneler içindir. Alt işlevlerde oluşturulan nesneler dahil değildir.  
  
  Bir işlev verileri oluşturulan nesne sayısını ve üst türün nesneleri için ayrılan bayt sayısını görüntüler.  
  
## <a name="highlighting-the-execution-hot-path"></a>Yürütmenin etkin yolunu vurgulama  
 Üst türün en çok nesnesini oluşturan çağrı ağacının yürütme yolunu bulabilirsiniz.  
  
- En etkin yolu göstermek için tür veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Ayrılan tür veya işlevin adı.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|Türü veya işlevi içeren modülün adı.|  
|**Modül yolu**|Türü veya işlevi içeren modülün yolu.|  
|**Kaynak Dosya**|Tür veya işlev tanımını içeren kaynak dosya.|  
|**İşlev satır numarası**|Bu tür tanımının veya kaynak dosyadaki işlevinin başlangıç satır numarası.|  
|**Düzeyde**|Verilerin bir tür veya işlev için olup olmadığını gösterir.|  
|**Kapsamlı ayırmalar**|-Bir işlev için, işlev tarafından oluşturulan üst tür nesnelerinin toplam sayısı. Bu sayı alt işlevlerde oluşturulan nesneleri içerir.<br />-Bir tür için, oluşturulan bu türdeki örneklerin toplam sayısı.|  
|**Kapsamlı ayırmalar%**|-Bir işlev için, işlev tarafından üst türün dahil tahsisatlarını içeren profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.<br />-Tür için, profil oluşturma çalıştırmasında oluşturulan, türün örnekleri olan toplam nesne sayısı yüzdesi.|  
|**Dışlamalı ayırmalar**|-Bir işlev için, işlev çağrı yığınının en üstünde doğrudan yürütüldüğü zaman oluşturulan nesne sayısı. Bu sayı alt işlevlerde oluşturulan nesneleri içermez.<br />-Bir tür için, oluşturulan bu türdeki örneklerin toplam sayısı.|  
|**Dışlamalı ayırmalar%**|-Bir işlev için, işlev tarafından üst türün özel ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.<br />-Tür için, profil oluşturma çalıştırmasında oluşturulan, türün örnekleri olan toplam nesne sayısı yüzdesi.|  
|**Kapsamlı baytlar**|-Bir işlev için, üst tür nesneler için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleriyle ayrılan belleği içerir.<br />-Bir tür için, tür örnekleri için profil oluşturma çalıştırmasında ayrılan toplam bayt sayısı.|  
|**Dahil edilen baytlar%**|-Bir işlev için, işlev tarafından üst tür ayırmaları dahil olmak üzere, profil oluşturma çalıştırmasında ayrılan tüm belleğin yüzdesi.<br />-Bir tür için, türü örnekleri için ayrılan profil oluşturma çalıştırmasında ayrılan tüm belleğin yüzdesi.|  
|**Dışlamalı baytlar**|-Bir işlev için, üst tür nesneler için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleri tarafından ayrılan belleği içermez.<br />-Bir tür için, tür örnekleri için profil oluşturma çalıştırmasında ayrılan toplam bayt sayısı.|  
|**Dışlamalı bayt yüzdesi**|-Bir işlev için, işlev tarafından üst türün özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm belleğin yüzdesi.<br />-Bir tür için, türü örnekleri için ayrılan profil oluşturma çalıştırmasında ayrılan tüm belleğin yüzdesi.|
