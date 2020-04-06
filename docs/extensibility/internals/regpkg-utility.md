---
title: RegPkg Yardımcı Programı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705646"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
> [!NOTE]
> Visual Studio'da paketleri kaydetmenin tercih edilen yolu .pkgdef dosyalarını kullanmaktır. Bu, VSIX dağıtımı için bir gereklilik olan sistem kayıt defterine erişmek zorunda kalmadan uzatma dağıtımına olanak tanır. Pkgdef dosyaları [CreatePkgDef Yardımcı Programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur. Visual Studio paket dağıtımı hakkında daha fazla bilgi için, [Görsel Stüdyo Uzantıları Gönderim](../../extensibility/shipping-visual-studio-extensions.md)bakın.

 RegPkg.exe yardımcı programı bir VSPackage ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydeder ve dağıtım için hazırlar. Bu yardımcı program VSPackage geliştirme sırasında sahne arkasında kullanılır. Deneysel kovanda bir VSPackage oluşturup çalıştırabilmeniz için yapı sürecinin bir parçası olarak çalışır.

 RegPkg çeşitli biçimlerde sistem kayıt defteri komut dosyaları oluşturabilir. Bu komut dosyalarını .msi projeleri veya Windows Installer XML Toolset dosyaları gibi dağıtım projelerine dahil edebilirsiniz.

 RegPkg.exe genellikle \< *Visual Studio SDK yükleme yolu*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe bulunur. RegPkg bu sözdizimini izler:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Belirtilen altında kayıt gerçekleştirir

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kök.

 /regfile:FileName kayıt defterini güncelleştirmek yerine bir .reg dosyası oluşturur.  /vrgfile veya /rgsfile veya /wixfile ile kullanılamaz.

 /rgsfile:FileName kayıt defterini güncelleştirmek yerine bir .rgs dosyası oluşturur.  /vrgfile veya /regfile veya /wixfile ile kullanılamaz.

 /vrgfile:FileName kayıt defterini güncelleştirmek yerine bir .vrg dosyası oluşturur.  /regfile veya /rgsfile veya /wixfile ile kullanılamaz.

 /rgm rgs dosyasına ek olarak bir .rgm dosyası oluşturur.  /rgsfile ile birleştirilmelidir.

 /wixfile:FileName, kayıt defterini güncelleştirmek yerine Windows Installer XML Toolset uyumlu bir dosya oluşturur.  /regfile veya /rgsfile veya /vrgfile ile kullanılamaz.

 /codebase Forces Assembly yerine CodeBase ile kayıt.

 /assembly Forces CodeBase yerine Assembly'e kayıt yaptırın.

 /unregister bu paketi kayıt dışı.  Kullanılamaz

 /regfile veya /vrgfile veya /rgsfile veya /wixfile ile.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
