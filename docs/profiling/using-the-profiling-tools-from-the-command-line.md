---
title: Profil Oluşturma Araçları'den Command-Line | Microsoft Docs
description: Uygulamaların profilini oluşturmak ve toplu Visual Studio Profil Oluşturma Araçları betik oluşturma kullanarak profil oluşturmayı otomatikleştirmek için komut satırı araçlarını kullanın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140875"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Komut Profil Oluşturma Araçları komutunu kullanma
Komut isteminde uygulamaların profilini oluşturmak Profil Oluşturma Araçları toplu dosya ve betik kullanarak profil oluşturmayı otomatikleştirmek için komut satırı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] araçlarını kullanabilirsiniz. Ayrıca, bir komut isteminde rapor dosyaları da oluşturabilirsiniz. Yüklü olmayan bilgisayarlarda veri toplamak için basit tek başına profilleyiciyi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Sembollerin konumunu ayarlayın:** İşlevlerin ve parametrelerin adlarını görüntülemek için profil oluşturmanın simgesine () erişimi olmalıdır.*profili profili* yapılan ikili dosyaların pdb ) dosyaları. Bu dosyalar, analizde görüntülemek istediğiniz Microsoft işletim sistemi ve uygulamaları için sembol dosyalarını içerir. Doğru olduğundan emin olmak için genel Microsoft sembol sunucusunu kullanabilirsiniz. Microsoft ikili dosyaları için *pdb* dosyaları. | -   [Nasıl gösterilir: Komut satırına simge dosyası konumlarını belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Uygulamanın profilini oluşturun:** Bir hedef uygulamanın profilini oluşturmak için kullandığınız komut satırı araçları ve seçenekleri uygulamanın türüne, profil oluşturma yöntemine ve hedefin yönetilen mi yoksa yerel bir uygulama mı olduğuna bağlıdır. | -   [Komut satırı profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md) |
| **Raporlar .xml ve .csv oluşturun:** Komut isteminde profil oluşturma, arabiriminde görüntülen kolay veri dosyaları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturur. Ayrıca, 'i de üretin. *xml* veya virgülle ayrılmış değer (.** VSPerfReport komut satırı aracını kullanarak verilerin csv ) dosyaları. | -   [Komut satırına profil oluşturma raporları oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [Vsperfreport](../profiling/vsperfreport.md) |
| **Profili olmayan bilgisayarlarda profil Visual Studio:** Yüklü olmayan Profil Oluşturma Araçları verileri toplamak için tek başına profilleyiciyi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanabilirsiniz. | -   [Nasıl kurulur: Tek başına profilleyiciyi yükleme](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Başvuru
- [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
