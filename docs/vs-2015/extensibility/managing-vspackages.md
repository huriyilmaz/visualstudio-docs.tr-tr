---
title: VSPackages 'yi yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194378"
---
# <a name="managing-vspackages"></a>VSPackage’ları Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoğu durumda, proje ve öğe şablonları paketi otomatik olarak kaydedip yüklerken VSPackages 'leri yönetme konusunda endişelenmenize gerek kalmaz. Ancak, bazı durumlarda paketinizi yönetmek için biraz daha fazla bilgi almanız gerekebilir.  
  
## <a name="using-the-experimental-instance"></a>Deneysel örneği kullanma  
 Deneysel örnek hakkında daha fazla bilgi edinmek için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>VSPackage Kaydetme ve Kaydını Kaldırma  
 VSPackages 'ları ve diğer uzantı türlerini kaydetme ve kaydını silme hakkında bilgi edinmek için bkz. [VSPackages kaydetme ve kaydını silme](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>VSPackage yükleme  
 Belirli bir CMDUICONTEXT GUID açık olduğunda VSPackages, oto Load olarak ayarlanabilir. Daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Arka planda VSPackages yüklemek için AsyncPackage kullanma  
 AsyncPackage sınıfı, Visual Studio 'da daha iyi UI yanıt verme için bir arka plan iş parçacığında paket yüklenmesine izin verebilir. Daha fazla bilgi için bkz. [nasıl yapılır: arka planda VSPackages yüklemek Için AsyncPackage kullanma](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Uzantılar için kural tabanlı kullanıcı arabirimi bağlamı  
 Kural tabanlı kullanıcı arabirimi bağlamları uzantı yazarlarının, Kullanıcı arabirimi bağlamı etkinleştirilmiş ve ilişkili VSPackages 'nin altında kesin koşulları tanımlamasına olanak tanır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio uzantıları Için kural tabanlı kullanıcı arabirimi bağlamını kullanma](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme  
 Yüklenmeyen veya hata yaşayan VSPackages sorunlarını giderme tekniklerini öğrenin: [VSPackages sorunlarını giderme](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)
