---
title: Çalışan işlemlere performans araçları ekleme
description: Örnekleme ve performans verilerini Visual Studio için çalışan bir işleme eklemek veya bu işlemden ayırmak için Visual Studio profilleyiciyi kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4002334d8fba7b31e33eecd5cf49532ba384046d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390027"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: Performans araçlarını çalışan işlemlere ekleme ve bunlardan ayırma
Profil oluşturma, örnekleme ve performans verilerini toplamayı kolaylaştırmak için çalışan bir işleme eklemek veya işlemden ayırmak için kullanılabilir. Uygulama yükleme süresi hakkında veri toplamaktan kaçınmak veya belirli bir durumuna ulaştıktan sonra bir sürecin performansını izlemek istediğiniz bir işlem profili oluşturmak için bu yöntemi kullanabilirsiniz.

> [!NOTE]
> Aşağıdaki adımlar, tümleşik geliştirme [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] environmnent (IDE) içinde işlemleri ekleme ve ayırma işlemleri için geçerlidir. Komut satırı araçlarını kullanma hakkında bilgi için [bkz. Komut satırı profili.](../profiling/using-the-profiling-tools-from-the-command-line.md) Hizmetlerin profilini oluşturma hakkında bilgi için bkz. [Profil hizmetleri.](../profiling/command-line-profiling-of-services.md)

 Profil için kullanılabilen işlemler, bilgisayarın yöneticisi tarafından ayarlanmış Kullanıcı Erişim İzinlerine bağlıdır. Örneğin, bir Kullanıcı hesabının, aşağıdakilerin herhangi biri için izni olabilir:

- Yönetici, sürücüyü ve hizmeti başlatıyorsa gelişmiş profil oluşturma özellikleri.

- Yalnızca örnek profil oluşturma (etki alanı kullanıcıları).

- Herkese profil oluşturma erişimini reddedin.

  Daha fazla bilgi için, [bkz. Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [VSPerfCmd'de YÖNETİCI seçenekleri.](../profiling/vsperfcmd.md)

### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme eklemek için

1. Hata **Ayıkla menüsünde** **Profiler'ın üzerine gelin,** ardından **öğesini Performans Gezgini** ve ekle'ye **tıklayın.**

     **profiler'ı İşleme Ekle** iletişim kutusu görüntülenir.

2. Eklemek istediğiniz sürecin adına tıklayın.

3. **Ekle'ye tıklayın.**

### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayırmak için

1. n hata **ayıkla menüsünde** **Profiler'ın üzerine gelin,** **ardından öğesini Performans Gezgini** ayır'a **tıklayın.**

     **profiler'ı İşleme Ekle** iletişim kutusu görüntülenir.

2. Ayırmak istediğiniz görüntü adına tıklayın.

3. **Ayır'a tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)
- [Nasıl kullanılır: Başlangıç ve bitiş performans verileri toplama](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
