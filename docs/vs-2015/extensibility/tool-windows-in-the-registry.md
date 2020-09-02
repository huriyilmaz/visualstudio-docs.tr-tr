---
title: Kayıt defterindeki araç pencereleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186379"
---
# <a name="tool-windows-in-the-registry"></a>Kayıt Defterindeki Araç Pencereleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç pencerelerini sağlayan VSPackages, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç penceresi sağlayıcıları olarak kaydedilmelidir. Visual Studio paket şablonu kullanılarak oluşturulan araç pencereleri varsayılan olarak bunu yapın. Araç penceresi sağlayıcılarının varsayılan araç penceresi boyutu ve konumu, araç penceresi bölmesi olarak hizmet veren pencerenin GUID 'SI ve yerleştirme stili gibi görünürlük özniteliklerini belirten sistem kayıt defteri anahtarları vardır.  
  
 Geliştirme sırasında, yönetilen araç penceresi sağlayıcıları kaynak koda öznitelikler ekleyerek ve sonra ortaya çıkan derlemede RegPkg.exe yardımcı programını çalıştırarak araç pencerelerini kaydeder. Daha fazla bilgi için bkz. [bir araç penceresini kaydetme](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Yönetilmeyen araç penceresi sağlayıcılarını kaydetme  
 Yönetilmeyen araç penceresi sağlayıcıları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistem kayıt defteri 'Nin araç pencereleri bölümünde ile kaydolmalıdır. Aşağıdaki. reg dosya parçası, dinamik bir araç penceresinin nasıl kaydettirilbileceğini göstermektedir:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Yukarıdaki örnekteki ilk anahtarda sürüm numarası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , 7,1 veya 8,0 gibi bir sürümüdür, {f0e1e9a1-9860-484d-ad5d-367d79aabf55} alt anahtarı araç penceresi bölmesinin GUID 'sidir (DynamicWindowPane) ve {01069cdd-95ce-4620-ac21-ddff6c57f012} varsayılan değeri araç penceresini sağlayan VSPackage GUID 'sidir. Float ve DontForceCreate alt anahtarlarının bir açıklaması için bkz. [araç penceresi görüntüleme yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
 İkinci isteğe bağlı anahtar olan ToolWindows\Visibility, araç penceresinin görünür hale getirilmesini gerektiren komutların GUID 'Lerini belirtir. Bu durumda, belirtilen bir komut yoktur. Daha fazla bilgi için bkz. [araç penceresi görüntü yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage temelleri](../misc/vspackage-essentials.md)
