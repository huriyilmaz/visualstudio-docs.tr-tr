---
title: VSPackage için Kurulum Dizini Seçimi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709757"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage için kurulum dizinini seçin
VSPackage ve destekleyici dosyaları bir kullanıcının dosya sisteminde olmalıdır. Konumu VSPackage yönetilen veya yönetilmeyen, yan yana sürüm düzeni ve kullanıcı seçimi bağlıdır.

## <a name="unmanaged-vspackages"></a>Yönetilmeyen VSPackages
 Yönetilmeyen VSPackage, herhangi bir konuma yüklenebilen bir COM sunucusudur. Kayıt bilgileri konumunu doğru bir şekilde yansıtmalıdır. Yükleyici kullanıcı arabirimi (UI) `ProgramFilesFolder` Windows Installer özellik değerinin bir alt dizini olarak varsayılan bir konum sağlamalıdır. Örnek:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;\V1.0\\*

 Kullanıcı, küçük bir önyükleme bölümü tutan ve uygulamaları ve araçları başka bir ses düzeyine yüklemeyi tercih eden kullanıcıları barındırmak için varsayılan dizini değiştirmesine izin verilmelidir.

 Yan yana şemanınız da sürümlü vspackage kullanıyorsa, farklı sürümleri depolamak için alt dizinler kullanabilirsiniz. Örnek:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Yönetilen VSPackages
 Yönetilen VSPackages herhangi bir konuma da yüklenebilir. Ancak, montaj yükleme sürelerini azaltmak için bunları her zaman genel montaj önbelleğine (GAC) yüklemeyi düşünmelisiniz. Yönetilen VSPackages her zaman güçlü adlandırılmış derlemeler olduğundan, bunları GAC'ye yüklemek, güçlü ad imza doğrulamalarının yalnızca yükleme zamanında olduğu anlamına gelir. Dosya sisteminin başka bir yerinde yüklü olan güçlü adlandırılmış derlemelerin, her yüklendiklerinde imzalarının doğrulanmış olması gerekir. YÖNETILEN VSPackages'i GAC'ye yüklediğinizde, derlemenin güçlü adını gösteren kayıt defteri girişleri yazmak için regpkg aracının **/derleme** anahtarını kullanın.

 Yönetilen VSPackages'ı GAC dışında bir konuma yüklerseniz, dizin hiyerarşilerini seçmek için yönetilmeyen VSPackages için verilen önceki tavsiyelere uyun. VSPackage derlemesinin yolunu gösteren kayıt defteri girişlerini yazmak için regpkg aracının **/codebase** anahtarını kullanın.

 Daha fazla bilgi için [bkz.](../../extensibility/registering-and-unregistering-vspackages.md)

## <a name="satellite-dlls"></a>Uydu DLL'leri
 Sözleşmeye göre, belirli bir yerel alan için kaynak içeren VSPackage uydu DL'leri, *VSPackage* dizininin alt dizinlerinde bulunur. Alt dizinler yerel kimlik (LCID) değerlerine karşılık gelir.

 [VSPackages yönet](../../extensibility/managing-vspackages.md) makalesi, kayıt defteri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] girişlerinin vspackage uydusu DLL'yi gerçekte nerede aradığını kontrol ettiğini gösterir. Ancak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aşağıdaki sırada, bir LCID değeri için adlandırılmış bir alt dizine bir uydu DLL yüklemeye çalışır:

1. Varsayılan LCID (Visual Studio LCID; örneğin, İngilizce için *\1033)*

2. Varsayılan alt dil ile Varsayılan LCID.

3. Sistem varsayılan LCID.

4. Varsayılan alt dil ile sistem varsayılan LCID.

5. ABD İngilizcesi (*.\1033* veya *.\0x409*).

VSPackage DLL'niz kaynakları içeriyorsa ve **SatelliteDll\DllName** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt defteri giriş noktaları bu kaynakları içeriyorsa, bunları yukarıdaki sırada yüklemeye çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
- [Paket kaydını yönetme](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
