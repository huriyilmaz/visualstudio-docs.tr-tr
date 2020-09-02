---
title: Windows Installer dağıtımı için Uzantılar hazırlanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694589"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Uzantıları Windows Installer Dağıtımı için Hazırlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir VSıX paketini dağıtmak için bir Windows Installer paketi (MSI) kullanamazsınız. Ancak, MSI dağıtımı için bir VSıX paketinin içeriğini ayıklayabilirsiniz. Bu belgede, varsayılan çıktısı bir kurulum projesine eklemek için VSıX paketi olan bir projenin nasıl hazırlanacağı gösterilir.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için uzantı projesi hazırlama  
 Bir kurulum projesine eklemeden önce bu adımları yeni uzantı projelerinde gerçekleştirin.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer dağıtımı için bir uzantı projesi hazırlamak için  
  
1. Bir VSPackage, MEF bileşeni, düzenleyici kenarlığı veya VSıX bildirimi içeren başka bir genişletilebilirlik proje türü oluşturun.  
  
2. Kod düzenleyicisinde VSıX bildirimini açın.  
  
3. VSıX bildiriminin InstalledByMsi öğesini olarak ayarlayın `true` . VSıX bildirimi hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Bu, VSıX yükleyicisinin bileşeni yüklemeyi denemelerini engeller.  
  
4. **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' e tıklayın.  
  
5. **VSIX** sekmesini seçin.  
  
6. **Aşağıdaki konuma VSIX Içeriğini Kopyala** etiketli kutuyu Işaretleyin ve Kurulum projesinin dosyaları alacak olan yolu yazın.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Mevcut bir VSıX paketinden dosyalar ayıklanıyor  
 Kaynak dosyalarınız yoksa, mevcut bir VSıX paketinin içeriğini bir kurulum projesine eklemek için bu adımları gerçekleştirin.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Mevcut bir VSıX paketinden dosyaları ayıklamak için  
  
1. Yeniden adlandırın. Dosya *adı*. VSIX 'ten *filename*. ZIP dosyasına uzantıyı içeren VSIX dosyası.  
  
2. . Zip dosyasının içeriğini bir dizine kopyalayın.  
  
3. [Content_types]. xml dosyasını dizinden silin.  
  
4. VSıX bildirimini, önceki yordamda gösterildiği gibi düzenleyin.  
  
5. Geri kalan dosyaları kurulum projenize ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Yükleyicisi dağıtımı](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [İzlenecek yol: özel eylem oluşturma](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
