---
title: Özellik ve paket bildirimlerinde XML birleştirme | Microsoft Docs
description: SharePoint özellik ve paket bildirimlerinde tasarımcı tarafından oluşturulan ve kullanıcı tarafından eklenen XML kodu birleştirme. Özellik ve paket bildirim öğelerini öğrenin ve özel durumları birleştirin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c4af8e25fa998804e56359faa29cd7e5651336218003100f60fac379fcc5f641
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244322"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Özellik ve paket bildirimlerinde XML 'yi birleştirme
  Özellikler ve paketler, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim dosyaları tarafından tanımlanır. Bu paketlenmiş bildirimler, tasarımcılardan oluşturulan verilerin ve [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim şablonunda kullanıcılar tarafından girilen özel bir birleşimidir. Paketleme sırasında, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] paketlenmiş bildirim dosyasını oluşturmak için özel deyimleri tasarımcı tarafından belirtilen şekilde birleştirir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . Daha sonra birleştirme özel durumları 'nda belirtilen özel durumlarla benzer öğeler, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dosyaları SharePoint dağıttıktan sonra doğrulama hatalarından kaçınmak ve bildirim dosyalarını daha küçük ve daha verimli hale getirmek için birleştirilir.

## <a name="modify-the-manifests"></a>Bildirimleri değiştirme
 Özelliği veya paket tasarımcılarını devre dışı bırakana kadar paketlenmiş bildirim dosyalarını doğrudan değiştiremezsiniz. Ancak, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] özellik ve paket tasarımcıları ya da düzenleyici aracılığıyla bildirim şablonuna el ile özel öğeler ekleyebilirsiniz [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . daha fazla bilgi için bkz. [nasıl yapılır: özelleştirme SharePoint özellikleri](../sharepoint/how-to-customize-a-sharepoint-feature.md) ve [nasıl yapılır: SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Özellik ve paket bildirimi birleştirme işlemi
 Özel öğeleri tasarımcı tarafından belirtilen öğelerle birlikte birleştirilirken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aşağıdaki işlemi kullanır. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Her bir öğenin benzersiz bir anahtar değeri olup olmadığını denetler. Bir öğenin benzersiz anahtar değeri yoksa, paketlenmiş bildirim dosyasına eklenir. Benzer şekilde, birden fazla anahtara sahip öğeler birleştirilemez. Bu nedenle, bildirim dosyasına eklenir.

 Bir öğe benzersiz bir anahtara sahipse, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcı ve özel anahtarların değerlerini karşılaştırır. Değerler eşleşiyorsa, tek bir değer birleştirir. Değerler farklıysa, tasarımcı anahtar değeri atılır ve özel anahtar değeri kullanılır. Koleksiyonlar da birleştirilir. Örneğin, tasarımcı tarafından oluşturulan [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ve Custom [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] her ikisi de bir derlemeler koleksiyonu içeriyorsa, paketlenmiş bildirim yalnızca bir derlemeler koleksiyonu içerir.

## <a name="merge-exceptions"></a>Özel durumları Birleştir
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] birçok tasarımcı [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] öğesini, benzer özel öğelerle birlikte birleştirerek [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , tek, benzersiz bir tanımlayıcı özniteliği oldukları sürece. Ancak, bazı öğeler birleştirme için gerekli benzersiz tanımlayıcı olmamasıdır [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . Bu öğeler *birleştirme özel durumları* olarak bilinir. Bu durumlarda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] öğeleri tasarımcı tarafından sağlanmış öğelerle birleştirmez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , bunun yerine bunları paketlenmiş bildirim dosyasına ekler.

 Özellik ve paket bildirim dosyaları için birleştirme özel durumlarının listesi aşağıda verilmiştir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Tasarımcı|XML öğesi|
|--------------|-----------------|
|Özellik Tasarımcısı|ActivationDependency|
|Özellik Tasarımcısı|UpgradeAction|
|Paket Tasarımcısı|SafeControl|
|Paket Tasarımcısı|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Özellik bildirim öğeleri
 Aşağıdaki tablo, birleştirilebilen tüm özellik bildirim öğelerinin ve eşleme için kullanılan benzersiz anahtarının bir listesidir.

|Öğe Adı|Benzersiz Anahtar|
|------------------|----------------|
|Özellik (tüm öznitelikler)|*Öznitelik adı* (özellik öğesinin her öznitelik adı, benzersiz bir anahtardır.)|
|ElementFile|Konum|
|Elementbildirimleri/ElementManifest|Konum|
|Özellikler/özellik|Anahtar|
|CustomUpgradeAction|Name|
|CustomUpgradeActionParameter|Name|

> [!NOTE]
> CustomUpgradeAction öğesini değiştirmek için tek yol özel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] düzenleyicide olduğu için, birleştirmenin etkisi düşüktür.

## <a name="package-manifest-elements"></a>Paket bildirim öğeleri
 Aşağıdaki tablo, birleştirilebilen tüm paket bildirim öğelerinin ve eşleme için kullanılan benzersiz anahtarının bir listesidir.

|Öğe Adı|Benzersiz Anahtar|
|------------------|----------------|
|Çözüm (tüm öznitelikler)|*Öznitelik adı* (çözüm öğesinin her öznitelik adı benzersiz bir anahtardır.)|
|ApplicationResourceFiles/ApplicationResourceFile|Konum|
|Derlemeler/derleme|Konum|
|ClassResources/ClassResource|Konum|
|DwpFiles/DwpFile|Konum|
|Özellik bildirimleri/FeatureManifest|Konum|
|Kaynaklar/kaynak|Konum|
|RootFiles/RootFile|Konum|
|Sitedefinitionbildirimleri/SiteDefinitionManifest|Konum|
|WebTempFile|Konum|
|TemplateFiles/TemplateFile|Konum|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Dağıtılan dosyaları el ile ekleme
 ApplicationResourceFile ve DwpFiles gibi bazı bildirim öğeleri, dosya adı içeren bir konum belirtir. Ancak, bildirim şablonuna bir dosya adı girdisi eklemek, temeldeki dosyayı pakete eklemez. Dosyayı pakete dahil etmek için projeye eklemeniz ve dağıtım türü özelliğini buna göre ayarlamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
