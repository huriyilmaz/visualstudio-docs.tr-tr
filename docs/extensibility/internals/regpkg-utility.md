---
title: RegPkg yardımcı programı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724442"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
> [!NOTE]
> Visual Studio 'da paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, VSıX dağıtımı için bir gereksinim olan sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur. Visual Studio paket dağıtımı hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını gönderme](../../extensibility/shipping-visual-studio-extensions.md).

 RegPkg. exe yardımcı programı, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir VSPackage kaydeder ve bunu dağıtıma hazırlar. Bu yardımcı program VSPackage geliştirme sırasında arka planda kullanılır. Deneysel Hive içinde VSPackage oluşturup çalıştırabilmeniz için yapı sürecinin bir parçası olarak çalışır.

 RegPkg, çeşitli biçimlerde sistem kayıt betikleri oluşturabilir. Bu komut dosyalarını. msi projeleri veya Windows Installer XML araç takımı dosyaları gibi dağıtım projelerinde ekleyebilirsiniz.

 RegPkg. exe genellikle \<*Visual STUDIO SDK yükleme yolunda*bulunur > \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg bu söz dizimini izler:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /Root: kök, belirtilen altında kayıt gerçekleştirir

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kök.

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