---
title: Dosya adı uzantıları hakkında | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148030"
---
# <a name="about-file-name-extensions"></a>Dosya Adı Uzantıları Hakkında
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage 'un bir dosya uzantısını kaydettiğinizde, bunu bir sürümüyle ilişkilendirirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bir bilgisayarda birden fazla sürümü yüklüyse bu önemlidir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 VSPackages için dosya uzantıları, ilişkili programlı tanımlayıcıyı (ProgID) gösteren varsayılan bir değer olan HKEY_CLASSES_ROOT anahtarı altına kaydedilir.  
  
 Aşağıda. VCPROJ dosya uzantısının kayıt bilgilerine bir örnek verilmiştir:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 İle ilişkili dosyalar, ürün [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `VisualStudio.vcproj.8.0` sürümleri arasında dosya uzantısı ilişkilendirmelerini sürdürmek üzere ürünün yan yana yüklemelerine izin vermek için gibi sürümlenmiş bir ProgID 'ye sahip olmalıdır. Sürüme özgü bir ProgID Ayrıca, diğer uygulamalar veya sürümleri için üzerine yazma veya üzerine yazma sorunu olmadan açık, düzenleme, vb. gibi standart yüklemleri kullanmanıza da olanak tanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Belirli durumlarda, bir dosya uzantısıyla ilişkili ProgID değiştirilmemelidir. Örneğin,. htm dosya uzantısı (ProgID = htmlfile) için ProgID, işletim sistemindeki birkaç yerde sabit olarak kodlanmıştır ve. htm ve. html dosyalarıyla ilişkilendirmede yaygın olarak bilinir ve kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
