---
title: Windows Installer Dağıtımı için Uzantı hazırlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702025"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows Installer dağıtımı için uzantıları hazırlama
Bir VSIX paketini dağıtmak için Windows Installer paketi (MSI) kullanamazsınız. Ancak, MSI dağıtımı için bir VSIX paketinin içeriğini ayıklayabilirsiniz. Bu belge, varsayılan çıktısı Bir Kurulum projesine dahil edilmesi için VSIX paketi olan bir projenin nasıl hazırlanacağını gösterir.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için bir uzantı projesi hazırlama
 Kurulum projesine eklemeden önce yeni uzantı projelerinde bu adımları gerçekleştirin.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için bir uzantı projesi hazırlamak için

1. VSIX bildirimi içeren bir VSPackage, MEF bileşeni, Düzenleyici Süsleme veya diğer genişletilebilirlik proje türü oluşturun.

2. Kod düzenleyicisinde VSIX bildirimini açın.

3. VSIX `InstalledByMsi` bildiriminin öğesini `true`. VSIX manifestosu hakkında daha fazla bilgi için [VSIX uzantı şeması 2.0 referansına](../extensibility/vsix-extension-schema-2-0-reference.md)bakın.

     Bu, VSIX yükleyicisinin bileşeni yüklemeye çalışmasına engel lenir.

4. **Çözüm Gezgini'nde** projeyi sağ tıklatın ve **Özellikler'i**tıklatın.

5. **VSIX** sekmesini seçin.

6. **VSIX içeriğini aşağıdaki konuma kopyala** etiketli kutuyu işaretleyin ve Kurulum projesinin dosyaları alacağı yolu yazın.

## <a name="extract-files-from-an-existing-vsix-package"></a>Varolan bir VSIX paketinden dosya ayıklama
 Kaynak dosyalarınız yoksa, varolan bir VSIX paketinin içeriğini kurulum projesine eklemek için aşağıdaki adımları gerçekleştirin.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Varolan bir VSIX paketinden dosya ayıklamak için

1. Yeniden *adlandırın. * *Filename.vsix'den* *filename.zip'e*uzantıyı içeren VSIX dosyası.

2. *.zip* dosyasının içeriğini bir dizine kopyalayın.

3. *[Content_types].xml* dosyasını dizinden silin.

4. Önceki yordamda gösterildiği gibi VSIX bildirimini edin.

5. Kalan dosyaları Kurulum projenize ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio yükleyici dağıtımı](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Walkthrough: Özel bir eylem oluşturma](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
