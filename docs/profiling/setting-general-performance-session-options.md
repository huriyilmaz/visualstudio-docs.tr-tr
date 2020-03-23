---
title: Genel Performans Oturum Seçeneklerinin Ayarlanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 023681b263e6e70048ec7d82d2cee741672989ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773948"
---
# <a name="set-general-performance-session-options"></a>Genel performans oturumunu ayarlama seçenekleri

Performans oturumu için özellikler iletişim kutusunun **Genel** sayfasında visual studio Profil Oluşturma Araçları performans oturumu için toplama yöntemini ve profil oluşturma veri adlandırma kurallarını ayarlayabilirsiniz. **Performans Gezgini'nden**bu iletişim kutusunu açmak için performans oturumunu sağ tıklatın ve ardından **Özellikler'i**tıklatın.

## <a name="choosing-data-collection-methods"></a>Veri toplama yöntemlerini seçme

Profil oluşturma koleksiyonu altındaki seçeneklerden birini seçerek temel toplama **yöntemini**ayarlarsınız. Seçenekler aşağıdaki tabloda açıklanmıştır:

|||
|-|-|
|**Örnekleme**. Örnekleme yöntemi, profil oluşturma bilgilerini düzenli aralıklarla toplar. Bu yöntem işlemci kullanım sorunlarını bulmak için yararlıdır ve çoğu performans araştırmasını başlatmak için önerilen yöntemdir.|- [Örnekleme Kullanarak Performans İstatistiklerini Toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Enstrümantasyon**. Enstrümantasyon yöntemi, bir profil oluşturma çalışması sırasında modüldeki işlevlerin her giriş, çıkış ve işlev çağrısını kaydeden bir modül profil oluşturma kodunun kopyasına enjekte eder. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıktı işlemlerinin uygulama performansı üzerindeki etkisini anlamak için yararlıdır.|- [Enstrümantasyon Kullanarak Ayrıntılı Zamanlama Verileri Toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Eşzamanlılık**. Eşzamanlılık yöntemi, bir iş parçacığının serbest bırakılacak bir uygulama kaynağına kilitli erişimi beklemesi gibi kodunuzu engelleyen her olay için veri toplar. Bu yöntem, çok iş parçacığı uygulamaları çözümleme için yararlıdır.|- [İş Parçacığı ve İşlem EşzamanlıLık Verilerini Toplama](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Örnekleme veya enstrümantasyon yöntemlerini kullanarak .NET bellek verilerini toplayabilirsiniz. **.NET bellek profiloluşturma**altında veri türünü seçin.

|||
|-|-|
|**.NET nesne ayırma bilgilerini topla.** Varsayılan olarak, veriler ayrılan nesnelerin sayısını ve boyutunu içerir. .NET bellek veri toplamayı etkinleştirmek veya devre dışı kakmak için bu onay kutusunu seçin veya temizleyin. |- [.NET Bellek Tahsisi ve Yaşam Boyu Veri Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Ayrıca .NET nesne yaşam boyu bilgi toplamak**. Bellek nesnelerini geri almak için kullanılan çöp toplama nesilleri hakkında veri eklemek için bu onay kutusunu seçin.|- [.NET Bellek Tahsisi ve Yaşam Boyu Veri Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Profil oluşturma oturumu sayfası, profil oluşturmayı duraklatabileceğiniz, devam ettirebileceğiniz ve durdurabileceğiniz bir uygulamanın profilini çıkarmaya başladığınızda görüntülenir.

 ![Profil oluşturma oturumu sayfası](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Profil oluşturma veri dosyası seçeneklerini ayarlama

|||
|-|-|
|**Rapor edin.** Varsayılan olarak, profil oluşturma verileri (.vsp) dosyasına profilli uygulamanın adı verilir ve çözüm veya proje klasöründe bulunur. Bir tarih dizesi de ada eklenir ve aksi takdirde yinelenen adlara sahip olan veri dosyalarına artımlı bir sayı eklenir. Bu seçenekleri değiştirebilirsiniz.|- [Nasıl kullanılır: Performans Verisi Dosya Adı Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
