---
title: VSIX Paketlerinin Yerelleştirilmesi | Microsoft Dokümanlar
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702895"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme

Her hedef dil için bir *Extension.vsixlangpack* dosyası oluşturup doğru klasöre koyarak bir VSIX paketini yerelleştirebilirsiniz. Yerelleştirilmiş bir paket yüklendiğinde, uzantının yerelleştirilmiş adı yerelleştirilmiş bir açıklamayla birlikte görüntülenir. Yerelleştirilmiş bir lisans dosyası veya yerelleştirilmiş bilgilere işaret eden bir URL sağlarsanız, bunlar da görüntülenir.

VSIX paketinizin içeriği menü komutları veya başka kullanıcı arabirimi ekleyen bir VSPackage içeriyorsa, yeni Kullanıcı Arabirimi öğelerini yerelleştirme hakkında bilgi için [yerelleştir menüsü komutlarına](../extensibility/localizing-menu-commands.md) bakın.

## <a name="directory-structure"></a>Dizin yapısı

 Bir kullanıcı bir uzantı yüklediğinde, **Uzantılar ve Güncelleştirmeler,** vsix paketinin üst düzeyini, adı hedef bilgisayarın Visual Studio yerel alanıyla eşleşen bir klasör için denetler. **Uzantılar ve Güncelleştirmeler** klasörde bir *.vsixlangpack* dosyası bulursa, o dosyadaki yerelleştirilmiş değerleri *.vsixmanifest* dosyasındaki karşılık gelen değerleryerine verir. Uzantı yüklenirken bu değerler görüntülenir. Aşağıdaki örnek, İspanyolca (es-ES) ve Fransızca (fr-FR) olarak yerelleştirilmiş bir VSIX paketinin dizin yapısını gösterir.

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
> VSIX destekli proje şablonları bir [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX bildirimi oluşturmak ve *source.extension.vsixmanifest*adı . Visual Studio projeyi oluşturduğunda, bu dosyanın içeriğini VSIX paketinde Extension.VsixManifest olarak kopyalar.

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack dosyası

*Extension.vsixlangpack* dosyası [VSIX Dil Paketi şema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)izler. Bu şema bir `PackageLanguagePackManifest`, hemen bir `Metadata` çocuk öğesi tarafından takip edilir. Metaveri öğesi en fazla 6 alt `DisplayName` `Description`öğe `MoreInfo` `License`içerebilir, , , `ReleaseNotes`, , ve `Icon`. Bu `DisplayName`alt `Description` *öğeler, Extension.vsixmanifest* dosyasının `Metadata` öğesinin , , `MoreInfo` `License`, , `ReleaseNotes`ve `Icon` alt öğelerine karşılık gelir.

Bir vsixlangpack dosyası oluşturduğunuzda, `Include in Vsix` özelliği `true`' ye ayarlamanız gerekir. Aksi takdirde, yerelleştirilmiş yükleme metni yoksayılır.

### <a name="to-set-the-include-in-vsix-property"></a>Vsix özelliğine Ekle'yi ayarlamak için

1. **Çözüm Gezgini'nde,** Extension.vsixlangpack dosyasına sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Özellik **Izgara'sında** **Vsix'e Ekle'yi**tıklatın ve değerini `true`.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, *Bir Extension.vsixmanifest* dosyasının ilgili bölümlerini gösterir. Dosya da İspanyolca için ilgili *Extension.vsixlangpack* dosyaiçerir. Hedef bilgisayarın Visual Studio yerel bilgisayarı İspanyolca olarak ayarlanmışsa, dil paketindeki değerler bildirimdeki değerleri değiştirir.

### <a name="code"></a>Kod

- [*Uzantı.vsixmanifest*]

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

- [*Uzantı.vsixlangpack*]

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
|[VSIX Dil Paketi şema 2.0 referans](vsix-language-pack-schema-2-0-reference.md)|VSIX dil paketi,.vsix dağıtım dosyasının yerelleştirme bilgilerini açıklar.|
|[VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSix paketinin yapısını ve içeriğini açıklar.|
|[Menü komutlarını yerelleştir](../extensibility/localizing-menu-commands.md)|Uzantıdaki diğer metin kaynaklarını nasıl yerelleştirini gösterir.|
