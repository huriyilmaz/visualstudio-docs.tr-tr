---
title: VSPackages 'yi yönetme | Microsoft Docs
description: Visual Studio tarafından sunulan varsayılan vspackage yönetimini ne zaman kullanabileceğinizi ve nasıl ve ne zaman özelleştirildiğini bilmeniz için vspackages 'yi yönetme hakkında bilgi edinin.
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
ms.openlocfilehash: 17afce8065377053494132644b33eb6389d98c74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724956"
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
 `AsyncPackage`Sınıfı Visual Studio daha ıyı UI yanıt verme için bir arka plan iş parçacığında paket yüklemeye izin vermez. Daha fazla bilgi için bkz. [nasıl yapılır: arka planda VSPackages yüklemek Için AsyncPackage kullanma](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Uzantılar için kural tabanlı kullanıcı arabirimi bağlamı
 Kural tabanlı kullanıcı arabirimi bağlamları uzantı yazarlarının, Kullanıcı arabirimi bağlamı etkinleştirilmiş ve ilişkili VSPackages 'nin altında kesin koşulları tanımlamasına olanak tanır. daha fazla bilgi için bkz. [nasıl yapılır: kural tabanlı kullanıcı arabirimi bağlamını Visual Studio uzantıları için kullanma](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Uzantı performansını tanılama
Uzantılar, başlangıç ve çözüm yükü performansını etkileyebilir. uzantı etkisini Visual Studio nasıl hesaplanacağını ve bir uzantının performansı etkileyen bir uzantı olarak gösterilip gösterilmeyeceğini test etmek için nasıl yerel olarak çözümlenebileceğinizi öğrenin. Daha fazla bilgi için bkz. [nasıl yapılır: uzantı performansını tanılama](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>VSPackages sorunlarını giderme
 Yüklenmeyen veya hata yaşayan VSPackages sorunlarını gidermeye yönelik teknikler hakkında bilgi edinin: [VSPackages sorunlarını giderme](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
