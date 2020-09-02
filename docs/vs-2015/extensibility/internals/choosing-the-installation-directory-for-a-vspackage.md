---
title: VSPackage için yükleme dizinini seçme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697239"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>VSPackage için Yükleme Dizinini Seçme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir VSPackage ve destekleyici dosyaları bir kullanıcının dosya sisteminde olmalıdır. Konum, VSPackage 'ın yönetilip yönetilmediğini, yan yana sürüm oluşturma şemanızın ve Kullanıcı tercihinizin olup olmamasına bağlıdır.  
  
## <a name="unmanaged-vspackages"></a>Yönetilmeyen VSPackages  
 Yönetilmeyen VSPackage, herhangi bir konuma yüklenebilen bir COM sunucusudur. Kayıt bilgileri, konumunu doğru şekilde yansıtmalıdır. Yükleyici Kullanıcı arabiriminiz (UI), ProgramFilesFolder Windows Installer özelliğinin alt dizini olarak varsayılan bir konum sağlamalıdır. Örneğin:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\  
  
 Kullanıcının küçük bir önyükleme bölümünü tutan ve başka bir birime uygulama ve araç yüklemeyi tercih ettiği kullanıcılara uyum sağlaması için varsayılan dizini değiştirmesine izin verilmelidir.  
  
 Yan yana şemanızın sürümü sürümlü bir VSPackage kullanıyorsa, farklı sürümleri depolamak için alt dizinleri kullanabilirsiniz. Örneğin:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Yönetilen VSPackages  
 Yönetilen VSPackages, herhangi bir konuma de yüklenebilir. Ancak, derleme yükleme sürelerini azaltmak için bunları her zaman genel derleme önbelleği 'ne (GAC) yüklemeyi düşünmelisiniz. Yönetilen VSPackages, her zaman güçlü adlandırılmış derlemeler olduğundan, bunları GAC 'ye yüklemek, tanımlayıcı ad imzası doğrulamanın yalnızca yükleme sırasında aldığı anlamına gelir. Dosya sisteminde başka bir yerde yüklü olan güçlü adlandırılmış derlemelerin imzaları her yüklenilişinde bunların doğrulanması gerekir. GAC 'de Yönetilen VSPackages yüklediğinizde, derlemenin tanımlayıcı adına işaret eden kayıt defteri girişlerini yazmak için RegPkg aracının **/Assembly** anahtarını kullanın.  
  
 Yönetilen VSPackages 'yi GAC dışında bir konuma yüklerseniz, Dizin hiyerarşilerini seçmek için Yönetilmeyen VSPackages için verilen önceki önerileri izleyin. VSPackage derlemesinin yolunu işaret eden kayıt defteri girişlerini yazmak için RegPkg aracının **/CODEBASE** anahtarını kullanın.  
  
 Daha fazla bilgi için bkz. [VSPackages kaydetme ve kaydını silme](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Uydu DLL'leri  
 Kural gereği, belirli bir yerel ayara yönelik kaynakları içeren VSPackage uydu dll 'Leri VSPackage dizininin alt dizinlerinde bulunur. Alt dizinler yerel ayar KIMLIĞI (LCıD) değerlerine karşılık gelir.  
  
 [VSPackages 'Yi yönetmek](../../extensibility/managing-vspackages.md) , kayıt defteri girdilerinin [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gerçekten bir VSPackage uydu dll 'sinin nerede göründüğünü denetler. Ancak, bir kültür DLL 'sini bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] LCID değeri için adlı bir alt dizine aşağıdaki sırayla yüklemeye çalışır:  
  
1. Varsayılan LCıD (1033 Örneğin, Ingilizce için VS LCıD)  
  
2. Varsayılan alt dille varsayılan LCıD.  
  
3. Sistem varsayılan LCıD 'SI.  
  
4. Varsayılan alt dille sistem varsayılan LCıD 'SI.  
  
5. ABD Ingilizcesi (. \ 1033 veya .\0x409).  
  
   VSPackage DLL 'niz kaynakları içeriyorsa ve SatelliteDll\DllName kayıt defteri girişi işaret ediyorsa, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bunları yukarıdaki sırayla yüklemeye çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paylaşılan ve sürümlü VSPackages arasında seçim yapma](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackages 'yi yönetme](../../extensibility/managing-vspackages.md)   
 [Yönetilen paket kaydı](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
