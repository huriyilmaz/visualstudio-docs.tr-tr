---
title: VSıX dil paketi şeması 2,0 başvurusu | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: f0eee51c0654c6e517209e23baf43c6b262d8f73
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830710"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSıX dil paketi şeması 2,0 başvurusu

VSıX dil paketi şeması, VSıX paketleri için yerelleştirilmiş yükleme bilgilerini sağlar. Bu şemanın sürüm 2,0, ek yerelleştirme öğelerini destekler.

## <a name="language-pack-schema"></a>Dil paketi şeması

Dil paketi dosyasının kök öğesi, `<PackageLanguagePackManifest>` `Version` dil paketi biçiminin sürümü olan öğesinin bir özniteliğiyle birlikte bulunur. Bu makalede, özniteliği değere ayarlanarak bildirimde belirtilen dil paketi biçiminin 2,0 sürümü açıklanır `Version` `Version="2.0.0"` . Kök öğesi tam olarak bir alt `<Metadata>` öğe içeriyor.

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest öğesi

Öğesi içinde `<PackageLanguagePackManifest>` Aşağıdaki öğe var olmalıdır:

|Başlık|Açıklama|
|-----------|-----------------|
|`<Metadata>`| Tüm yerelleştirilmiş paket meta verileri için kapsayan öğe

### <a name="metadata-element"></a>Metadata öğesi

Öğesi içinde `<Metadata>` aşağıdaki öğelere sahip olabilirsiniz:

|Başlık|Açıklama|
|-----------|-----------------|
|`<DisplayName>`|Yüklenecek uzantının yerelleştirilmiş adı|
|`<Description>`|Yüklenecek uzantının yerelleştirilmiş açıklaması|
|`<License>`| Uzantının lisansının yerelleştirilmiş bir sürümünün yolu|
|`<MoreInfo>`| Uzantı ile ilgili yerelleştirilmiş bilgilere bir bağlantı|
|`<ReleaseNotes>`| Sürüm notlarının yerelleştirilmiş bir sürümüne yol veya bağlantı|
|`<Icon>`| Uzantılar simgesinin yerelleştirilmiş bir sürümünün yolu|

### <a name="sample-manifest"></a>Örnek bildirim

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Ayrıca bkz.

|Başlık|Açıklama|
|-----------|-----------------|
|[VSıX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)|Bir VSıX paketi için yerelleştirilmiş yükleme desteğinin nasıl sağlanması gerektiğini gösterir.|
|[VSıX uzantı Şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)|VSıX bildirimi bir *. VSIX* dağıtım dosyasının içeriğini açıklar. Dağıtım dosyası, **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanarak bir Visual Studio uzantısı yüklemenizi sağlar.|
|[Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)|Uzantılar **ve güncelleştirmeler** iletişim kutusunun uzantıları yüklemek, kaldırmak, etkinleştirmek ve devre dışı bırakmak için nasıl kullanılacağını gösterir.|
