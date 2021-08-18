---
title: Üst Öğe | Microsoft Docs
description: Parent öğesi bir öğenin düğme, birleşik giriş kutusu, menü veya grubun üst öğesi olduğunu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cb2ce0ddcf779d5c6c9e0b880d99f169d762065d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152074"
---
# <a name="parent-element"></a>Üst öğe
Bir düğmenin veya birleşik giriş kutusunun üst öğesi yalnızca bir grup olabilir. Bir menü veya grubun üst öğesi başka bir menü veya grup olabilir. Bir [CommandPlacement öğesinde](../extensibility/commandplacement-element.md)bu öğe gereklidir; diğer tüm örneklerde isteğe bağlıdır. Bu öğe atlanırsa üst öğesi `Group_Undefined:0` kullanılır.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|

### <a name="child-elements"></a>Alt öğeleri
 Hiçbiri

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin menü öğeleri, menüler, araç çubukları ve birleşik giriş kutuları.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Gruplar [Düğmesi öğesi](../extensibility/button-element.md) öğeleri.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri tanımlar.|
|[Groups öğesi](../extensibility/groups-element.md)|VSPackage'ın komut gruplarını tanımlayan girdileri içerir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
