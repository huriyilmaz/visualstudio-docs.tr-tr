---
title: VSPackages Yönetme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702646"
---
# <a name="manage-vspackages"></a>VSPackage’ları Yönetme
Proje ve madde şablonları paketi otomatik olarak kaydedip yüklediğinden, çoğu durumda VSPackages'ı yönetme konusunda endişelenmenize gerek yoktur. Ancak, bazı durumlarda paketinizi yönetmek için biraz daha fazla bilgi edinmeniz gerekebilir.

## <a name="use-the-experimental-instance"></a>Deneysel örneği kullanma
 Deney örneği hakkında daha fazla bilgi edinmek [için, bkz.](../extensibility/the-experimental-instance.md)

## <a name="register-and-unregister-vspackages"></a>VSPackages'ı kaydetme ve kayıt dışı
 VSPackages'ı ve diğer uzantı türlerini nasıl kaydedip not alacağınızı öğrenmek için, [VSPackages'ı kaydedin ve kaydını silin.](../extensibility/registering-and-unregistering-vspackages.md)

## <a name="load-a-vspackage"></a>VSPackage yükleyin
 VSPackages belirli bir CMDUICONTEXT GUID açık olduğunda otomatik yüklenecek şekilde ayarlanabilir. Daha fazla bilgi için [Load VSPackages'e](../extensibility/loading-vspackages.md)bakın.

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Arka planda VSPackages yüklemek için AsyncPackage kullanın
 Sınıf, `AsyncPackage` Visual Studio'da daha iyi ui yanıt verme için arka plan iş parçacığına paket yüklemesi sağlar. Daha fazla bilgi için [bkz: Arka planda VSPackages yüklemek için AsyncPackage kullanın.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Uzantılar için kural tabanlı UI Bağlamı
 Kurallara dayalı Kullanıcı Arası Bilgi Birimi Bağlamları, uzantı lı yazarların Kullanıcı Arası Bilgi Birimi Bağlamı'nın etkinleştirildiği ve vspackages'ın yüklendiği kesin koşulları tanımlamasına olanak tanır. Daha fazla bilgi için [bkz: Visual Studio uzantıları için kural tabanlı Kullanıcı Arabirimi Bağlamı'nı kullanın.](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)

## <a name="diagnose-extension-performance"></a>Uzantı performansını tanılama
Uzantılar başlangıç ve çözüm yük performansını etkileyebilir. Visual Studio uzantısı etkisinin nasıl hesaplandığını ve bir uzantın performans etkileyen uzantı olarak gösterip gösterilemediğini test etmek için yerel olarak nasıl analiz edilebildiğini öğrenin. Daha fazla bilgi için [bkz: Uzantı performansını tanıla.](how-to-diagnose-extension-performance.md)

## <a name="troubleshoot-vspackages"></a>Sorun Giderme VSPackages
 Sorun giderme VSPackages'ı yüklemeyen veya hata yaşayan tekniklerini öğrenin: [Sorun Giderme VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
