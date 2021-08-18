---
title: VSIX Paketlerini Yerelleştirme | Microsoft Docs
description: Her hedef dil için bir Extension.vsixlangpack dosyası oluşturarak ve sonra bunları doğru klasöre koyarak VSIX paketini yerelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c818c05831f48875c1ad15c47d3d5f3c1610997e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152230"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme

Her hedef dil için bir *Extension.vsixlangpack* dosyası oluşturarak ve sonra bunları doğru klasöre koyarak bir VSIX paketini yerelleştirebilirsiniz. Yerelleştirilmiş bir paket yüklenirken, uzantının yerelleştirilmiş adı yerelleştirilmiş bir açıklamayla birlikte görüntülenir. Yerelleştirilmiş bir lisans dosyası veya yerelleştirilmiş bilgilere yönelik bir URL sağlarsanız bunlar da görüntülenir.

VSIX paketinizin içeriği menü komutları veya başka bir kullanıcı arabirimi [](../extensibility/localizing-menu-commands.md) ekleyen bir VSPackage içerirse, yeni kullanıcı arabirimi öğelerini yerelleştirme hakkında bilgi için bkz. Menü komutlarını yerelleştirme.

## <a name="directory-structure"></a>Dizin yapısı

 Kullanıcı bir uzantı yüklemiş olduğunda **Uzantılar** ve Güncelleştirmeler, adı hedef bilgisayarın yerel Visual Studio ile eşleşen bir klasör için VSIX paketinin en üst düzeyini denetler. Uzantılar **ve Güncelleştirmeler** klasöründe *bir .vsixlangpack* dosyası bulursa, *.vsixmanifest* dosyasındaki karşılık gelen değerler için bu dosyada yerelleştirilmiş değerlerin yerini alır. Uzantı yüklenirken bu değerler görüntülenir. Aşağıdaki örnek, İspanyolca (es-ES) ve Fransızca (fr-FR) olarak yerelleştirilmiş bir VSIX paketinin dizin yapısını gösterir.

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> içinde VSIX tarafından desteklenen proje şablonları bir VSIX bildirimi oluşturur ve [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] *source.extension.vsixmanifest olarak adlar.* Proje Visual Studio, bu dosyanın içeriğini VSIX paketinde Extension.VsixManifest'e kopyalar.

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack dosyası

*Extension.vsixlangpack dosyası* VSIX Dil Paketi şeması [2.0'ı izler.](../extensibility/vsix-language-pack-schema-2-0-reference.md) Bu şemada `PackageLanguagePackManifest` hemen ardından bir alt öğe gelen bir `Metadata` vardır. Metadata öğesi en fazla 6 alt öğe içerebilir: `DisplayName` , , , , , ve `Description` `MoreInfo` `License` `ReleaseNotes` `Icon` . Bu alt öğeler `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` `Icon` `Metadata` *Extension.vsixmanifest* dosyasının öğesinin , , , , ve alt öğelerine karşılık gelen öğelerdir.

Vsixlangpack dosyası oluşturdukta özelliğini olarak `Include in Vsix` `true` ayarlayabilirsiniz. Aksi takdirde, yerelleştirilmiş yükleme metni yoksayılır.

### <a name="to-set-the-include-in-vsix-property"></a>Vsix'e Dahil Etmek özelliğini ayarlamak için

1. Bu **Çözüm Gezgini** Extension.vsixlangpack dosyasına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Property **Grid'de** **Vsix'e Ekle'ye tıklayın** ve değerini olarak `true` ayarlayın.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, *extension.vsixmanifest dosyasının ilgili bölümlerini* gösterir. Dosya ayrıca İspanyolca için ilgili *Extension.vsixlangpack* dosyasını da içerir. Hedef bilgisayarın yerel ayar İspanyolca olarak ayarlanırsa, dil paketinden Visual Studio bildirim değerleri değiştirilir.

### <a name="code"></a>Kod

- [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension.vsixlangpack*]

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
|[VSIX Dil Paketi şema 2.0 başvurusu](vsix-language-pack-schema-2-0-reference.md)|VSIX dil paketi, bir .vsix dağıtım dosyasının yerelleştirme bilgilerini açıklar.|
|[VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|Vsix paketinin yapısını ve içeriğini açıklar.|
|[Menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md)|Uzantıda diğer metin kaynaklarını yerelleştirmeyi gösterir.|
