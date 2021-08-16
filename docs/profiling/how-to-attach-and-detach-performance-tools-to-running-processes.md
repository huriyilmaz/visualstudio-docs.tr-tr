---
title: Çalışan işlemlere performans araçları iliştirme
description: örnekleme ve performans verilerini toplamayı kolaylaştırmak için çalışan bir işleme eklemek veya ayırmak üzere Visual Studio profil oluşturucuyu kullanmayı öğrenin.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7a47db533dd894ebd2fc31cbd1b27214b5c0277ba9dca80d0d6dcae09e63d913
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368571"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: Performans araçlarını çalışan işlemlere ekleme ve bunlardan ayırma
Profil Oluşturucu, örnekleme yapmak ve performans verilerini toplamak için çalışan bir işlemden eklemek ya da ayırmak için kullanılabilir. Bu yöntemi, uygulama yükleme süresi hakkında veri toplamayı önlemek veya belirli bir duruma ulaştıktan sonra bir işlemin performansını izlemek istediğinizde bir işlemi profil için kullanabilirsiniz.

> [!NOTE]
> Aşağıdaki adımlar, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Tümleşik geliştirme environmnent (IDE) içinden işlemleri eklemek ve ayırmak için geçerlidir. Komut satırı araçlarını kullanma hakkında daha fazla bilgi için, bkz. [komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md). Hizmetleri profil oluşturma hakkında daha fazla bilgi için bkz. [profil hizmetleri](../profiling/command-line-profiling-of-services.md).

 Profil için kullanılabilen süreçler, bilgisayarın yöneticisi tarafından ayarlanan Kullanıcı erişim Izinlerine bağlıdır. Örneğin, bir kullanıcı hesabı, aşağıdakilerden herhangi biri için izne sahip olabilir:

- Yönetici, sürücüyü ve hizmeti başlatılmak üzere ayarladığınızda gelişmiş profil oluşturma özellikleri.

- Yalnızca örnek profil oluşturma (etki alanı kullanıcıları).

- Herkes için profil oluşturma erişimini engelleyin.

  daha fazla bilgi için bkz. [profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [vsperfcmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.

### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için

1. **Hata Ayıkla** menüsünde **Profiler**' ın üzerine gelin ve **Performans Gezgini** ve ardından **Ekle**' ye tıklayın.

     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.

2. Eklemek istediğiniz işlemin adına tıklayın.

3. **Ekle**' ye tıklayın.

### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayrılmak için

1. **Hata Ayıkla** menüsünde, **Profil Oluşturucu** üzerine gelin ve **Performans Gezgini** ve ardından **Ayır**' a tıklayın.

     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.

2. Ayırmak istediğiniz görüntü adına tıklayın.

3. **Ayır**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)
- [Nasıl yapılır: performans veri toplamayı başlatma ve bitirme](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
