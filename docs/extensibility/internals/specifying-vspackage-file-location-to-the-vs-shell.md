---
title: VSPackage Dosya Konumunu VS Shell'e Belirtme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704972"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Kabuğuna VSPackage Dosya Konumunu Belirtme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage yüklemek için montaj DLL bulmak gerekir. Aşağıdaki tabloda açıklandığı gibi, çeşitli şekillerde bulabilirsiniz.

| Yöntem | Açıklama |
| - | - |
| CodeBase kayıt defteri anahtarını kullanın. | CodeBase tuşu, VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] montajını tam nitelikli herhangi bir dosya yolundan yüklemek için doğrudan kullanılabilir. Anahtarın değeri DLL'ye giden dosya yolu olmalıdır. Paket montajınızı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemenin en iyi yolu budur. Bu teknik bazen "CodeBase/private installation directory technique" olarak adlandırılır. Kayıt sırasında kod tabanının değeri, <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> türdeki bir örnek aracılığıyla kayıt özniteliği sınıflarına aktarılır. |
| DLL'yi **PrivateAssemblies** dizinine yerleştirin. | Derlemeyi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dizinin **PrivateAssemblies** alt dizinine yerleştirin. **PrivateAssemblies'de** bulunan derlemeler otomatik olarak algılanır, ancak **Başvuru Ekle** iletişim kutusunda görünmez. **PrivateAssemblies** ve **PublicAssemblies** arasındaki fark, **PublicAssemblies derlemeleri** **Ekleme Başvurular** iletişim kutusunda numaralandırılır olmasıdır. "CodeBase/private installation directory" tekniğini kullanmamayı seçtiyseniz, **PrivateAssemblies** dizinine yüklemeniz gerekir. |
| Güçlü adlandırılmış bir derleme ve Derleme kayıt defteri anahtarı kullanın. | Montaj tuşu, güçlü bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage derlemesini yüklemek için açıkça yönlendirmek için kullanılabilir. Anahtarın değeri derlemenin güçlü adı olmalıdır. |
| DLL'yi **PublicAssemblies** dizinine yerleştirin. | Son olarak, montaj da **PublicAssemblies** alt dizini yerleştirilebilir. **PublicAssemblies'de** bulunan derlemeler otomatik olarak algılanır ve ayrıca **'deki** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Başvuru Ekle iletişim kutusunda da görünür.<br /><br /> VSPackage derlemeleri yalnızca diğer VSPackage geliştiricileri tarafından yeniden kullanılması amaçlanan yönetilen bileşenler içeriyorsa **PublicAssemblies** dizinine yerleştirilmelidir. Meclislerin çoğu bu ölçüte uymaz. |

> [!NOTE]
> Tüm bağımlı derlemeleriniz için güçlü adlandırılmış, imzalı derlemeler kullanın. Bu derlemeler kendi dizininizde veya genel derleme önbelleğine (GAC) da yüklenmelidir. Bu, zayıf ad bağlama olarak bilinen aynı temel dosya adı olan derlemelerle çakışmalara karşı korur.
