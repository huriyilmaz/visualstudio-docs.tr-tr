---
title: Dosya adı uzantıları hakkında | Microsoft Docs
description: VSPackages için dosya adı uzantılarını kaydetmeyi ve bunları Visual Studio 'nun belirli bir sürümüyle ilişkilendirmeyi öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: f38bee1b62340f7d557ac2e5190fc5c48d9268fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060152"
---
# <a name="about-file-name-extensions"></a>Dosya adı uzantıları hakkında
VSPackage 'un bir dosya uzantısını kaydettiğinizde, bunu bir sürümüyle ilişkilendirirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bir bilgisayarda birden fazla sürümü yüklüyse bu önemlidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 VSPackages için dosya uzantıları, ilişkili programlı tanımlayıcıyı (ProgID) gösteren varsayılan bir değer olan **HKEY_CLASSES_ROOT** anahtarı altına kaydedilir.

 Aşağıdaki örnek, *. vcproj* dosya uzantısının kayıt bilgilerini gösterir:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 İle ilişkili dosyalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , gibi sürümlü bir ProgID 'ye sahip olmalıdır `VisualStudio.vcproj.8.0` . Sürümlü bir ProgID, ürün sürümleri arasında dosya uzantısı ilişkilendirmelerini sürdürmek için ürünün yan yana yüklemelerine izin verir. Sürüme özgü bir ProgID Ayrıca, diğer uygulamalar veya sürümleri için üzerine yazma veya üzerine yazma sorunu olmadan açık, düzenleme, vb. gibi standart yüklemleri kullanmanıza da olanak tanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Belirli durumlarda, bir dosya uzantısıyla ilişkili ProgID değiştirilmemelidir. Örneğin, *. htm* dosya uzantısı (ProgID = htmlfile) için ProgID, işletim sistemindeki birkaç yerde sabit kodlanmış ve *. htm* ve *. html* dosyalarıyla ilişkilendirmede yaygın olarak bilinir ve kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için dosya işleyicileri belirtin](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
