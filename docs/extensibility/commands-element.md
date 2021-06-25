---
title: Commands Öğesi | Microsoft Docs
description: 'Commands öğesi VSPackage araç çubuğundaki komut koleksiyonunu temsil eder ve şu bölümlere sahip olabilir: menüler, gruplar, düğmeler, birleşik girişler ve bit eşlemler.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4c7b058acdd634079d0ca60dddb9f80e0e26ff0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901880"
---
# <a name="commands-element"></a>Commands öğesi
VSPackage araç çubuğunda komut koleksiyonunu temsil eder. Koleksiyonda en fazla beş alt bölüm olabilir: menüler, gruplar, düğmeler, birleşik girişler ve bit eşlemler.

 Örneğin her alt bölüm alt öğesi, GUID ve sayısal tanımlayıcı \<Menu> çifti olan benzersiz bir komut kimliğiyle tanımlanır. GUID , "komut kümesi" tanımlar ve mantıksal olarak ilgili komutları gruplatır. VSPackage, diğer VSPackage'lar tarafından tanımlanan komut kimlikleriyle çakışmaları önlemek için kendi komut kümesi tanımlamalı.

## <a name="syntax"></a>Syntax

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|package|Komutları sağlayan VSPackage'i tanımlayan GUID.<br /><br /> Örneğin, package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri tanımlar.|
|[Groups öğesi](../extensibility/groups-element.md)|VSPackage'da komut gruplarını tanımlayan girdileri içerir.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Gruplar Düğmesi öğeleri.|
|[Bitmaps öğesi](../extensibility/bitmaps-element.md)|Bit Eşlem öğelerini gruplar.|
|[Combos öğesi](../extensibility/combos-element.md)|Gruplar Birleşik öğeler.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın IDE'ye sağladığı komutları temsil eden tüm öğeleri tanımlar. Olası öğeler menü öğeleri, menüler, araç çubukları ve birleşik giriş kutularıdır.|

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir Commands Öğesinin nasıl [kullanımı gösterir.](../extensibility/commands-element.md)

```
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
