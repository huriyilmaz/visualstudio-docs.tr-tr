---
title: VSPackages 'yi yönetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702646"
---
# <a name="manage-vspackages"></a>VSPackage’ları Yönetme
Çoğu durumda, proje ve öğe şablonları paketi otomatik olarak kaydedip yüklerken VSPackages 'leri yönetme konusunda endişelenmenize gerek kalmaz. Ancak, bazı durumlarda paketinizi yönetmek için biraz daha fazla bilgi almanız gerekebilir.

## <a name="use-the-experimental-instance"></a>Deneysel örneği kullanma
 Deneysel örnek hakkında daha fazla bilgi edinmek için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>VSPackages kaydetme ve kaydını silme
 VSPackages 'ları ve diğer uzantı türlerini kaydetme ve kaydını kaldırma hakkında bilgi edinmek için bkz. [VSPackages 'ı kaydetme ve kaydını kaldırma](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>VSPackage yükleme
 Belirli bir CMDUICONTEXT GUID açık olduğunda VSPackages, oto Load olarak ayarlanabilir. Daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Arka planda VSPackages yüklemek için AsyncPackage kullanın
 `AsyncPackage`Sınıfı, Visual Studio 'da daha ıyı UI yanıt verme için bir arka plan iş parçacığında paket yüklenmesine izin vermez. Daha fazla bilgi için bkz. [nasıl yapılır: arka planda VSPackages yüklemek Için AsyncPackage kullanma](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Uzantılar için kural tabanlı kullanıcı arabirimi bağlamı
 Kural tabanlı kullanıcı arabirimi bağlamları uzantı yazarlarının, Kullanıcı arabirimi bağlamı etkinleştirilmiş ve ilişkili VSPackages 'nin altında kesin koşulları tanımlamasına olanak tanır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio uzantıları için kural tabanlı kullanıcı arabirimi bağlamını kullanma](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Uzantı performansını tanılama
Uzantılar, başlangıç ve çözüm yükü performansını etkileyebilir. Visual Studio uzantısı etkisinin nasıl hesaplanacağını ve bir uzantının bir performans etkileyerek uzantısı olarak gösterilip gösterilmeyeceğini test etmek için nasıl yerel olarak çözümlenebileceğinizi öğrenin. Daha fazla bilgi için bkz. [nasıl yapılır: uzantı performansını tanılama](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>VSPackages sorunlarını giderme
 Yüklenmeyen veya hata yaşayan VSPackages sorunlarını gidermeye yönelik teknikler hakkında bilgi edinin: [VSPackages sorunlarını giderme](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
