---
title: SharePoint Project öğesi şeması başvurusu | Microsoft Docs
description: . spdata dosyalarının içeriğini doğrulamak için kullanılan SharePoint proje öğesi XML şema başvurusuna (projectıtemmodelschema. xsd) genel bakış bölümüne bakın.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 5dbeefe02cf917ac03aeb558acdb5c609543952e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636838"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint proje öğesi şema başvurusu
  Visual Studio, *. spdata* dosyalarının içeriğini doğrulamak için SharePoint proje öğesi şemasını kullanır. *. spdata* dosyası bir SharePoint proje öğesinin içeriğini ve davranışını belirtir. SharePoint proje öğelerinin içerikleri hakkında daha fazla bilgi için, bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 SharePoint proje öğesi şeması projectıtemmodelschema. xsd olarak adlandırılmıştır ve varsayılan olarak% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xml\bir dosya olarak yüklendi.

 Kök öğesi [ProjectItem](../sharepoint/projectitem-element.md) öğesidir. Aşağıdaki tabloda, şema tarafından tanımlanan tüm öğeler açıklanmaktadır.

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu temsil eder.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|anahtar/değer biçiminde SharePoint proje öğesiyle ilişkili özel bir veri öğesini temsil eder. Anahtar ve değer dizeler olmalıdır.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint dağıtıldığında bir özelliğe dahil edilen özellik değerleri koleksiyonunu temsil eder. Bir özellik dağıtıldıktan sonra, kodunuzda özellik değerlerine erişebilirsiniz.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint dağıtıldığında bir özelliğe dahil olan özel bir özelliği temsil eder. Bir özellik dağıtıldıktan sonra, kodunuzda özelliğine erişebilirsiniz.|
|[Dosyalar](../sharepoint/files-element.md)|özellik öğesi dosyası veya bir projenin çıktısı gibi SharePoint proje öğesiyle dağıtılacak dosyaları belirtir.|
|[ProjectItem](../sharepoint/projectitem-element.md)|bir SharePoint proje öğesini temsil eder.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|SharePoint öğesine dağıtıldığında proje öğesi dahil olmak üzere özellik öğesi dosyası gibi bir SharePoint dosyasını temsil eder.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Eşlenmiş bir klasörü temsil eder.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint öğesine dağıtıldığında proje öğesiyle birlikte içerilecek projenin çıkışını temsil eder.|
|[SafeControl](../sharepoint/safecontrol-element.md)|tüm kullanıcıların SharePoint sitesindeki herhangi bir aspx sayfasına erişmesi için güvenli olarak belirlenmiş bir aspx denetimi veya Web bölümü temsil eder.|
|[SafeControls](../sharepoint/safecontrols-element.md)|herhangi bir kullanıcının SharePoint sitesindeki herhangi bir aspx sayfasına erişmesi için güvenli olarak belirlenmiş bir aspx denetimleri ve Web Bölümleri koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
