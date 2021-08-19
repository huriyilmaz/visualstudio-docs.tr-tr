---
title: SharePoint Project Öğesi Şema Başvurusu | Microsoft Docs
description: .spdata dosyalarının içeriğini doğrulamak için SharePoint proje öğesi XML şema başvurusuna (ProjectItemModelSchema.xsd) genel bakış bilgilerine bakın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115518"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint öğesi şema başvurusu
  Visual Studio *.spdata* SharePoint doğrulamak için proje öğesi şemasını kullanır. *.spdata dosyası,* bir proje öğesinin içeriğini SharePoint belirtir. Proje öğelerinin içeriği hakkında daha fazla SharePoint için bkz. Proje öğeleri için öğe [SharePoint ve proje şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 SharePoint proje öğesi şeması ProjectItemModelSchema.xsd olarak adlandırılmıştır ve %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas dizinine varsayılan olarak yüklenir.

 Kök öğe [ProjectItem öğesidir.](../sharepoint/projectitem-element.md) Aşağıdaki tabloda şema tarafından tanımlanan tüm öğeler açıklandı.

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu SharePoint temsil eder.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Anahtar/değer biçiminde bir proje öğesiyle SharePoint özel bir veri öğesini temsil eder. Hem anahtar hem de değer dizeler olmalı.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Bir Özellik,özel bir özel durum için dağıtıldığında dahil edilen özellik değerleri koleksiyonunu SharePoint. Bir Özellik dağıtıldıktan sonra, kodundaki özellik değerlerine erişebilirsiniz.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Özel bir özel özelliği, özel bir özel durum için dağıtıldığında bir Özellik'e dahil SharePoint. Bir Özellik dağıtıldıktan sonra kodundaki özelliğine erişebilirsiniz.|
|[Dosyalar](../sharepoint/files-element.md)|Özellik öğesi dosyası veya projenin çıkışı SharePoint proje öğesiyle birlikte dağıtıla dosyaları belirtir.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir proje SharePoint temsil eder.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Bu SharePoint proje öğesine dahil etmek için Özellik öğesi dosyası gibi bir dosya SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Eşlenmiş bir klasörü temsil eder.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Bir proje, proje öğesi bir projeye dağıtıldığında dahil etmek için bir projenin çıkışını SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Herhangi bir kullanıcının sitenin herhangi bir ASPX sayfasından erişmesi için güvenli olarak belirlenen bir ASPX SharePoint temsil eder.|
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX denetimleri koleksiyonunu temsil eder ve Web Bölümleri kullanıcının SharePoint sitesinde herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiştir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
