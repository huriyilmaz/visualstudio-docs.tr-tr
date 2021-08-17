---
title: RegPkg Yardımcı Programı | Microsoft Docs
description: RegPkg.exe yardımcı Visual Studio vsPackage'Visual Studio dağıtım için hazırlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ed91788526177392901a6fd8aa03f139f9267827
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062855"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
> [!NOTE]
> Paketleri uygulama içinde kaydetmenin tercih Visual Studio .pkgdef dosyalarını kullanmaktır. Bu, VSIX dağıtımı için bir gereksinim olan sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına olanak sağlar. Pkgdef dosyaları [CreatePkgDef Yardımcı Programı kullanılarak oluşturulur.](../../extensibility/internals/createpkgdef-utility.md) Paket dağıtımı hakkında daha fazla Visual Studio için bkz. [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md).

 RegPkg.exe yardımcı programı ile bir VSPackage'i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydeden ve dağıtım için hazırlar. Bu yardımcı program VSPackage geliştirmesi sırasında arka planı kullanılır. Deneysel hive'da VSPackage derlemek ve çalıştırmak için derleme işleminin bir parçası olarak çalışır.

 RegPkg çeşitli biçimlerde sistem kayıt defteri betikleri oluşturabilirsiniz. Bu betikleri, .msi veya Windows YükleyiciSI XML Araç Seti dosyaları gibi dağıtım projelerine dahil edin.

 RegPkg.exe genellikle \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg şu söz dizimlerini izler:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Belirtilen kök altında kaydı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerçekleştirir.

 /regfile:FileName Kayıt defterini güncelleştirmek yerine bir .reg dosyası oluşturur.  /vrgfile, /rgsfile veya /wixfile ile kullanılamaz.

 /rgsfile:FileName Kayıt defterini güncelleştirmek yerine bir .rgs dosyası oluşturur.  /vrgfile, /regfile veya /wixfile ile kullanılamaz.

 /vrgfile:FileName Kayıt defterini güncelleştirmek yerine bir .vrg dosyası oluşturur.  /regfile, /rgsfile veya /wixfile ile kullanılamaz.

 /rgm rgs dosyasına ek olarak bir .rgm dosyası oluşturur.  /rgsfile ile birleştirilmiş olması gerekir.

 /wixfile:FileName Kayıt defterini güncelleştirmek Windows Yükleyici XML Araç Seti ile uyumlu bir dosya oluşturur.  /regfile, /rgsfile veya /vrgfile ile kullanılamaz.

 /codebase Derleme yerine CodeBase ile kaydı zorlar.

 /assembly CodeBase yerine Assembly ile kaydı zorlar.

 /unregister Unregisters this package.  Kullanılamaz

 /regfile veya /vrgfile, /rgsfile veya /wixfile ile.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
