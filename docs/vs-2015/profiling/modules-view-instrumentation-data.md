---
title: Modüller görünümü-Izleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4455f850ad533f17cd9f6cb33e7e874621d0bb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205898"
---
# <a name="modules-view---instrumentation-data"></a>Modüller Görünümü - İzleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modüller görünümü profil oluşturma verilerinde olan modüllerle gruplanmış performans verilerini görüntüler. Modülün işlevleri modül düğümünün altında listelenmiştir.  
  
## <a name="general"></a>Genel  
 Genel sütunlar, bir görünüm satırındaki işlevi belirler.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlevin veya modülün adı.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Çağrı Sayısı**|Bu işlev veya modüle yapılan toplam çağrı sayısı.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|İşlevi içeren modülün yolu.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Modülün veya işlevin yürütüldüğü işlemin adı.|  
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev veya modül için izleme nedeniyle zaman yükü.|  
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev veya modülle ilgili zaman yükü ve izleme nedeniyle alt işlevleri.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler  
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen kapsamlı süre**|-Bir işlev için, işlevde harcanan zaman. Bu, alt işlevlerde harcanan zamanı ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları içerir.<br />-Bir modül için, modüldeki en az bir işlevin çağrı yığınında olduğu zaman.|  
|**Geçen kapsamlı süre yüzdesi**|Bu modülün veya işlevin toplam geçen kapsamlı süresi içinde harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|  
|**Ortalama geçen kapsamlı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen ortalama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen ortalama kapsamlı süresi.|  
|**Geçen maksimum kapsamlı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen en uzun kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen maksimum kapsamlı süresi.|  
|**Geçen minimum kapsamlı süre**|-Bir işlev için, bu modül veya işlev çağrısının geçen en düşük kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların geçen minimum kapsamlı süresi.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler  
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içerir, ancak alt işlevlerde harcanan zamanı içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dışlamalı süre**|-Bir işlev için, modülde veya işlevinde harcanan zaman. Bu, işletim sistemine çağrı içerir (bağlam anahtarları ve giriş/çıkış işlemleri gibi), ancak alt işlevlerde harcanan süreyi dışlar.<br />-Bir modül için, modüldeki işlevlerin geçen dışlamalı saatlerin toplamı.|  
|**Geçen dışlamalı süre yüzdesi**|Bu modülün veya işlevin toplam geçen dışlamalı süre içinde harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|  
|**Geçen ortalama dışlamalı süre**|-Bir işlev için, bu işleve yapılan çağrının ortalama hariç geçen süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama hariç geçen süresi.|  
|**Geçen maksimum dışlamalı süre**|-Bir işlev için, bu işleve yapılan çağrının geçen en büyük dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrılar için geçen maksimum dışlamalı süre.|  
|**Geçen en düşük dışlamalı süre**|-Bir işlev için, bu modül veya işlev çağrısının en az bir özel süresi geçti.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en düşük özel süresi geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler  
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan zamanı içermez. Ancak, bu süre alt işlevlerde harcanan zamanı içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama kapsamlı süresi**|-Bir işlev için, işlev çağrılarında harcanan zaman. Bu, alt işlevlerde harcanan zamanı içerir, ancak bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dışlar.<br />-Bir modül için, modüldeki en az bir işlevin çağrı yığınında olduğu zaman. Bu, işletim sistemi çağrılarında harcanan süreyi dışlar.|  
|**Uygulama kapsamlı süresi%**|Bu modülün veya işlevin uygulama kapsamlı sırasında harcanan, profil oluşturma çalıştırmasının toplam geçen iç süresinin yüzdesi.|  
|**Ortalama uygulama kapsamlı süresi**|-Bir işlev için, bu işleve yapılan çağrının ortalama uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama uygulama kapsamlı süresi.|  
|**En fazla uygulama kapsamlı süresi**|-Bir işlev için, bu işleve yapılan çağrının en büyük uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en fazla uygulama kapsamlı süresi.|  
|**En az uygulama kapsamlı süre**|-Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama kapsamlı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en düşük uygulama kapsamlı süresi.|  
  
## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri  
 Uygulamanın dışlamalı değeri, modülde veya işlevde harcanan süreyi belirtir. Bu, alt işlevlerde harcanan süreyi dışlar ve ayrıca, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine çağrıları dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı uygulama süresi**|Bu modül veya işleve yapılan tüm çağrıların Toplam uygulama dışlamalı süresi.|  
|**Uygulama dışlamalı süresi%**|Bu modülün veya işlevin uygulama dışlamalı sırasında harcanan, profil oluşturma çalıştırmasının toplam geçen dışlamalı sürenin yüzdesi.|  
|**Ortalama uygulama dışlamalı süresi**|-Bir işlev için, bu işleve yapılan çağrının ortalama uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların ortalama uygulama dışlamalı süresi.|  
|**Maksimum uygulama dışlamalı süresi**|-Bir işlev için, bu işleve yapılan çağrının en büyük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrıların en fazla uygulama dışlamalı süresi.|  
|**En az uygulama dışlamalı süresi**|-Bir işlev için, bu modüle veya işleve yapılan çağrının en düşük uygulama dışlamalı süresi.<br />-Bir modül için, modüldeki işlevlere yapılan tüm çağrılar için en düşük uygulama dışlamalı süresi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modüller görünümü](../profiling/modules-view-sampling-data.md)   
 [Modüller görünümü-Izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller Görünümü - Örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
