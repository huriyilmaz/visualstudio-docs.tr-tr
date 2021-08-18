---
title: VSIX Dil Paketi Şeması 2.0 Başvuru | Microsoft Docs
description: VSIX Dil Paketi şeması, VSIX paketleri için yerelleştirilmiş yükleme bilgileri sağlar. Sürüm 2.0, ek yerelleştirme öğelerini destekler.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.openlocfilehash: 8ade27ac47c25a3170c5c7c6048aa1c6c21181e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109896"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX dil paketi şeması 2.0 başvurusu

VSIX Dil Paketi şeması, VSIX paketleri için yerelleştirilmiş yükleme bilgileri sağlar. Bu şemanın 2.0 sürümü ek yerelleştirme öğelerini destekler.

## <a name="language-pack-schema"></a>Dil paketi şeması

Dil paketi dosyasının kök öğesi, `<PackageLanguagePackManifest>` dil paketi biçiminin `Version` sürümü olan özniteliğine sahip olan öğesidir. Bu makalede, özniteliği değerine ayarlanıp bildirimde belirtilen dil paketi biçiminin 2.0 `Version` sürümü `Version="2.0.0"` açıklanmıştır. Kök öğe tam olarak bir alt öğe `<Metadata>` içerir.

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest öğesi

öğesinin `<PackageLanguagePackManifest>` içinde aşağıdaki öğenin mevcut olması gerekir:

|Başlık|Açıklama|
|-----------|-----------------|
|`<Metadata>`| Tüm yerelleştirilmiş paket meta verileri için içeren öğesi

### <a name="metadata-element"></a>Meta veri öğesi

öğesinin `<Metadata>` içinde aşağıdaki öğelere sahip olabilir:

|Başlık|Açıklama|
|-----------|-----------------|
|`<DisplayName>`|Yüklenilecek uzantının yerelleştirilmiş adı|
|`<Description>`|Yüklenilecek uzantının yerelleştirilmiş açıklaması|
|`<License>`| Uzantı lisansının yerelleştirilmiş sürümünün yolu|
|`<MoreInfo>`| Uzantı hakkında yerelleştirilmiş bilgilerin bağlantısı|
|`<ReleaseNotes>`| Sürüm notlarının yerelleştirilmiş bir sürümüne giden yol veya bağlantı|
|`<Icon>`| Uzantılar simgesinin yerelleştirilmiş sürümüne giden yol|

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
|[VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)|VSIX paketi için yerelleştirilmiş yükleme desteği sağlamayı gösterir.|
|[VSIX uzantı şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX bildirimi bir *.vsix* dağıtım dosyasının içeriğini açıklar. Dağıtım dosyası, Uzantılar ve Güncelleştirmeler iletişim kutusunu Visual Studio bir uzantı **yüklemenize** olanak sağlar.|
|[Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)|Uzantıları yüklemek, **kaldırmak, etkinleştirmek ve devre** dışı bırakmak için Uzantılar ve Güncelleştirmeler iletişim kutusunu kullanmayı gösterir.|
