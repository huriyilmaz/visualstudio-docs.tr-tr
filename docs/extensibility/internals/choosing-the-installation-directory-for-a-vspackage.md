---
title: VSPackage Paketi için Yükleme Dizinini | Microsoft Docs
description: Yönetilen mi yoksa yönetilemeyen mi olduğu gibi faktörleri kullanarak VSPackage için yükleme dizinini ve destek dosyalarını seçmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: bde953b023b91c3c3e3b06fb3d50770851352da9d441b6277406ed91bbc392a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359734"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage için yükleme dizinini seçme
VSPackage ve destek dosyaları kullanıcının dosya sisteminde bulunarak kullanılabilir. Konum, VSPackage'ın yönetilip yönetilemeyen bir model olup olmadığı, yan yana sürüm oluşturma düzeninize ve kullanıcı seçiminize bağlıdır.

## <a name="unmanaged-vspackages"></a>Unmanaged VSPackages
 Unmanaged VSPackage, herhangi bir konuma yüklenemeyen bir COM sunucusudur. Kayıt bilgileri konumunu doğru bir şekilde yansıtmalı. Yükleyici kullanıcı arabiriminiz (UI), Yükleyici özellik değerinin alt dizini olarak `ProgramFilesFolder` varsayılan Windows sağlaydır. Örnek:

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \V1.0\\*

 Kullanıcının, küçük bir önyükleme bölümünü saklayan ve başka birimde uygulama ve araç yüklemeyi tercih eden kullanıcılara uyum sağlayacak şekilde varsayılan dizini değiştirmesine izin verilmiyor.

 Yan yana düzeniniz sürüme sahip bir VSPackage kullanıyorsa, farklı sürümleri depolamak için alt dizinleri kullanabilirsiniz. Örnek:

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \\ V1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>Yönetilen VSPackage'lar
 Yönetilen VSPackage'lar herhangi bir konuma da yüklenebilirsiniz. Ancak, derleme yükleme sürelerini azaltmak için bunları her zaman genel derleme önbelleğine (GAC) yüklemeyi düşünebilirsiniz. Yönetilen VSPackage'lar her zaman güçlü adlandırılmış derlemeler olduğundan, bunları GAC'ye yüklemek, bunların güçlü ad imza doğrulamasının yalnızca yükleme zamanında olduğu anlamına gelir. Dosya sisteminin başka bir yerinde yüklü olan güçlü adlandırılmış derlemeler, her yüklendiğinde imzalarının doğrulanmış olması gerekir. GAC'ye yönetilen VSPackage'ları yükleyebilirsiniz. Derlemenin güçlü adına işaret ediyor kayıt defteri girdilerini yazmak için regpkg aracının **/assembly** anahtarını kullanın.

 Yönetilen VSPackage'ları GAC dışında bir konuma yüklürsanız, dizin hiyerarşileri seçmek için yönetilemeyen VSPackage'lar için verilen önceki öneriyi izleyin. VSPackage derlemesi yolunu işaret alan kayıt defteri girdileri yazmak için regpkg aracının **/codebase** anahtarını kullanın.

 Daha fazla bilgi için [bkz. VSPackage'ları kaydetme ve kaydını çıkarma.](../../extensibility/registering-and-unregistering-vspackages.md)

## <a name="satellite-dlls"></a>Uydu DLL'leri
 Kural gereği, belirli bir yerele yönelik kaynakları içeren VSPackage uydu DLL'leri *VSPackage* dizininin alt dizinlerinde bulunur. Alt dizinler yerel kimlik (LCID) değerlerine karşılık gelen.

 [VSPackage'ları Yönetme](../../extensibility/managing-vspackages.md) makalesi, kayıt defteri girdilerinin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ın uydu DLL'sini nerede araması gerektirse de denetlemesi olduğunu gösterir. Ancak, aşağıdaki sırayla bir LCID değeri için adlı alt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dizinde bir uydu DLL'leri yüklemeye çalışır:

1. Varsayılan LCID (Visual Studio LCID; örneğin, *\1033* İngilizce)

2. Varsayılan alt dil ile varsayılan LCID.

3. Sistem varsayılan LCID'i.

4. Varsayılan alt dil ile sistem varsayılan LCID'i.

5. ABD İngilizcesi (*.\1033* veya *.\0x409*).

VSPackage DLL'niz kaynaklara sahipse ve **SatelliteDll\DllName** kayıt defteri giriş noktası varsa, bunları yukarıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sırayla yükleme girişiminde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürüme sahip VSPackage'lar arasında seçim](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [Paket kaydını yönetme](/previous-versions/bb166783(v=vs.100))