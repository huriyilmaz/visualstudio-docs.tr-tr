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
ms.openlocfilehash: 7911c31b6e7766d69e51b65abea8184f4d6fbbdc8d2518560b13d665c365e61f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432234"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
> [!NOTE]
> Paketleri uygulama içinde kaydetmenin tercih Visual Studio .pkgdef dosyalarını kullanmaktır. Bu, VSIX dağıtımı için bir gereksinim olan sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına olanak sağlar. Pkgdef dosyaları, [CreatePkgDef Yardımcı Programı kullanılarak oluşturulur.](../../extensibility/internals/createpkgdef-utility.md) Paket dağıtımı hakkında daha Visual Studio için bkz. [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md).

 RegPkg.exe yardımcı programı bir VSPackage'i ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydeden ve dağıtım için hazırlar. Bu yardımcı program, VSPackage geliştirme sırasında arka planı kullanılır. Deneysel hive'da VSPackage derlemek ve çalıştırmak için derleme işleminin bir parçası olarak çalışır.

 RegPkg çeşitli biçimlerde sistem kayıt defteri betikleri oluşturabilirsiniz. Bu betikleri, .msi veya Windows YükleyiciSI XML Araç Seti dosyaları gibi dağıtım projelerine dahil edin.

 RegPkg.exe genellikle \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg şu söz dizimlerini izler:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Belirtilen kök altında kaydı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerçekleştirir.

 /regfile:FileName Kayıt defterini güncelleştirmek yerine bir .reg dosyası oluşturur.  /vrgfile, /rgsfile veya /wixfile ile kullanılamaz.

 /rgsfile:FileName Kayıt defterini güncelleştirmek yerine bir .rgs dosyası oluşturur.  /vrgfile, /regfile veya /wixfile ile kullanılamaz.

 /vrgfile:FileName Kayıt defterini güncelleştirmek yerine bir .vrg dosyası oluşturur.  /regfile, /rgsfile veya /wixfile ile kullanılamaz.

 /rgm rgs dosyasına ek olarak bir .rgm dosyası oluşturur.  /rgsfile ile birleştirildi.

 /wixfile:FileName Kayıt defterini güncelleştirmek Windows Yükleyici XML Araç Seti ile uyumlu bir dosya oluşturur.  /regfile, /rgsfile veya /vrgfile ile kullanılamaz.

 /codebase Derleme yerine CodeBase ile kaydı zorlar.

 /assembly CodeBase yerine Assembly ile kaydı zorlar.

 /unregister Unregisters this package.  Kullanılamaz

 /regfile veya /vrgfile, /rgsfile veya /wixfile ile.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
