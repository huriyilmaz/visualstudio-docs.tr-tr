---
title: Komut satırından Profil Oluşturma Araçları kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebd0fbabb73d4c77d1d888b207882e7403f46aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822691"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Komut Satırından Profil Oluşturma Araçlarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Komut isteminde uygulamalar profili oluşturmak ve toplu iş dosyalarını ve komut dosyalarını kullanarak profil oluşturmayı otomatikleştirmek için profil oluşturma araçları komut satırı araçlarını kullanabilirsiniz. Ayrıca, bir komut isteminde rapor dosyaları da oluşturabilirsiniz. Yüklü olmayan bilgisayarlarda veri toplamak için hafif tek başına profil oluşturucuyu kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Simgelerin konumunu ayarlayın:** İşlevlerin ve parametrelerin adlarını göstermek için profil oluşturucunun profili oluşturulmuş ikililerin sembol (. pdb) dosyalarına erişimi olmalıdır. Bu dosyalar, analizinizdeki görüntülemek istediğiniz Microsoft işletim sistemi ve uygulamaları için simge dosyalarını içermelidir. Microsoft ikilileri için doğru. pdb dosyalarına sahip olduğunuzdan emin olmak için genel Microsoft sembol sunucusu ' nu kullanabilirsiniz.|-   [Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Uygulamanızın profilini yapın:** Bir hedef uygulama profilini oluşturmak için kullandığınız komut satırı araçları ve seçenekleri uygulamanın türüne, profil oluşturma yöntemine ve hedefin yönetilen ya da yerel bir uygulama olup olmadığına bağlıdır.|-   [Komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)|  
|**. Xml ve. csv raporları oluşturun:** Komut isteminde profil oluşturma, için arabiriminde görüntülenebilen veri dosyaları oluşturur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . VSPerfReport komut satırı aracını kullanarak, verilerin. xml veya virgülle ayrılmış değer (. csv) dosyaları da oluşturabilirsiniz.|-   [Komut satırından profil Oluşturucu raporları oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Visual Studio olmadan bilgisayarlardaki profil kodu:** Yüklü olmayan bilgisayarlardaki uygulamalar için veri toplamak üzere Profil Oluşturma Araçları tek başına profil oluşturucuyu kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Nasıl yapılır: tek başına profil oluşturucuyu yüklemek](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Başvuru  
 [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)
