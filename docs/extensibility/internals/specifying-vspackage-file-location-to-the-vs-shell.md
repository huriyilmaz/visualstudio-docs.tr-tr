---
title: VS Shell'de VSPackage Dosya Konumunu | Microsoft Docs
description: VsPackage'ı yüklemek için Visual Studio DLL'lerini bulmanın nasıl mümkün olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 044655e6f1b1eb984e521b26cb9796ae3e5543d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057167"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Kabuğuna VSPackage Dosya Konumunu Belirtme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı yüklemek için derleme DLL'lerini bulmalıdır. Aşağıdaki tabloda açıklandığı gibi çeşitli yollarla bu dosyayı buabilirsiniz.

| Yöntem | Açıklama |
| - | - |
| CodeBase kayıt defteri anahtarını kullanın. | CodeBase anahtarı, VSPackage derlemeyi herhangi bir tam dosya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yolundan yüklemek için doğrudan kullanılabilir. Anahtarın değeri, DLL'nin dosya yoludur. Bu, paket derlemenizi yüklemenin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en iyi yolu. Bu teknik bazen "CodeBase/özel yükleme dizini tekniği" olarak adlandırılır. Kayıt sırasında kod tabanının değeri, tür örneği aracılığıyla kayıt özniteliği sınıflara <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> geçirilir. |
| DLL'yi **PrivateAssemblies dizinine** ekleyin. | Derlemeyi dizinin **PrivateAssemblies** alt dizinine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yer. **PrivateAssemblies'te bulunan** derlemeler otomatik olarak algılanır, ancak Başvuru Ekle **iletişim kutusunda** görünmez. **PrivateAssemblies** ile **PublicAssemblies** arasındaki **fark, PublicAssemblies'te** derlemelerin Başvuru Ekle iletişim kutusunda **numaralandırılacaklarıdır.** "CodeBase/özel yükleme dizini" tekniğini kullanmamayı seçtiyebilirsiniz, **privateAssemblies dizinine yüklemeniz** gerekir. |
| Strong adlı bir derleme ve Derleme kayıt defteri anahtarı kullanın. | Derleme anahtarı, adlandırılmış güçlü bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage derlemesi yüklemek için açıkça doğrudan kullanılabilir. Anahtarın değeri derlemenin güçlü adı olabilir. |
| DLL'yi **PublicAssemblies dizinine** ekleyin. | Son olarak, derleme **PublicAssemblies alt dizinine** de yer olabilir. **PublicAssemblies'te bulunan** derlemeler otomatik olarak algılanır ve içinde Başvuru Ekle **iletişim** kutusunda da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görünür.<br /><br /> VSPackage derlemeleri yalnızca diğer VSPackage geliştiricileri tarafından yeniden kullanılması amaçlanan yönetilen bileşenler içeriyorsa **PublicAssemblies** dizinine yerleştirilsin. Derlemelerin çoğu bu ölçütü karşılamaz. |

> [!NOTE]
> Tüm bağımlı derlemeler için güçlü adlandırılmış, imzalı derlemeler kullanın. Bu derlemeler kendi dizininize veya genel derleme önbelleğine (GAC) de yük olmalıdır. Bu, zayıf ad bağlaması olarak bilinen aynı temel dosya adına sahip derlemelerle çakışmalara karşı koruma sağlar.
