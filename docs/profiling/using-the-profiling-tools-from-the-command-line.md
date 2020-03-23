---
title: Komut Satırından Profil Oluşturma Araçlarını Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1420aa9f92e8ef7564478499c78393510ad61c23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778043"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Komut satırındaki Profil Oluşturma Araçlarını kullanma
Profil Oluşturma Araçları'nın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut satırı araçlarını, komut istemindeki uygulamaları profillemek ve toplu dosya ve komut dosyası kullanarak profil oluşturmayı otomatikleştirmek için kullanabilirsiniz. Ayrıca, bir komut isteminde rapor dosyaları oluşturabilirsiniz. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yüklü olmayan bilgisayarlarda veri toplamak için hafif tek başına profil oluşturucuyu kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Sembollerin konumunu ayarlayın:** Işlevlerin ve parametrelerin adlarını görüntülemek için profil oluşturucunun simgeye erişimi olmalıdır (.* pdb*) profilli ikili dosyaların dosyaları. Bu dosyalar, Microsoft işletim sistemi için sembol dosyalarını ve çözümlemenizde görüntülemek istediğiniz uygulamaları içermelidir. Microsoft sembol sunucusunu kullanarak doğru sunucuya sahip olduğunuzu emin olabilirsiniz. Microsoft ikilileri için *pdb* dosyaları. | -   [Nasıl kullanılır: Komut satırından sembol dosya konumlarını belirtin](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Uygulamanızın profilini:** Hedef uygulamayı profillemek için kullandığınız komut satırı araçları ve seçenekleri, uygulamanın türüne, profil oluşturma yöntemine ve hedefin yönetilen veya yerel bir uygulama olup olmadığına bağlıdır. | -   [Komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md) |
| **.xml ve .csv raporları oluşturun:** Komut isteminde profil oluşturma, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]arayüz'te görüntülenebilen veri dosyaları oluşturur. Ayrıca oluşturabilirsiniz. *xml* veya virgülden ayrılmış değer (.* csv*) vsPerfReport komut satırı aracını kullanarak verilerin dosyaları. | -   [Komut satırından profil oluşturraporları oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [Vsperfreport](../profiling/vsperfreport.md) |
| **Visual Studio olmayan bilgisayarlarda profil kodu:** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yüklü olmayan bilgisayarlardaki uygulamalar için veri toplamak için Profil Oluşturma Araçları'nı tek başına profil oluşturma aracını kullanabilirsiniz. | -   [Nasıl yapılır: Tek başına profil oluşturucuyu yükleyin](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Başvuru
- [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
