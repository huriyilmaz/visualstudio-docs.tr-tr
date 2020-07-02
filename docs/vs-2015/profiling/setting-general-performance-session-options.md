---
title: Genel performans oturumu seçeneklerini ayarlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3bb57e2c8c5dd156fd5c96994eeb843569954af
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544956"
---
# <a name="setting-general-performance-session-options"></a>Genel Performans Oturumunu Ayarlama Seçenekleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında bir profil oluşturma araçları performans oturumu için koleksiyon yöntemini ve profil oluşturma veri adlandırma kuralları ' nı ayarlayabilirsiniz. Bu iletişim kutusunu **Performans Gezgini**açmak için, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Veri toplama yöntemlerini seçme  
 **Profil oluşturma koleksiyonu**altındaki seçeneklerden birini seçerek temel toplama yöntemini ayarlarsınız. Seçenekler aşağıdaki tabloda açıklanmıştır:  
  
|Seçenek|Açıklama|  
|-|-|  
|**Örnekleme**. Örnekleme yöntemi, düzenli aralıklarla profil oluşturma bilgilerini toplar. Bu yöntem, işlemci kullanımı sorunlarını bulmak için yararlıdır ve en fazla performans araştırmaları başlatmak için önerilen yöntemdir.|-   [Örnekleme kullanarak performans Istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**İzleme**. İzleme yöntemi, bir profil oluşturma çalışması sırasında modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeden bir modül profil oluşturma kodunun bir kopyasına çıkartır. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır.|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Eşzamanlılık**. Eşzamanlılık yöntemi, kodunuzun yürütülmesini engelleyen her olay için veri toplar; Örneğin, bir iş parçacığı, bir uygulama kaynağına yönelik kilitli erişimin serbest gelmesini bekler. Bu yöntem, çok iş parçacıklı uygulamaların çözümlenmesi için yararlıdır.|-   [Iş parçacığını toplama ve eşzamanlılık verilerini Işleme](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Örnekleme veya izleme yöntemlerini kullanarak .NET bellek verileri toplayabilirsiniz. **.Net bellek profili oluşturma**altında veri türünü seçersiniz.  
  
|Seçenekler|Makale|  
|-|-|  
|**.NET nesne ayırma bilgilerini toplayın**. Varsayılan olarak, veriler ayrılan nesnelerin sayısını ve boyutunu içerir. .NET bellek verileri toplamayı etkinleştirmek veya devre dışı bırakmak için bu onay kutusunu işaretleyin veya temizleyin.<br /><br /> **Ayrıca .NET nesne yaşam süresi bilgilerini toplayın**. Bellek nesnelerini geri kazanmak için kullanılan çöp toplama nesilleri hakkındaki verileri dahil etmek için bu onay kutusunu işaretleyin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Profil oluşturmayı başlattığınızda bir profil oluşturma oturumu sayfası görüntülenir, burada profil oluşturmayı duraklatabilir, sürdürebilir ve durdurabilirsiniz.  
  
 ![Profil oluşturma oturum sayfası](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-data-file-options"></a>Profil oluşturma veri dosyası seçeneklerini ayarlama  
  
|Seçenek|Makale|  
|-|-|  
|**Rapor**. Varsayılan olarak, profil oluşturma verileri (. vsp) dosyasına profili oluşturulan uygulamanın adı verilir ve çözüm veya proje klasöründe bulunur. Bir tarih dizesinin da adın sonuna eklendiği ve başka türlü yinelenen adlara sahip olan veri dosyalarına artan bir sayı eklenir. Bu seçenekleri değiştirebilirsiniz.|-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
