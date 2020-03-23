---
title: Sorun Giderme Performans Araçları Sorunları | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778108"
---
# <a name="troubleshoot-performance-tools-issues"></a>Performans araçları sorunları
Profil Oluşturma Araçlarını kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:

- [Profil oluşturma araçları tarafından veri toplanmaz](#no-data-is-collected-by-the-profiling-tools)

- [Performans Görünümleri ve raporlar işlev adları için numaraları görüntüler](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Profil oluşturma araçları tarafından veri toplanmaz
 Bir uygulamanın profilini çıkardıktan sonra, profil oluşturma verileri (.* vsp*) dosyası oluşturulmaz ve **Çıkış** penceresinde veya komut penceresinde aşağıdaki uyarıyı alırsınız:

 PRF0025: Veri toplanmadı.

 Bu sorun çeşitli sorunlardan kaynaklanabilir:

- Örnekleme veya .NET bellek yöntemi kullanılarak profillenmiş bir işlem, uygulama çalışmasını gerçekleştiren işlem haline gelen bir alt işlem başlatır. Örneğin, bazı uygulamalar windows uygulaması olarak mı yoksa komut satırı uygulaması olarak mı başlatıldığını belirlemek için komut satırını okur. Bir Windows uygulaması istenirse, özgün işlem Windows uygulaması olarak yapılandırılan yeni bir işlem başlatır ve özgün işlem çıkar. Profil Oluşturma Araçları alt işlemler için otomatik olarak veri toplamdığından, hiçbir veri toplanmaz.

     Bu durumda profil oluşturma verileri toplamak için, uygulamayı profil oluşturucuyla başlatmak yerine profil oluşturcayı alt işleme takın. Daha fazla bilgi için [bkz: Performans araçlarını çalıştırma işlemlerine ekleme ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) [(VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Performans görünümleri ve raporlar işlev adları için numaraları görüntüler
 Bir uygulamayı profilledikten sonra, raporlarda ve görünümlerde işlev adları yerine sayılar görürsünüz.

 Bu sorun, Profil Oluşturma Araçları çözümleme motorunun . kaynak kod bilgilerini eşleyen sembol bilgilerini içeren *pdb* dosyaları, bu tür işlev adları ve satır numaraları derlenen dosyaya. Varsayılan olarak, derleyici . uygulama dosyası oluşturulunca *pdb* dosyası. Yerel dizine bir başvuru. *pdb* dosyası derlenen uygulamada saklanır. Analiz motoru için başvurulan dizini bakar. *pdb* dosyası ve daha sonra şu anda uygulama dosyasını içeren dosya. Eğer . *pdb* dosyası bulunamadı, çözümleme motoru işlev adları yerine işlev ofsetlerini kullanır.

 Sorunu iki şekilde çözebilirsiniz:

- Bulun. *pdb* dosyaları ve uygulama dosyaları ile aynı dizine yerleştirin.

- Profil oluşturma verilerine sembol bilgilerini gömün (.* vsp*) dosyası. Daha fazla bilgi için [bkz.](../profiling/saving-symbol-information-with-performance-data-files.md)

> [!NOTE]
> Analiz motoru gerektirir . *pdb* dosyası derlenen uygulama dosyasıyla aynı sürümdür. A. uygulama dosyasının daha önceki veya daha sonra oluşturduğu *pdb* dosyası çalışmaz.
