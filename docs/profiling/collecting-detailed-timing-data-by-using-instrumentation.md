---
title: Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama
description: Kodunuzun bir Profil Oluşturma Araçları ayrıntılı zamanlama bilgileri için ve I/O işlemlerinin etkisini anlamak için Profil Oluşturma Araçları ölçüm ölçümleme yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 128faca35ef666ee791147718aa2eaac82f07984ecb285b54926717730b3d8a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396948"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>İzleme kullanarak ayrıntılı zamanlama verileri toplama
Veri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları yöntemi, profil oluşturma kodunu bir modülün kopyasına ekler. Kod, profil oluşturma çalıştırması sırasında modülde işlevlerin giriş, çıkış ve işlev çağrılarını kaydediyor. Ölçüm yöntemi, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerindeki etkisini anlamak için kullanışlıdır.

 Aşağıdaki yordamlardan birini kullanarak ölçümleme yöntemini belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında, Ölçümler'i **seçin.**

- Araç **çubuğunda Performans Gezgini** listesinde, **Ölçümler'e** **tıklayın.**

- Performans **oturumunun** özellikler iletişim kutusunun Genel sayfasında, Ölçümler'i **seçin.**

## <a name="common-tasks"></a>Genel görevler
 Performans oturumunun Performans Oturumu _Özellik Sayfaları_**iletişim kutusunda** ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- Bu **Performans Gezgini,** performans oturumu adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

  Aşağıdaki tabloda yer alan görevler, ölçüm ölçüm yöntemini kullanarak profil oluşturma sırasında Performans Oturumu **Özellik** Sayfaları iletişim kutusunda belirtebilirsiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|Genel sayfasında **.NET** bellek ayırma ve yaşam süresi verilerini ekleyin ve oluşturulan profil oluşturma verileri (.vsp) dosyası için adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl kullanılır: Performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Başlat **sayfasında,** çözümünüzde birden çok .exe projeniz varsa, başlatacak uygulamayı ve bunların başlangıç sıralarını belirtin.|-   [Nasıl olur: Başlamak için ikili dosya belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|Ikili **Dosyalar sayfasında,** modüllerin irdeli kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikili dosyalar bir yedekleme klasörüne taşınır.|-   [Nasıl olur: Araçlı ikilileri yeniden bulma](../profiling/how-to-relocate-instrumented-binaries.md)|
|Katman **Etkileşimi sayfasında,** profil oluşturma ADO.NET veri çağırmayı seçin.|-   [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Ölçümler **sayfasında,** profil oluşturma ek yükünü azaltmak için küçük işlevleri profil oluşturmanın dışında tutmak, ASP.NET Web sayfalarında JavaScript kodunun profilini oluşturmak ve ölçümleme işlemi öncesinde ve sonrasında komut isteminde çalıştırılacak komutları belirtin.|-   [Nasıl kullanılır: Kısa işlevleri ölçümden hariç tutmak veya dahil etmek](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Nasıl kullanılır: Web sayfalarında JavaScript kodunun profilini oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Nasıl kullanılır: Ön ve son ölçüm komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|CPU **Sayaçları sayfasında,** profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [Nasıl kullanılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|Örnek **Windows sayfasında,** örnekleme verileriyle topilebilecek bir Windows olay için bir veya daha fazla Olay İzleme (ETW) olayı seçin.|-   [Nasıl Windows (ETW) verileri için olay izleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Profil **Windows profil** oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl Windows: Windows toplama](../profiling/how-to-collect-windows-counter-data.md)|
|Gelişmiş **sayfasında,** VSInstr instrumentation programına geçmek istediğiniz belirli işlevleri dahil etmek veya hariç tutmak için seçenekler gibi ek seçenekleri belirtin.|-   [Nasıl yapabilirsiniz: Ek ölçüm seçenekleri belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Nasıl kullanılır: Araçları belirli işlevlerle sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Vsınstr](../profiling/vsinstr.md)|
