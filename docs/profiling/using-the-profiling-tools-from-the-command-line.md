---
title: Komut satırından Profil Oluşturma Araçları kullanma | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778043"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Komut satırından Profil Oluşturma Araçları kullanın
Komut isteminde uygulamalar profili oluşturmak ve toplu iş dosyalarını ve komut dosyalarını kullanarak profil oluşturmayı otomatikleştirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarını kullanabilirsiniz. Ayrıca, bir komut isteminde rapor dosyaları da oluşturabilirsiniz. Hafif tek başına profil oluşturucuyu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü olmayan bilgisayarlarda veri toplamak için kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

| Görev | İlgili Içerik |
| - | - |
| **Simgelerin konumunu ayarlayın:** İşlevlerin ve parametrelerin adlarını göstermek için, profil oluşturucunun simgeye erişimi olmalıdır (. *pdb*) dosyaları profili oluşturulmuş ikililer. Bu dosyalar, analizinizdeki görüntülemek istediğiniz Microsoft işletim sistemi ve uygulamaları için simge dosyalarını içermelidir. Doğru olduğundan emin olmak için genel Microsoft sembol sunucusu ' nu kullanabilirsiniz. Microsoft ikilileri için *pdb* dosyaları. | -   [nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Uygulamanızın profilini yapın:** Bir hedef uygulama profilini oluşturmak için kullandığınız komut satırı araçları ve seçenekleri uygulamanın türüne, profil oluşturma yöntemine ve hedefin yönetilen ya da yerel bir uygulama olup olmadığına bağlıdır. | -   [profil oluşturma yöntemlerini komut satırından kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />[tek başına uygulamalar -   profili](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [profili ASP.NET Web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [profili Hizmetleri](../profiling/command-line-profiling-of-services.md) |
| **. Xml ve. csv raporları oluşturun:** Komut isteminde profil oluşturma, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]için arabirimde görüntülenebilen veri dosyaları oluşturur. Ayrıca oluşturabilirsiniz. *XML* veya virgülle ayrılmış değer (. *CSV*) VSPerfReport komut satırı aracını kullanarak veri dosyaları. | [komut satırından profil Oluşturucu raporları -   oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />[VSPerfReport](../profiling/vsperfreport.md) -    |
| **Visual Studio olmadan bilgisayarlardaki profil kodu:** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü olmayan bilgisayarlardaki uygulamalar için veri toplamak üzere Profil Oluşturma Araçları tek başına profil oluşturucuyu kullanabilirsiniz. | -   [nasıl yapılır: tek başına profil oluşturucuyu yüklemeyi](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Başvuru
- [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
