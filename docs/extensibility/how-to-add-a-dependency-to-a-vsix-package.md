---
title: 'Nasıl: VSIX PaketiNe Bağımlılık Ekleme | Microsoft Docs'
description: Hedef bilgisayarda zaten mevcut olan bağımlılıkları yüken bir VSIX paket dağıtımı ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 58453344957b5264e9f3061878953c2007d56c238f71b4200c6d518df6d7af1c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359929"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Nasıl: VSIX paketine bağımlılık ekleme

Hedef bilgisayarda zaten mevcut olan bağımlılıkları yüken bir VSIX paket dağıtımı kurabilirsiniz. Bunu gerçekleştirmek için, VSIX bağımlılıklarını *source.extension.vsixmanifest dosyasına* dahil edin.

## <a name="to-add-a-dependency"></a>Bağımlılık eklemek için

1. Tasarım *görünümünde source.extension.vsixmanifest* **dosyasını** açın. Bağımlılıklar **sekmesine gidin** ve Yeni'ye **tıklayın.**

2. Yüklü bir uzantı eklemek için: Yeni Bağımlılık Ekle  iletişim kutusunda Yüklü uzantı'ya tıklayın ve ardından Ad **için** listeden bir uzantı seçin. 

3. Yüklenmemiş başka bir VSIX eklemek için: Yeni Bağımlılık Ekle  iletişim kutusunda Dosya sisteminde  Dosya'ya tıklayın ve ardından Gözat düğmesini kullanarak VSIX'i seçin. 

## <a name="require-a-specific-visual-studio-release"></a>Belirli bir Visual Studio gerektirme

Uzantınız belirli bir Visual Studio 2017 sürümünü gerektiriyorsa, örneğin, 15.3 sürümünde yayımlanan bir özeliklere bağlı olarak VSIX InstallationTarget içinde derleme numarasını **belirtebilirsiniz.** Örneğin, 15.3 sürümü '15.0.26730.3' derleme numarasına sahip. Derleme numaralarına yayın eşlemesini [buradaabilirsiniz.](../install/visual-studio-build-numbers-and-release-dates.md) '15.3' yayın numarasının doğru çalışmaycagunu unutmayın.

Uzantınız 15.3 veya daha yüksek bir sürüm gerektiriyorsa **InstallationTarget Sürümünü** [15.0.26730.3, 16.0) olarak bildirebilirsiniz:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller, uygulamanın önceki Visual Studio algılar ve kullanıcıya daha sonraki bir güncelleştirmenin gerekli olduğunu bildirecek.

## <a name="see-also"></a>Ayrıca bkz.

- [VSIX uzantı şeması 1.0 başvurusu](/previous-versions/dd393700(v=vs.110))
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows Yükleyicisi dağıtımı için uzantıları hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)