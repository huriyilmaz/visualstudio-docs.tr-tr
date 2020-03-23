---
title: Performans araçlarını çalıştırma işlemlerine ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4c4ae54d6b90166de31c338a5e606eaf31ecd6cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779174"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: Performans araçlarını çalışan işlemlere ekleme ve bunlardan ayırma
Profil oluşturucu, örnekleme ve performans verilerini toplamayı kolaylaştırmak için çalışan bir işleme eklemek veya bu işlemden ayırmak için kullanılabilir. Uygulama yükleme süresi hakkında veri toplamaktan kaçınmak istediğinizde bir işlemin profilini çıkarmak veya belirli bir duruma ulaştıktan sonra bir işlemin performansını izlemek için bu yöntemi kullanabilirsiniz.

> [!NOTE]
> Aşağıdaki [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] adımlar, tümleşik geliştirme çevresi (IDE) içinden süreçleri iliştirmek ve ayırmak için geçerlidir. Komut satırı araçlarının nasıl kullanılacağı hakkında bilgi için [komut satırındaki Profil'e](../profiling/using-the-profiling-tools-from-the-command-line.md)bakın. Hizmetlerin nasıl profilini niçin oluşturabileceğiniz hakkında bilgi için [Profil hizmetlerine](../profiling/command-line-profiling-of-services.md)bakın.

 Profil için kullanılabilen işlemler, bilgisayarın bir yöneticisi tarafından ayarlanan Kullanıcı Erişim İzinlerine bağlıdır. Örneğin, bir Kullanıcı hesabı aşağıdakilerden herhangi biri için izin alabilir:

- Yönetici sürücüyü ve hizmeti başlatmak için ayarladığında gelişmiş profil oluşturma özellikleri.

- Yalnızca örnek profil oluşturma (etki alanı kullanıcıları).

- Herkese profil oluşturma erişimini reddedin.

  Daha fazla bilgi için, [VSPerfCmd'deki](../profiling/vsperfcmd.md) [Profil oluşturma ve Windows Vista güvenliği ve](../profiling/profiling-and-windows-vista-security.md) ADMIN seçeneklerine bakın.

### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme eklemek için

1. Hata **Ayıklama** menüsünde **Profiler'ı**, ardından **Performans Gezgini'ni**işaret edin ve sonra **Ekle'yi**tıklatın.

     **Profil oluştur'u İşleme** iletişim kutusuna ekle görüntülenir.

2. Eklemek istediğiniz işlemin adını tıklatın.

3. **Ekle'yi**tıklatın.

### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayırmak için

1. n **Hata Ayıklama** menüsü, **Profiler**işaret , sonra **Performans Gezgini**, ve sonra **Detach**tıklatın.

     **Profil oluştur'u İşleme** iletişim kutusuna ekle görüntülenir.

2. Ayırmak istediğiniz resim adını tıklatın.

3. **Ayır'ı**tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)
- [Nasıl kullanılır: Performans veri toplamayı başlatın ve sonla](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
