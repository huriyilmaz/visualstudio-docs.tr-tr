---
title: Groups Öğesi | Microsoft Docs
description: Groups öğesi, VSPackage'ın komut gruplarını tanımlayan girdileri içerir. Bu makale bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 703c0717a93cd2a201bad708830c42497758edb3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087008"
---
# <a name="groups-element"></a>Groups öğesi
VSPackage'ın komut gruplarını tanımlayan girdileri içerir.

## <a name="syntax"></a>Syntax

```xml
<Groups>
  <Group>... </Group>
  <Group>... </Group>
</Groups>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Group öğesi](../extensibility/group-element.md)|Tek bir komut grubunu temsil eder.|
|[Groups öğesi](../extensibility/groups-element.md)|VSPackage'ın komut gruplarını tanımlayan girdileri içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğunda komut koleksiyonunu temsil eder.|

## <a name="example"></a>Örnek

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
