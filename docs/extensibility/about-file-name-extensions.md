---
title: Dosya Adı Uzantıları hakkında | Microsoft Docs
description: VSPackage'lar için dosya adı uzantılarını kaydetmeyi ve bunları uygulamanın belirli bir sürümüyle Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 75629d0f559db2dac717d44eb3dc59b23c8af9e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127798"
---
# <a name="about-file-name-extensions"></a>Dosya adı uzantıları hakkında
VSPackage'ın bir dosya uzantısını kaydeden bir sürümüyle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ilişkilendirmek. Bir bilgisayarda birden fazla sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklüyse bu önemlidir.

 VSPackage'lar için dosya uzantıları, **HKEY_CLASSES_ROOT** program tanımlayıcısına (ProgID) yönelik varsayılan bir değere sahip bir anahtar altında kaydedilir.

 Aşağıdaki örnekte *.vcproj* dosya uzantısı için kayıt bilgileri gösterir:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 ile ilişkili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyaların, gibi sürümüne sahip bir ProgID'ye sahip olması `VisualStudio.vcproj.8.0` gerekir. Sürüme sahip bir ProgID, ürün sürümleri arasındaki dosya uzantısı ilişkilendirmelerini korumak için ürünün yan yana yüklenmesine olanak sağlar. Sürüme özgü Bir ProgID, üzerine yazma veya diğer uygulamalar veya sürümleri tarafından üzerine yazılma endişesi olmadan açık, düzenleme gibi standart fiilleri de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanabilirsiniz.

 Bazı durumlarda, bir dosya uzantısıyla ilişkili ProgID değiştirilemez. Örneğin, *.htm* dosya uzantısı için ProgID (progid = htmlfile) işletim sistemi içinde bir dizi yerde sabit kodlanır ve yaygın olarak bilinir ve *.htm* ve.html *dosyalarıyla birlikte* kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için dosya işleyicileri belirtme](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
