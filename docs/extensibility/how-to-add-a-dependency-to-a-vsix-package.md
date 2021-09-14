---
title: 'Nasıl yapılır: VSıX paketine bağımlılık ekleme | Microsoft Docs'
description: Hedef bilgisayarda zaten mevcut olmayan bağımlılıkları yükleyen bir VSıX paketi dağıtımını ayarlamayı öğrenin.
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
ms.openlocfilehash: 0335e243fe0779060282cecdc58ad9deb608c948
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626276"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Nasıl yapılır: VSıX paketine bağımlılık ekleme

Hedef bilgisayarda zaten mevcut olmayan bağımlılıkları yükleyen bir VSıX paketi dağıtımı ayarlayabilirsiniz. Bunu gerçekleştirmek için, *kaynak. Extension. valtmanifest* dosyasına VSIX bağımlılıklarını ekleyin.

## <a name="to-add-a-dependency"></a>Bir bağımlılık eklemek için

1. **Design** görünümünde *Source. Extension. valtmanifest* dosyasını açın. **Bağımlılıklar** sekmesine gidin ve **Yeni**' ye tıklayın.

2. Yüklü bir uzantı eklemek için: **Yeni bağımlılık Ekle** iletişim kutusunda, **yüklü uzantı** ' ı seçin ve ardından **ad** için listeden bir uzantı seçin.

3. Yüklü olmayan başka bir VSıX eklemek için: **Yeni bağımlılık Ekle** iletişim kutusunda **dosya sistemindeki dosya** ' yı seçin ve ardından VSIX ' i seçmek için, **tarayıcı** düğmesini kullanın.

## <a name="require-a-specific-visual-studio-release"></a>belirli bir Visual Studio sürümü gerektir

uzantınız Visual Studio 2017 ' nin belirli bir sürümünü gerektiriyorsa, örneğin, 15,3 ' de yayınlanan bir özelliğe bağlı olarak, vsıx **ınstalyüklemi hedefinizdeki** derleme numarasını belirtebilirsiniz. Örneğin, Release 15,3 ' 15.0.26730.3 ' derleme numarasına sahiptir. Sürüm numaralarını [burada](../install/visual-studio-build-numbers-and-release-dates.md)oluşturmak için bu sürümlerin eşlemesini görebilirsiniz. ' 15,3 ' yayın numarasını kullanmanın doğru şekilde çalışmadığına unutmayın.

Uzantınız 15,3 veya daha yüksek bir sürüm gerektiriyorsa, **ınstalyüklemehedef sürümünü** [15.0.26730.3, 16,0) olarak bildirebilirsiniz:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

valtıyükleyicisi, önceki Visual Studio sürümlerini algılayacak ve kullanıcıyı daha sonra bir güncelleştirmenin gerekli olduğunu bilgilendirdirecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [VSıX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110))
- [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows Installer dağıtımı için uzantıları hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)