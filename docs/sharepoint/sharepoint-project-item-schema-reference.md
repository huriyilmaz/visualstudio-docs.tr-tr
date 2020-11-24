---
title: SharePoint proje öğesi şema başvurusu | Microsoft Docs
description: . Spdata dosyalarının içeriğini doğrulamak için kullanılan SharePoint proje öğesi XML şema başvurusuna (Projectıtemmodelschema. xsd) genel bakış bölümüne bakın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd425111e7e3d69e381e69e60daf914f74cd2d11
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442553"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint proje öğesi şema başvurusu
  Visual Studio, *. spdata* dosyalarının içeriğini doğrulamak için SharePoint proje öğesi şemasını kullanır. *. Spdata* dosyası bir SharePoint proje öğesinin içeriğini ve davranışını belirtir. SharePoint proje öğelerinin içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 SharePoint proje öğesi şeması Projectıtemmodelschema. xsd olarak adlandırılmıştır ve% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\şeması \ ' de varsayılan olarak yüklenir.

 Kök öğesi [ProjectItem](../sharepoint/projectitem-element.md) öğesidir. Aşağıdaki tabloda, şema tarafından tanımlanan tüm öğeler açıklanmaktadır.

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint proje öğesiyle ilişkili özel veri öğelerinin koleksiyonunu temsil eder.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Anahtar/değer biçiminde SharePoint proje öğesiyle ilişkili özel bir veri öğesini temsil eder. Anahtar ve değer dizeler olmalıdır.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint 'e dağıtıldığında bir özelliğe dahil olan özellik değerlerinin koleksiyonunu temsil eder. Bir özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint 'e dağıtıldığında bir özelliğe dahil olan özel bir özelliği temsil eder. Bir özellik dağıtıldıktan sonra, kodunuzda özelliğine erişebilirsiniz.|
|[Dosyalar](../sharepoint/files-element.md)|Bir özellik öğesi dosyası veya bir projenin çıktısı gibi SharePoint proje öğesiyle dağıtılacak dosyaları belirtir.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir SharePoint proje öğesini temsil eder.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|SharePoint 'e dağıtıldığında proje öğesiyle birlikte dahil edilecek özellik öğesi dosyası gibi bir SharePoint dosyasını temsil eder.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Eşlenmiş bir klasörü temsil eder.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint 'e dağıtıldığında proje öğesiyle birlikte dahil edilecek bir projenin çıkışını temsil eder.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimi veya Web bölümü temsil eder.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimleri ve Web Bölümleri koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
