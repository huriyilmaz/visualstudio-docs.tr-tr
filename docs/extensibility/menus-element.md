---
title: Menü öğesi | Microsoft Docs
description: Menüler öğesi, VSPackage'ın uygulayan tüm menüleri ve araç çubuklarını tanımlar. Bu makale bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7fd8f65c0994ceb500ab389b3437cca85d8030a4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626018"
---
# <a name="menus-element"></a>Menüler öğesi
VSPackage'ın uygulayan tüm menüleri ve araç çubuklarını tanımlar.

## <a name="syntax"></a>Syntax

```xml
<Menus>
  <Menu>... </Menu>
  <Menu>... </Menu>
</Menus>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri ve araç çubuklarını tanımlar.|
|[Menü öğesi](../extensibility/menu-element.md)|Tek bir menüyü veya araç çubuğunu temsil eder.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage'daki komut koleksiyonunu temsil eder.|

## <a name="example"></a>Örnek

```xml
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
