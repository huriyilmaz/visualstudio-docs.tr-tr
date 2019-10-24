---
title: Dağıtılan ASP.NET uygulamalarında hata ayıklama | Microsoft Docs
ms.date: 06/30/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: c2b1838375ee878640d77a9c93808efafc9f519c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738296"
---
# <a name="debugging-deployed-aspnet-applications"></a>Dağıtılan ASP.NET uygulamalarında hata ayıklama
Dağıtılan bir uygulamada hata ayıklamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanmak için, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemine iliştirmeli ve hata ayıklayıcının uygulama için simgelere erişimi olduğundan emin olmanız gerekir. Ayrıca, uygulamanın kaynak dosyalarını bulup açmanız gerekir. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)ve [sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Hata ayıklama için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemine iliştirmiş ve bir kesme noktasına ulaşırsanız, çalışan işlemindeki tüm yönetilen kodlar durur. Çalışan işlemdeki tüm yönetilen kodların kilitlenmesine, sunucudaki tüm kullanıcılar için bir iş durdurma sayfasına neden olabilir. Bir üretim sunucusunda hata ayıklamadan önce, üretim işlerinde olası etkiyi göz önünde bulundurun.

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemine ekleme işlemi, başka bir uzak işleme iliştirme ile aynıdır. İliştirdikten sonra, doğru proje açık değilse, uygulama kesildiğinde bir iletişim kutusu görünür. Bu iletişim kutusu, uygulamanın kaynak dosyalarının konumunu sorar. İletişim kutusunda belirttiğiniz dosya adı, Web sunucusundaki hata ayıklama sembollerinde belirtilen dosya adıyla aynı olmalıdır. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). IIS 'de uzaktan hata ayıklamayı ayarlamak için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Birçok [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması, iş mantığını veya diğer yararlı kodu içeren dll 'Lere başvurur. Bu tür bir başvuru, uygulamanızı dağıtırken yerel bilgisayarınızdaki DLL 'yi Web uygulamasının sanal dizininin \bin klasörüne kopyalar. Hata ayıklarken, Web uygulamanızın yerel bilgisayarınızdaki kopya değil, DLL 'nin kopyasına başvurduğundan emin olabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Nasıl Yapılır: ASP.NET Uygulamaları için Hata Ayıklamayı Etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Nasıl Yapılır: ASP.NET İşleminin Adını Bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)