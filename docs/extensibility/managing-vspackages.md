---
title: VSPackage'ları | Microsoft Docs
description: YALNıZCA Visual Studio tarafından sağlanan varsayılan VSPackage yönetimini ne zaman kullanabileceğinizi ve nasıl ve ne zaman özelleştirebileceğinizi öğrenmek için VSPackage'ları yönetme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: af813e57420cfcb5c583af18790f5399cb54be47f1f1dc959ec1d6d451951711
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401069"
---
# <a name="manage-vspackages"></a>VSPackage’ları Yönetme
Çoğu durumda, proje ve öğe şablonları paketi otomatik olarak kaydederek yükleyene kadar VSPackage'ları yönetme konusunda endişelenmenize gerek yok. Ancak bazı durumlarda paketinizi yönetmek için biraz daha fazla bilgi edinmek zorundayabilirsiniz.

## <a name="use-the-experimental-instance"></a>Deneysel örneği kullanma
 Deneysel örnek hakkında daha fazla bilgi için [bkz. Deneysel örnek.](../extensibility/the-experimental-instance.md)

## <a name="register-and-unregister-vspackages"></a>VSPackage'ları kaydetme ve kaydını çıkarma
 VSPackage'ları ve diğer uzantı türlerini kaydetmeyi ve kaydını nasıl silenleri bulmak için bkz. [VSPackage'ları kaydetme ve kaydını çıkarma.](../extensibility/registering-and-unregistering-vspackages.md)

## <a name="load-a-vspackage"></a>VSPackage Yükleme
 BELIRLI bir CMDUICONTEXT GUID'i açık olduğunda VSPackage'lar otomatik olarak yük devredülerek ayar olabilir. Daha fazla bilgi için [bkz. VSPackage'ları Yükleme.](../extensibility/loading-vspackages.md)

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>ARKA planda VSPackage yüklemek için AsyncPackage kullanma
 sınıfı, `AsyncPackage` kullanıcı arabiriminde daha iyi kullanıcı arabirimi yanıt hızı için arka plan iş parçacığında paket Visual Studio. Daha fazla bilgi için, [bkz. How to: Use AsyncPackage to load VSPackages in the background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Uzantılar için kural tabanlı KULLANıCı Arabirimi Bağlamı
 Kural tabanlı UI Bağlamları, uzantı yazarlarının bir UI Bağlamının etkinleştirildikten ve vsPackage'ların yükleniyor olduğu kesin koşulları tanımlamalarına olanak sağlar. Daha fazla bilgi için, [bkz. How to: Use rule-based UI Context for Visual Studio .](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)

## <a name="diagnose-extension-performance"></a>Uzantı performansını tanılama
Uzantılar başlatma ve çözüm yükleme performansını etkileyebilir. Uzantının Visual Studio nasıl hesaplanmış olduğunu ve bir uzantının performansı etkileyen bir uzantı olarak gösterip gösterileyemlileyrini test etmek için yerel olarak nasıl analiz edildiklerini öğrenin. Daha fazla bilgi için, [bkz. How to: Diagnose extension performance](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>VSPackage sorunlarını giderme
 Yüklenmeen veya hatalarla karşılaşan VSPackage sorunlarını giderme tekniklerini bulun: [VSPackage](../extensibility/troubleshooting-vspackages.md) sorunlarını giderme

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
