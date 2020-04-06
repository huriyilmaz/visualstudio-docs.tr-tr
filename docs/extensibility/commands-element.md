---
title: Komutlar Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739691"
---
# <a name="commands-element"></a>Komutlar öğesi
VSPackage araç çubuğundaki komutların toplanmasını temsil eder. Koleksiyonda aşağıdaki gibi en fazla beş alt bölüm olabilir: menüler, gruplar, düğmeler, kombinasyonlar ve bit eşlemler.

 Her alt bölüm alt \<öğesi, örneğin, Menü>, bir GUID ve sayısal tanımlayıcı çifti benzersiz bir komut kimliği ile tanımlanır. GUID "komut kümesini" tanımlar ve mantıksal olarak ilişkili komutları gruplandırmak için kullanılır. VSPackage, diğer VSPackages tarafından tanımlanan komut iD'leriyle çakışmaları önlemek için kendi komut kümesini tanımlamalıdır.

## <a name="syntax"></a>Sözdizimi

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
|Paket|Komutları sağlayan VSPackage'ı tanımlayan bir GUID.<br /><br /> Örneğin, paket="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uyguladığı tüm menüleri tanımlar.|
|[Gruplar öğesi](../extensibility/groups-element.md)|VSPackage'daki komut gruplarını tanımlayan girişler içerir.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğelerini grupla.|
|[Biteşler öğesi](../extensibility/bitmaps-element.md)|Bitmap öğelerini gruplar.|
|[Kombinasyon öğesi](../extensibility/combos-element.md)|Combo öğelerini gruplar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın IDE'ye sağladığı komutları temsil eden tüm öğeleri tanımlar. Olası öğeler menü öğeleri, menüler, araç çubukları ve açılan kutulardır.|

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [KomutLar Öğesi'nin](../extensibility/commands-element.md)nasıl kullanılacağını gösterir.

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
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
