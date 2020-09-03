---
title: 'Hata: Web sunucusunda hata ayıklama başlatılamıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185478"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web sunucusunda çalışan bir ASP.NET uygulamasında hata ayıklamaya çalıştığınızda şu hata iletisini alabilirsiniz: Web sunucusunda hata ayıklama başlatılamıyor.
  
Çoğu durumda, IIS düzgün yapılandırılmadığı için bu hata oluşur.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> IIS yapılandırmanızı denetleyin

Burada ayrıntılı bir sorunu çözmeye yönelik adımları uyguladıktan sonra ve hata ayıklamayı yeniden denemeden önce, IIS 'yi de sıfırlamanız gerekebilir. Bunu, bir yönetici komut istemi açıp yazarak yapabilir ya da bunu `iisreset` IIS Yöneticisi 'nde yapabilirsiniz. 

* Uygulama havuzlarınızı durdurup yeniden başlatın ve yeniden deneyin.

    Uygulama havuzu durdurulmuş olabilir veya yaptığınız başka bir yapılandırma değişikliği, uygulama havuzunuzu durdurup yeniden başlatmanızı gerektirebilir.
    
    > [!NOTE]
    > Uygulama havuzu durmaya devam ederse, Denetim Masası 'ndan URL yeniden yazma modülünü kaldırmanız ve ardından Web Platformu Yükleyicisi 'ni (WPı) kullanarak yeniden yüklemeniz gerekebilir. Bu, önemli bir sistem yükseltmesinden sonra bir sorun olabilir.

* Uygulama havuzu yapılandırmanızı denetleyin, gerekirse düzeltin ve yeniden deneyin.

    Parola kimlik bilgileri değiştiyse, bunları uygulama havuzunuzdaki güncelleştirmeniz gerekebilir. Ayrıca, ASP.NET son zamanlarda yüklediyseniz, uygulama havuzu yanlış ASP.NET sürümü için yapılandırılmış olabilir. Sorunu giderip uygulama havuzunu yeniden başlatın.
    
* Web uygulaması klasörünüzün doğru izinlere sahip olup olmadığını denetleyin.

    Web uygulaması klasörü için IIS_IUSRS veya ıUSR (ya da uygulama havuzuyla ilişkili belirli bir Kullanıcı) okuma ve yürütme haklarına sahip olduğunuzdan emin olun. Sorunu giderip uygulama havuzunuzu yeniden başlatın.

* Yerel adreslerle bir HOSTS dosyası kullanıyorsanız, makinenin IP adresi yerine geri döngü adresini kullanmayı deneyin.

* Tarayıcıda localhost sayfasını açın.

     IIS düzgün yüklenmemişse, bir tarayıcıya yazarken hata almanız gerekir `http://localhost` .
     
     IIS 'ye dağıtma hakkında daha fazla bilgi için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya ASP.NET Core, [IIS 'ye yayımlama](https://docs.asp.net/en/latest/publishing/iis.html)).

* IIS 'de doğru ASP.NET sürümünün yüklü olduğundan emin olun.  Bkz. [ASP.NET uygulamasını dağıtma](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) veya ASP.NET Core, [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html)).

* Sunucuda temel bir ASP.NET uygulaması oluşturun.

     Uygulamanızı hata ayıklayıcıyla çalışacak şekilde alamazsanız, sunucuda yerel olarak temel bir ASP.NET uygulaması oluşturmayı deneyin ve temel uygulamada hata ayıklamayı deneyin. Temel bir uygulamada hata ayıklaması yapabiliyorsanız, bu iki yapılandırma arasında nelerin farklı olduğunu belirlemenize yardımcı olabilir.
  
* Yalnızca IP adresini kullanıyorsanız kimlik doğrulama hatalarını çözün

     Varsayılan olarak, IP adreslerinin Internet 'in bir parçası olduğu varsayılır ve NTLM kimlik doğrulaması Internet üzerinden yapılmaz. Web siteniz IIS 'de kimlik doğrulaması gerektirecek şekilde yapılandırıldıysa, bu kimlik doğrulaması başarısız olur. Bu sorunu düzeltmek için IP adresi yerine uzak bilgisayarın adını belirtebilirsiniz.
     
## <a name="other-causes"></a>Diğer nedenler

Visual Studio 'nun eski bir sürümünü kullanıyorsanız:

- Visual Studio 'Yu yükseltilmiş ayrıcalıklarla yeniden başlatın ve yeniden deneyin.

    Eski sürümlerde (daha sonra düzeltilen) bir hata, bazı ASP.NET hata ayıklama senaryolarında yükseltilmiş ayrıcalıklar gerektirir.
    
- Visual Studio 'nun birden çok örneği çalışıyorsa, projenizi Visual Studio 'nun bir örneğinde yeniden açın ve yeniden deneyin.

## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
