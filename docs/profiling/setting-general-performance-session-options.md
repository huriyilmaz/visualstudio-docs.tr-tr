---
title: Genel Performans Oturumu Seçeneklerini | Microsoft Docs
description: Bir performans oturumu için koleksiyon yöntemini ve profil oluşturma veri adlandırma Profil Oluşturma Araçları öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a42998a30856765dcd7c3eaea32a67bcb13f59e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141525"
---
# <a name="set-general-performance-session-options"></a>Genel performans oturumunu ayarlama seçenekleri

Performans oturumunun özellikler iletişim kutusunun Genel sayfasında bir Visual Studio Profil Oluşturma Araçları için toplama  yöntemini ve profil oluşturma veri adlandırma kuralları ayarlayabilirsiniz. Bu iletişim kutusunu dosyadan **açmak Performans Gezgini,** performans oturumuna sağ tıklayın ve ardından Özellikler'e **tıklayın.**

## <a name="choosing-data-collection-methods"></a>Veri toplama yöntemlerini seçme

Profil oluşturma koleksiyonu altındaki seçeneklerden birini seçerek temel koleksiyon **yöntemini ayarlayın.** Seçenekler aşağıdaki tabloda açıklanmıştır:

|Seçenek|Makale|
|-|-|
|**Örnekleme.** Örnekleme yöntemi, profil oluşturma bilgilerini düzenli aralıklarla toplar. Bu yöntem, işlemci kullanım sorunlarını bulmak için yararlıdır ve performans araştırmalarını başlatmaya ilişkin önerilen yöntemdir.|- [Örnekleme Kullanarak Performans İstatistikleri Toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentation**. Ölçüm yöntemi, profil oluşturma çalıştırması sırasında modülde işlevlerin her girdisini, çıkış ve işlev çağrısını kaydeden bir modül profil oluşturma kodunun bir kopyasına ekler. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerindeki etkisini anlamak için yararlıdır.|- [Ölçüm ölçümlerini kullanarak Ayrıntılı Zamanlama Verileri Toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Eşzamanlılık**. Eşzamanlılık yöntemi, bir iş parçacığının uygulama kaynağına kilitli erişimin serbest bıraklığını beklemesi gibi kodunuzun yürütülmesini engelleyen her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamaları analiz etmek için kullanışlıdır.|- [İş Parçacığı ve İşlem Eşzamanlılık Verileri Toplama](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Örnekleme veya ölçüm yöntemlerini kullanarak .NET bellek verilerini toplayabilirsiniz. .NET bellek profili oluşturma altında **veri türünü seçersiniz.**

|Seçenek|Makale|
|-|-|
|**.NET nesne ayırma bilgilerini toplayın.** Varsayılan olarak, veriler ayrılan nesnelerin sayısını ve boyutunu içerir. .NET bellek veri toplamayı etkinleştirmek veya devre dışı bırakmak için bu onay kutusunu seçin veya temizleyin. |- [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Ayrıca .NET nesne yaşam süresi bilgilerini de toplayın.** Bellek nesnelerini geri iade etmek için kullanılan atık toplama nesilleri ile ilgili verileri eklemek için bu onay kutusunu seçin.|- [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Profil oluşturmayı duraklatmak, devam etmek ve durdurmak için bir uygulama profili oluşturmayı başlatmanız sırasında profil oluşturma oturumu sayfası görüntülenir.

 ![Profil oluşturma oturumu sayfası](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Profil oluşturma veri dosyası seçeneklerini ayarlama

|Seçenek|Makale|
|-|-|
|**rapor.** Varsayılan olarak, profil oluşturma verileri (.vsp) dosyasına profili profili yapılan uygulamanın adı verilir ve çözüm veya proje klasöründe bulunur. Ayrıca, adına bir tarih dizesi eklenir ve aksi takdirde yinelenen adlara sahip olacak veri dosyalarına artırılmış bir sayı eklenir. Bu seçenekleri değiştirebilirsiniz.|- [Nasıl yapabilirsiniz: Performans Veri Dosyası Adı Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
