---
title: VSıX paketlerini yerelleştirme | Microsoft Docs
description: Her hedef dil için bir Extension. valtlangpack dosyası oluşturarak ve bunları doğru klasöre yerleştirerek bir VSıX paketini nasıl yerelleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d55acd30a0ea5381e9b14cf10c952c5626922c22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893613"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme

Her hedef dil için bir *extension. valtlangpack* dosyası oluşturarak ve ardından bunları doğru klasöre YERLEŞTIREREK bir VSIX paketini yerelleştirebilirsiniz. Yerelleştirilmiş bir paket yüklendiğinde, uzantının yerelleştirilmiş adı yerelleştirilmiş bir açıklamayla birlikte görüntülenir. Yerelleştirilmiş bir lisans dosyası ya da yerelleştirilmiş bilgilere işaret eden bir URL sağlarsanız, bunlar da görüntülenir.

VSıX paketinizin içeriği menü komutları veya diğer kullanıcı arabirimi ekleyen bir VSPackage içeriyorsa, yeni kullanıcı arabirimi öğelerini yerelleştirme hakkında bilgi için bkz. [yerelleştirmek menü komutları](../extensibility/localizing-menu-commands.md) .

## <a name="directory-structure"></a>Dizin yapısı

 Kullanıcı bir uzantı yüklediğinde, **Uzantılar ve güncelleştirmeler** adı hedef bilgisayarın Visual Studio yerel ayarıyla eşleşen bir klasör için VSIX paketinin en üst düzeyini denetler. **Uzantılar ve güncelleştirmeler** klasörde bir *. valtlangpack* dosyası bulursa, *. valtmanifest* dosyasındaki karşılık gelen değerler için bu dosyadaki yerelleştirilmiş değerleri değiştirir. Bu değerler, uzantı yüklenirken görüntülenir. Aşağıdaki örnek, Ispanyolca (ES-ES) ve Fransızca (fr-FR) olarak yerelleştirilmiş bir VSıX paketinin dizin yapısını gösterir.

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
> VSıX için desteklenen proje şablonları [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] BIR VSIX bildirimi oluşturur ve bunu *kaynak. Extension. valtmanifest* olarak adlandırın. Visual Studio projeyi oluşturduğunda, bu dosyanın içeriğini VSıX paketindeki. Valtmanifest uzantısına kopyalar.

## <a name="the-extensionvsixlangpack-file"></a>. Valtlangpack dosyası uzantısı

*Uzantı. valtlangpack* dosyası [VSIX dil paketi şeması 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md)' i izler. Bu şemada `PackageLanguagePackManifest` , hemen arkasından bir `Metadata` alt öğe gelen bir öğesi vardır. Meta veri öğesi en fazla 6 alt öğe içerebilir,,,, `DisplayName` `Description` `MoreInfo` `License` , `ReleaseNotes` ve `Icon` . Bu alt öğeler `DisplayName` , `Description` `MoreInfo` `License` `ReleaseNotes` `Icon` `Metadata` *uzantısı. valtmanifest* dosyası öğesinin,,,, ve alt öğelerine karşılık gelir.

Bir valtlangpack dosyası oluşturduğunuzda, `Include in Vsix` özelliğini olarak ayarlamanız gerekir `true` . Aksi takdirde, yerelleştirilmiş yükleme metni yok sayılır.

### <a name="to-set-the-include-in-vsix-property"></a>VSIX özelliğinde Içerme özelliğini ayarlamak için

1. **Çözüm Gezgini**, Extension. valtlangpack dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik kılavuzunda** **VSIX 'e Ekle**' ye tıklayın ve değerini olarak ayarlayın `true` .

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Aşağıdaki örnekte bir *extension. valtmanifest* dosyasının ilgili bölümleri gösterilmektedir. Bu dosya, Ispanyolca için karşılık gelen *extension. valtlangpack* dosyasını da içerir. Dil paketindeki değerler, hedef bilgisayarın Visual Studio yerel ayarı Ispanyolca olarak ayarlandıysa, bildirim içindeki değerleri değiştirin.

### <a name="code"></a>Kod

- [*Extension. valtmanifest*]

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

- [*Extension. valtlangpack*]

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
|[VSıX dil paketi şeması 2,0 başvurusu](vsix-language-pack-schema-2-0-reference.md)|VSıX dil paketi bir. vsix dağıtım dosyasının yerelleştirme bilgilerini tanımlar.|
|[VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)|VSIX paketinin yapısını ve içeriğini açıklar.|
|[Yerelleştirmek menü komutları](../extensibility/localizing-menu-commands.md)|Bir uzantıdaki diğer metin kaynaklarının nasıl yerelleştirileceğini gösterir.|
