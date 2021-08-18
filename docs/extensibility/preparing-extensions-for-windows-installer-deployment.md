---
title: Windows Installer dağıtımı için uzantılar hazırlanıyor | Microsoft Docs
description: Varsayılan çıktısı bir kurulum projesine eklemek için VSıX paketi olan bir projeyi nasıl hazırlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ce2dce5735fa665ff127736db2df6d7dfb53b9f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041613"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows Installer dağıtımı için uzantıları hazırlama
bir vsıx paketini dağıtmak için bir Windows Installer paketi (msı) kullanamazsınız. Ancak, MSI dağıtımı için bir VSıX paketinin içeriğini ayıklayabilirsiniz. Bu belgede, varsayılan çıktısı bir kurulum projesine eklemek için VSıX paketi olan bir projenin nasıl hazırlanacağı gösterilir.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için bir uzantı projesi hazırlama
 Bir kurulum projesine eklemeden önce bu adımları yeni uzantı projelerinde gerçekleştirin.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için bir uzantı projesi hazırlamak için

1. Bir VSPackage, MEF bileşeni, düzenleyici kenarlığı veya VSıX bildirimi içeren başka bir genişletilebilirlik proje türü oluşturun.

2. Kod düzenleyicisinde VSıX bildirimini açın.

3. `InstalledByMsi`VSIX bildiriminin öğesini olarak ayarlayın `true` . VSıX bildirimi hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).

     Bu, VSıX yükleyicisinin bileşeni yüklemeyi denemelerini engeller.

4. **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' e tıklayın.

5. **VSIX** sekmesini seçin.

6. **Aşağıdaki konuma VSIX Içeriğini Kopyala** etiketli kutuyu Işaretleyin ve Kurulum projesinin dosyaları alacak olan yolu yazın.

## <a name="extract-files-from-an-existing-vsix-package"></a>Mevcut bir VSıX paketinden dosyaları ayıkla
 Kaynak dosyalarınız yoksa, mevcut bir VSıX paketinin içeriğini bir kurulum projesine eklemek için bu adımları gerçekleştirin.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Mevcut bir VSıX paketinden dosyaları ayıklamak için

1. Yeniden adlandırın *.* Dosya *adı. vsix* ' den *filename.zip* için uzantıyı içeren VSIX dosyası.

2. *.zip* dosyanın içeriğini bir dizine kopyalayın.

3. *[Content_Types] .xml* dosyasını dizinden silin.

4. VSıX bildirimini, önceki yordamda gösterildiği gibi düzenleyin.

5. Geri kalan dosyaları kurulum projenize ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio yükleyici dağıtımı](/previous-versions/2kt85ked(v=vs.120))
- [İzlenecek yol: özel eylem oluşturma](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))