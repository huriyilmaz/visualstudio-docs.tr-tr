---
title: Performans araçları sorunlarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 514b910f2c19822dc821b8c9a52ae96b8aac80f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778108"
---
# <a name="troubleshoot-performance-tools-issues"></a>Performans araçları sorunlarını giderme
Profil Oluşturma Araçları kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:

- [Profil oluşturma araçları tarafından hiçbir veri toplanmadı](#no-data-is-collected-by-the-profiling-tools)

- [Performans görünümleri ve raporlar işlev adlarının numaralarını görüntüler](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Profil oluşturma araçları tarafından hiçbir veri toplanmadı
 Bir uygulamayı profilledikten sonra, profil oluşturma verileri (.* VSP*) dosyası oluşturulmaz ve **Çıkış** penceresinde veya komut penceresinde aşağıdaki uyarıyı alırsınız:

 PRF0025: veri toplanmadı.

 Bu sorun birkaç sorundan kaynaklanıyor olabilir:

- Örnekleme veya .NET bellek yöntemi kullanılarak profili oluşturulmuş bir işlem, uygulamanın çalışmasını gerçekleştiren işlem haline gelen bir alt işlem başlatır. Örneğin, bazı uygulamalar, bir Windows uygulaması veya bir komut satırı uygulaması olarak başlatılıp başlatılmayacağını anlamak için komut satırını okur. Bir Windows uygulaması isteniyorsa, özgün işlem Windows uygulaması olarak yapılandırılmış yeni bir işlem başlatır ve ardından orijinal işlem çıkar. Profil Oluşturma Araçları alt işlemlere yönelik verileri otomatik olarak toplamadığından, hiçbir veri toplanmaz.

     Bu durumda profil oluşturma verilerini toplamak için, profil oluşturucuyu, uygulamayı profil Oluşturucu ile başlatmak yerine alt işleme bağlayın. Daha fazla bilgi için bkz [. nasıl yapılır: performans araçlarını çalışan Işlemlere bağlama ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) ve [Iliştirme (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Performans görünümleri ve raporlar işlev adlarının numaralarını görüntüler
 Bir uygulamayı profilledikten sonra, raporlarda ve görünümlerde işlev adları yerine sayılar görürsünüz.

 Bu sorun, Profil Oluşturma Araçları Analysis Engine 'in bulamamasından kaynaklanmıştır. kaynak kodu bilgilerini, derlenmiş dosyanın işlev adlarını ve satır numaralarını eşleyen simge bilgilerini içeren *pdb* dosyaları. Varsayılan olarak, derleyici öğesini oluşturur. uygulama dosyası yapılandırıldığında *pdb* dosyası. Yerel dizinine başvuru. *pdb* dosyası derlenen uygulamada depolanıyor. Analiz altyapısı, için başvurulan dizine bakar. *pdb* dosyası ve ardından uygulama dosyasını içeren dosyada. . *pdb* dosyası bulunamadı, analiz Altyapısı işlev adları yerine işlev uzaklıklarını kullanır.

 Sorunu iki şekilde giderebilirsiniz:

- Öğesini bulun. *pdb* dosyaları ve uygulama dosyalarıyla aynı dizine yerleştirin.

- Sembol bilgilerini profil oluşturma verilerine ekleyin (.* VSP*) dosyası. Daha fazla bilgi için bkz. [performans veri dosyalarıyla sembol bilgilerini kaydetme](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Analiz altyapısı, için gerektirir. *pdb* dosyası, derlenen uygulama dosyasıyla aynı sürümdür. A. uygulama dosyasının önceki veya sonraki bir derlemeden *pdb* dosyası çalışmayacak.
