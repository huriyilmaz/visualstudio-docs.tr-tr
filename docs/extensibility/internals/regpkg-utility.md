---
title: RegPkg yardımcı programı | Microsoft Docs
description: RegPkg.exe yardımcı programının Visual Studio ile VSPackage 'a nasıl kaydolmasını ve dağıtıma hazırlanmasını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5160608379549abbd469bd6cf1c17e4357eac15
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060763"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
> [!NOTE]
> Visual Studio 'da paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, VSıX dağıtımı için bir gereksinim olan sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur. Visual Studio paket dağıtımı hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını gönderme](../../extensibility/shipping-visual-studio-extensions.md).

 RegPkg.exe yardımcı programı ile VSPackage kaydeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve bunu dağıtıma hazırlar. Bu yardımcı program VSPackage geliştirme sırasında arka planda kullanılır. Deneysel Hive içinde VSPackage oluşturup çalıştırabilmeniz için yapı sürecinin bir parçası olarak çalışır.

 RegPkg, çeşitli biçimlerde sistem kayıt betikleri oluşturabilir. Bu komut dosyalarını. msi projeleri veya Windows Installer XML araç takımı dosyaları gibi dağıtım projelerinde ekleyebilirsiniz.

 RegPkg.exe genellikle \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe bulunur. RegPkg bu söz dizimini izler:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /Root: kök, belirtilen altında kayıt gerçekleştirir

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Asıl.

 /regfile: FileName kayıt defterini güncelleştirmek yerine bir. reg dosyası oluşturur.  /Vrgfile veya/rgsfile veya/wixfile. ile birlikte kullanılamaz

 /rgsfile: FileName, kayıt defterini güncelleştirmek yerine bir. rgs dosyası oluşturur.  /Vrgfile veya/regfile veya/wixfile. ile birlikte kullanılamaz

 /vrgfile: FileName kayıt defterini güncelleştirmek yerine bir. VRG dosyası oluşturur.  /Regfile veya/rgsfile veya/wixfile. ile birlikte kullanılamaz

 /RGM, RGS dosyasına ek olarak bir. RGM dosyası oluşturur.  /Rgsfileile birleştirilmelidir.

 /wixfile: FileName, kayıt defterini güncelleştirmek yerine Windows Installer XML araç takımı ile uyumlu bir dosya oluşturur.  ,/Regfile veya/rgsfile veya/vrgfileile kullanılamaz.

 /CodeBase derleme yerine kod temeli ile kaydolmayı zorlar.

 /Assembly kod temeli yerine derlemeyle kaydolmayı zorlar.

 /Unregister bu paketin kaydını siler.  Kullanılamaz

 /regfile veya/vrgfile veya/rgsfile veya/wixfile. ile

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
