---
title: Dosya Adı Uzantıları Hakkında | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740350"
---
# <a name="about-file-name-extensions"></a>Dosya adı uzantıları hakkında
Bir VSPackage'ın dosya uzantısını kaydettirdiğinizde, dosyayı bir .. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bir bilgisayarda birden fazla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümü yüklüyse bu önemlidir.

 VSPackages için dosya uzantıları, ilişkili programlı tanımlayıcıya (ProgID) işaret eden varsayılan bir değere sahip **HKEY_CLASSES_ROOT** anahtar altında kaydedilir.

 Aşağıdaki örnekte *.vcproj* dosya uzantısı için kayıt bilgileri gösterilmektedir:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 İlişkili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyaların progid sürümü olması gerekir, örneğin. `VisualStudio.vcproj.8.0` Sürümlü ProgID, ürünün yan yana yüklenmesini sağlayarak ürün sürümleri arasında dosya uzantısı ilişkilendirmelerini korur. Bir sürüm özel ProgID de standart fiiller kullanmanıza olanak sağlar, açık gibi, düzenleme, ve benzeri, overwriting veya diğer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]uygulamalar veya sürümleri tarafından üzerine yazılmış olma endişesi olmadan .

 Bazı durumlarda, bir dosya uzantısı ile ilişkili ProgID değiştirilmemelidir. Örneğin, *.htm* dosya uzantısı için ProgID (progid = htmlfile) işletim sistemindeki bir dizi yerde sabit kodlanır ve *.htm* ve *.html* dosyalarıyla bağlantılı olarak yaygın olarak bilinir ve kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için dosya işleyicileri belirtin](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
