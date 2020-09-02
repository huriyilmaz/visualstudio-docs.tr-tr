---
title: RegPkg yardımcı programı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819776"
---
# <a name="regpkg-utility"></a>RegPkg Yardımcı Programı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Visual Studio 'da paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, VSıX dağıtımı için bir gereksinim olan sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur. Visual Studio paket dağıtımı hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını gönderme](../../extensibility/shipping-visual-studio-extensions.md).  
  
 RegPkg.exe yardımcı programı ile VSPackage kaydeder [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve bunu dağıtıma hazırlar. Bu yardımcı program VSPackage geliştirme sırasında arka planda kullanılır. Deneysel Hive içinde VSPackage oluşturup çalıştırabilmeniz için yapı sürecinin bir parçası olarak çalışır.  
  
 RegPkg, çeşitli biçimlerde sistem kayıt betikleri oluşturabilir. Bu komut dosyalarını. msi projeleri veya Windows Installer XML araç takımı dosyaları gibi dağıtım projelerinde ekleyebilirsiniz.  
  
 RegPkg.exe genellikle \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe bulunur. RegPkg bu söz dizimini izler:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /Root: kök  
 Belirtilen kayıt işlemini gerçekleştirir  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Asıl.  
  
 /regfile: dosya adı  
 Kayıt defterini güncelleştirmek yerine bir. reg dosyası oluşturur.  /Vrgfile veya/rgsfile veya/wixfile. ile birlikte kullanılamaz  
  
 /rgsfile: dosya adı  
 Kayıt defterini güncelleştirmek yerine bir. rgs dosyası oluşturur.  /Vrgfile veya/regfile veya/wixfile. ile birlikte kullanılamaz  
  
 /vrgfile: dosya adı  
 Kayıt defterini güncelleştirmek yerine bir. VRG dosyası oluşturur.  /Regfile veya/rgsfile veya/wixfile. ile birlikte kullanılamaz  
  
 /RGM  
 RGS dosyasına ek olarak bir. RGM dosyası oluşturur.  /Rgsfileile birleştirilmelidir.  
  
 /wixfile: dosya adı  
 Kayıt defterini güncelleştirmek yerine, Windows Installer XML araç takımı ile uyumlu bir dosya oluşturur.  ,/Regfile veya/rgsfile veya/vrgfileile kullanılamaz.  
  
 /codebase  
 Derlemeyi derleme yerine kod temeli ile zorlar.  
  
 /Assembly  
 Kod temeli yerine derlemeyle kayıt işlemini zorlar.  
  
 türlerin  
 Bu paketin kaydını siler.  Kullanılamaz  
  
 /regfile veya/vrgfile veya/rgsfile veya/wixfile. ile  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir ürünü serbest bırakma](../../misc/releasing-a-visual-studio-integration-product.md)   
 [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
