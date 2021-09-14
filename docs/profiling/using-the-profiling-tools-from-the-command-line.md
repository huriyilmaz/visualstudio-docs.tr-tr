---
title: Command-Line Profil Oluşturma Araçları kullanma | Microsoft Docs
description: uygulama profili oluşturmak ve toplu iş dosyalarını ve komut dosyalarını kullanarak profil oluşturmayı otomatikleştirmek için Visual Studio Profil Oluşturma Araçları komut satırı araçlarını kullanın.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e954fe8eb6bef735b90d73ac9384f321ae6c8320
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725667"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Komut satırından Profil Oluşturma Araçları kullanın
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Komut isteminde uygulamalar profili oluşturmak ve toplu iş dosyalarını ve komut dosyalarını kullanarak profil oluşturmayı otomatikleştirmek için profil oluşturma araçları komut satırı araçlarını kullanabilirsiniz. Ayrıca, bir komut isteminde rapor dosyaları da oluşturabilirsiniz. Yüklü olmayan bilgisayarlarda veri toplamak için hafif tek başına profil oluşturucuyu kullanabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Simgelerin konumunu ayarlayın:** İşlevlerin ve parametrelerin adlarını göstermek için, profil oluşturucunun simgeye erişimi olmalıdır (.*pdb*) dosyaları profili oluşturulmuş ikililer. Bu dosyalar, analizinizdeki görüntülemek istediğiniz Microsoft işletim sistemi ve uygulamaları için simge dosyalarını içermelidir. Doğru olduğundan emin olmak için genel Microsoft sembol sunucusu ' nu kullanabilirsiniz. Microsoft ikilileri için *pdb* dosyaları. | -   [Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Uygulamanızın profilini yapın:** Bir hedef uygulama profilini oluşturmak için kullandığınız komut satırı araçları ve seçenekleri uygulamanın türüne, profil oluşturma yöntemine ve hedefin yönetilen ya da yerel bir uygulama olup olmadığına bağlıdır. | -   [Komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md) |
| **.xml ve .csv raporları oluşturun:** Komut isteminde profil oluşturma, için arabiriminde görüntülenebilen veri dosyaları oluşturur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ayrıca oluşturabilirsiniz. *XML* veya virgülle ayrılmış değer (.*CSV*) VSPerfReport komut satırı aracını kullanarak veri dosyaları. | -   [Komut satırından profil Oluşturucu raporları oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Visual Studio olmayan bilgisayarlarda profil kodu:** Yüklü olmayan bilgisayarlardaki uygulamalar için veri toplamak üzere Profil Oluşturma Araçları tek başına profil oluşturucuyu kullanabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . | -   [Nasıl yapılır: tek başına profil oluşturucuyu yüklemek](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Başvuru
- [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
