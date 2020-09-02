---
title: Durum kalıcılığı için destek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434325"
---
# <a name="support-for-state-persistence"></a>Durum kalıcılığı desteği
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ortak nesnelerin durumunu koruyabilir. Örneğin, çözüm ve proje özellikleri, çözüm ve proje dosyalarına kaydedilir ve geri yüklenir. Kullanıcı ayarları, ayarlar dosyasına aktarılabilir ve bu dosyalardan içeri aktarılabilir.  
  
 VSPackages, genellikle sistem kayıt defterinde veya geçerli kullanıcı ya da bilgisayarın uygulama verileri klasöründe yerel depolama alanını kullanır. Depolama için, tamsayılar ve dizeler gibi az miktarda alan gerektiren değerler genellikle sistem kayıt defterinde saklanır. Bit eşlemler gibi, depolama için çok fazla alan gerektiren değerler bir dosyaya kaydedilir. Dosyanın yolu sistem kayıt defterine kaydedilebilir. Kalıcılık mekanizmasının yerel depolamaya erişim izni olmalıdır.  
  
## <a name="support-for-locating-local-storage"></a>Yerel depolamayı bulma desteği  
 <xref:Microsoft.VisualStudio.Shell.Package>Sınıfı, geçerli kullanıcı veya bilgisayar için sistem kayıt defteri veya uygulama verileri klasöründeki durum bilgilerini bulmaya yönelik destek sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 İçin yerel bilgisayarın kayıt defteri kökünün yolunu döndürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; Örneğin, HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0Exp.  
  
 Yerel kayıt defteri kökü <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> hizmetten alınır. Bu kullanılamıyorsa, <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackage özniteliğinden elde edilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 İçin geçerli kullanıcının (bilgisayar başına) kayıt defteri kökünün yolunu döndürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; Örneğin, HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp.  
  
 Yerel kayıt defteri kökü <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> hizmetten alınır. Bu kullanılamıyorsa, VSPackage 'ın DefaultLocalRegistryRoot özniteliğinden elde edilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Geçerli dolaşım kullanıcısına ilişkin veriler için ortak bir depo görevi gören dizinin yolunu döndürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; Örneğin, C:\Documents ve Settings \\ *youraccountname*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Geçerli dolaşım olmayan kullanıcı için veri için ortak bir depo görevi gören dizinin yolunu döndürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Örneğin, C:\Documents and Settings \\ *youraccountname*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage durumu](../misc/vspackage-state.md)