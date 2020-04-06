---
title: 'Nasıl yapılsın: VSIX Paketine Bağımlılık Ekleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711072"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Nasıl yapilir: VSIX paketine bağımlılık ekleme

Hedef bilgisayarda zaten bulunmayan bağımlılıkları yükleyen bir VSIX paket dağıtımı ayarlayabilirsiniz. Bunu başarmak için *source.extension.vsixmanifest* dosyasına VSIX bağımlılıklarını ekleyin.

## <a name="to-add-a-dependency"></a>Bağımlılık eklemek için

1. **Design** görünümünde *source.extension.vsixmanifest* dosyasını açın. **Bağımlılıklar** sekmesine gidin ve **Yeni'yi**tıklatın.

2. Yüklü bir uzantı eklemek için: **Yeni Bağımlılık Ekle** iletişim **kutusunda, Yüklü uzantıyı** seçin ve ardından **Ad**için listede bir uzantı seçin.

3. Yüklü olmayan başka bir VSIX eklemek için: **Yeni Bağımlılık Ekle** iletişim kutusunda dosya sisteminde **Dosya'yı** seçin ve ardından VSIX'yi seçmek için **Gözat** düğmesini kullanın.

## <a name="require-a-specific-visual-studio-release"></a>Belirli bir Visual Studio sürümü gerektirir

Uzantınız Visual Studio 2017'nin belirli bir sürümünü gerektiriyorsa, örneğin, 15.3'te yayımlanan bir özelliğe bağlıysa, VSIX **InstallationTarget'ınızdaki**yapı numarasını belirtebilirsiniz. Örneğin, sürüm 15.3 '15.0.26730.3' bir yapı numarası vardır. [Burada](../install/visual-studio-build-numbers-and-release-dates.md)sayılar oluşturmak için bültenlerin eşleme görebilirsiniz. '15.3' sürüm numarasını kullanmanın doğru çalışmayacağını unutmayın.

Uzantınız 15.3 veya üzeri gerektiriyorsa, **InstallationTarget Sürümünü** [15.0.26730.3, 16.0) olarak bildirirsiniz:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller Visual Studio önceki sürümlerini algılar ve daha sonra bir güncelleştirme gerekli olduğunu kullanıcıbilgilendirir.

## <a name="see-also"></a>Ayrıca bkz.

- [VSIX uzantı şeması 1.0 referans](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows Installer dağıtımı için uzantıları hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
