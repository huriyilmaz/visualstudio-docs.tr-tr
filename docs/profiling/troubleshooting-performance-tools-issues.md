---
title: Performans araçları sorunlarını giderme | Microsoft Docs
description: Profil oluşturma araçları tarafından veri toplandığında, örneğin, performans araçları sorunlarını giderirken kullanabileceğiniz çeşitli sorunlar hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1d2339ee7638fa6e3a4b1776abd61196cbe814cf075228b5d0eee651d89e70cc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230982"
---
# <a name="troubleshoot-performance-tools-issues"></a>Performans araçları sorunlarını giderme
Profil Oluşturma Araçları kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:

- [Profil oluşturma araçları tarafından hiçbir veri toplanmadı](#no-data-is-collected-by-the-profiling-tools)

- [Performans görünümleri ve raporlar işlev adlarının numaralarını görüntüler](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Profil oluşturma araçları tarafından hiçbir veri toplanmadı
 Bir uygulamayı profilledikten sonra, profil oluşturma verileri (.*VSP*) dosyası oluşturulmaz ve **Çıkış** penceresinde veya komut penceresinde aşağıdaki uyarıyı alırsınız:

 PRF0025: veri toplanmadı.

 Bu sorun birkaç sorundan kaynaklanıyor olabilir:

- Örnekleme veya .NET bellek yöntemi kullanılarak profili oluşturulmuş bir işlem, uygulamanın çalışmasını gerçekleştiren işlem haline gelen bir alt işlem başlatır. örneğin, bazı uygulamalar, Windows bir uygulama olarak veya bir komut satırı uygulaması olarak başlatılıp başlatılmayacağını anlamak için komut satırını okur. Windows bir uygulama isteniyorsa, özgün işlem, Windows uygulama olarak yapılandırılmış yeni bir işlem başlatır ve ardından özgün işlem çıkar. Profil Oluşturma Araçları alt işlemlere yönelik verileri otomatik olarak toplamadığından, hiçbir veri toplanmaz.

     Bu durumda profil oluşturma verilerini toplamak için, profil oluşturucuyu, uygulamayı profil Oluşturucu ile başlatmak yerine alt işleme bağlayın. Daha fazla bilgi için bkz [. nasıl yapılır: performans araçlarını çalışan Işlemlere bağlama ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) ve [Iliştirme (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Performans görünümleri ve raporlar işlev adlarının numaralarını görüntüler
 Bir uygulamayı profilledikten sonra, raporlarda ve görünümlerde işlev adları yerine sayılar görürsünüz.

 Bu sorun, Profil Oluşturma Araçları Analysis Engine 'in bulamamasından kaynaklanmıştır. kaynak kodu bilgilerini, derlenmiş dosyanın işlev adlarını ve satır numaralarını eşleyen simge bilgilerini içeren *pdb* dosyaları. Varsayılan olarak, derleyici öğesini oluşturur. uygulama dosyası yapılandırıldığında *pdb* dosyası. Yerel dizinine başvuru. *pdb* dosyası derlenen uygulamada depolanıyor. Analiz altyapısı, için başvurulan dizine bakar. *pdb* dosyası ve ardından uygulama dosyasını içeren dosyada. . *pdb* dosyası bulunamadı, analiz Altyapısı işlev adları yerine işlev uzaklıklarını kullanır.

 Sorunu iki şekilde giderebilirsiniz:

- Öğesini bulun. *pdb* dosyaları ve uygulama dosyalarıyla aynı dizine yerleştirin.

- Sembol bilgilerini profil oluşturma verilerine ekleyin (.*VSP*) dosyası. Daha fazla bilgi için bkz. [performans veri dosyalarıyla sembol bilgilerini kaydetme](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Analiz altyapısı, için gerektirir. *pdb* dosyası, derlenen uygulama dosyasıyla aynı sürümdür. A. uygulama dosyasının önceki veya sonraki bir derlemeden *pdb* dosyası çalışmayacak.
