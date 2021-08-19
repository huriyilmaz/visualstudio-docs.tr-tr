---
title: Özellik ve Paket Bildirimleri belgesinde XML'i birleştirme | Microsoft Docs
description: Tasarımcı tarafından oluşturulan ve kullanıcı tarafından eklenen XML kodunu, SharePoint ve paket bildirimlerini birleştirin. Özellik ve paket bildirimi öğelerini öğrenin ve özel durumları birleştirin.
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
ms.openlocfilehash: 1e2150995946039bef9dbb4d77c64f8bbb33bf8f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156298"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Özellik ve paket bildirimlerini XML birleştirme
  Özellikler ve paketler bildirim dosyaları [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tarafından tanımlanır. Bu paketlenmiş bildirim, tasarımcılar tarafından oluşturulan ve kullanıcılar tarafından bildirim şablonuna girilen özel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] verilerin bir birleşimidir. Paketleme zamanında, paketlenmiş bildirim dosyasını oluşturmak için özel deyimleri tasarımcı tarafından sağlanan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] deyimlerle birler. Benzer öğeler, Özel Durumları Birleştir'de daha sonra not ettiği özel durumlarla birlikte, dosyaları SharePoint'ye dağıtarak doğrulama hatalarını önlemek ve bildirim dosyalarını daha küçük ve daha verimli hale [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] getirir.

## <a name="modify-the-manifests"></a>Bildirimleri değiştirme
 Özellik veya paket tasarımcıları devre dışı bırakmadan paketli bildirim dosyalarını doğrudan değiştiremezsiniz. Ancak, özellik ve paket [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tasarımcıları veya düzenleyici aracılığıyla bildirim şablonuna el ile özel öğeler [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ekleyebilirsiniz. Daha fazla bilgi için [bkz. Nasıl SharePoint:](../sharepoint/how-to-customize-a-sharepoint-feature.md) SharePoint Özelliği [Özelleştirme: Bir SharePoint paketini özelleştirme.](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)

## <a name="feature-and-package-manifest-merge-process"></a>Özellik ve paket bildirimi birleştirme işlemi
 Özel öğeleri tasarımcı tarafından sağlanan öğelerle birlikte birleştirerek [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aşağıdaki işlemi kullanır. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] her öğenin benzersiz bir anahtar değeri olup olmadığını denetler. Bir öğenin benzersiz anahtar değeri yoksa, paketli bildirim dosyasına eklenir. Benzer şekilde, birden çok anahtara sahip öğeler birleştirilemez. Bu nedenle, bildirim dosyasına eklenirler.

 Bir öğe benzersiz bir anahtara [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sahipse, tasarımcının ve özel anahtarların değerlerini karşılar. Değerler eşleşiyorsa, tek bir değerde birleşiyor. Değerler farklı olursa tasarımcı anahtarı değeri atılır ve özel anahtar değeri kullanılır. Koleksiyonlar da birleştirilir. Örneğin, tasarımcı tarafından oluşturulan ve özel her ikisi de bir Derlemeler koleksiyonu içeriyorsa, paketlenmiş bildirim yalnızca [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bir Derleme koleksiyonu içerir.

## <a name="merge-exceptions"></a>Birleştirme özel durumları
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tek, benzersiz bir tanımlayıcı özniteliği olduğu sürece çoğu tasarımcı öğelerini benzer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] özel öğelerle bir araya sağlar. Ancak, bazı öğeler birleştirme için gereken benzersiz [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tanımlayıcıya sahip değildir. Bu öğeler birleştirme özel *durumları olarak bilinir.* Bu durumlarda, özel öğeleri tasarımcı tarafından sağlanan öğelerle birleştirmez, bunun yerine bunları paketlenmiş [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bildirim dosyasına [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ekler.

 Aşağıda, özellik ve paket bildirim dosyaları için birleştirme özel durumlarının [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] listesi ve ardından yer almaktadır.

|Tasarımcı|XML Öğesi|
|--------------|-----------------|
|Özellik tasarımcısı|ActivationDependency|
|Özellik tasarımcısı|UpgradeAction|
|Paket tasarımcısı|SafeControl|
|Paket tasarımcısı|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Özellik bildirimi öğeleri
 Aşağıdaki tablo, birleştirilecek tüm özellik bildirimi öğelerinin ve eşleştirme için kullanılan benzersiz anahtarlarının bir listesidir.

|Öğe Adı|Benzersiz Anahtar|
|------------------|----------------|
|Özellik (tüm öznitelikler)|*Öznitelik Adı* (Özellik öğesinin her öznitelik adı benzersiz bir anahtardır.)|
|ElementFile|Konum|
|ElementManifests/ElementManifest|Konum|
|Özellikler/Özellik|Anahtar|
|CustomUpgradeAction|Name|
|CustomUpgradeActionParameter|Name|

> [!NOTE]
> CustomUpgradeAction öğesini değiştirmenin tek yolu özel düzenleyicide olduğu için [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] birleştirmeme etkisi düşüktür.

## <a name="package-manifest-elements"></a>Paket bildirimi öğeleri
 Aşağıdaki tablo, birleştirilecek tüm paket bildirimi öğelerinin ve eşleştirme için kullanılan benzersiz anahtarlarının bir listesidir.

|Öğe Adı|Benzersiz Anahtar|
|------------------|----------------|
|Çözüm (tüm öznitelikler)|*Öznitelik Adı* (Çözüm öğesinin her öznitelik adı benzersiz bir anahtardır.)|
|ApplicationResourceFiles/ApplicationResourceFile|Konum|
|Derlemeler/Derlemeler|Konum|
|ClassResources/ClassResource|Konum|
|DwpFiles/DwpFile|Konum|
|FeatureManifests/FeatureManifest|Konum|
|Kaynaklar/Kaynak|Konum|
|RootFiles/RootFile|Konum|
|SiteDefinitionManifests/SiteDefinitionManifest|Konum|
|WebTempFile|Konum|
|TemplateFiles/TemplateFile|Konum|
|Çözüm Bağımlılığı|SolutionID|

## <a name="manually-add-deployed-files"></a>Dağıtılan dosyaları el ile ekleme
 ApplicationResourceFile ve DwpFiles gibi bazı bildirim öğeleri, dosya adı içeren bir konum belirtir. Ancak, bildirim şablonuna dosya adı girişi eklemek, temel alınan dosyayı pakete eklemez. Paketin içinde yer alan dosyayı projeye eklemeniz ve Dağıtım Türü özelliğini uygun şekilde ayarlamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Çözüm oluşturma ve SharePoint ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
