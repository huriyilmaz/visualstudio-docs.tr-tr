---
title: dağıtılan ASP.NET uygulamalarında hata ayıklama | Microsoft Docs
description: çalışan işleme ekleyerek ve hata ayıklayıcının uygulama simgelerine yönelik simgelere erişmesine olanak sağlayarak dağıtılan bir ASP.NET uygulamasının hatalarını ayıklamak için Visual Studio kullanın.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 0190d563dab26ee89a157cf4a997a53b8d8f3ae9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097615"
---
# <a name="debugging-deployed-aspnet-applications"></a>dağıtılan ASP.NET uygulamalarında hata ayıklama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Dağıtılan bir uygulamada hata ayıklamak için kullanmak üzere, çalışan işleme iliştirmeli [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve hata ayıklayıcının uygulama için simgelere erişimi olduğundan emin olmanız gerekir. Ayrıca, uygulamanın kaynak dosyalarını bulup açmanız gerekir. daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [nasıl yapılır: ASP.NET işlemin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)ve [sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Hata ayıklama için çalışan işleme iliştirmiş ve bir kesme noktasına ulaşırsanız, çalışan işlemindeki tüm yönetilen kodlar. Çalışan işlemdeki tüm yönetilen kodların kilitlenmesine, sunucudaki tüm kullanıcılar için bir iş durdurma sayfasına neden olabilir. Bir üretim sunucusunda hata ayıklamadan önce, üretim işlerinde olası etkiyi göz önünde bulundurun.

Çalışan işleme ekleme işlemi, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] başka bir uzak işleme iliştirme ile aynıdır. İliştirdikten sonra, doğru proje açık değilse, uygulama kesildiğinde bir iletişim kutusu görünür. Bu iletişim kutusu, uygulamanın kaynak dosyalarının konumunu sorar. İletişim kutusunda belirttiğiniz dosya adı, Web sunucusundaki hata ayıklama sembollerinde belirtilen dosya adıyla aynı olmalıdır. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). ııs 'de uzaktan hata ayıklamayı ayarlamak için, bkz. uzaktan [hata ayıklama ASP.NET uzak bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Birçok [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması, iş mantığını veya diğer yararlı kodu Içeren dll 'lere başvurur. Bu tür bir başvuru, uygulamanızı dağıtırken yerel bilgisayarınızdaki DLL 'yi Web uygulamasının sanal dizininin \bin klasörüne kopyalar. Hata ayıklarken, Web uygulamanızın yerel bilgisayarınızdaki kopya değil, DLL 'nin kopyasına başvurduğundan emin olabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarda hata ayıkla](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Nasıl Yapılır: ASP.NET Uygulamaları için Hata Ayıklamayı Etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [nasıl yapılır: ASP.NET işlemin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)