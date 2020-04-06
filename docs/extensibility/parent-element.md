---
title: Üst Öğe | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702227"
---
# <a name="parent-element"></a>Üst öğe
Bir düğmenin veya açılan kutunun üst öğesi yalnızca bir grup olabilir. Bir menünün veya grubun üst öğesi başka bir menü veya grup olabilir. Bir [Komut Yerleştirme öğesinde,](../extensibility/commandplacement-element.md)bu öğe gereklidir; diğer tüm durumlarda isteğe bağlıdır. Bu öğe atlanırsa, üst ima `Group_Undefined:0` edilecektir.

## <a name="syntax"></a>Sözdizimi

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.|
|id|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|

### <a name="child-elements"></a>Alt öğeleri
 None

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve açılan kutular.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Grupları [Düğme öğesi](../extensibility/button-element.md) öğeleri.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uyguladığı tüm menüleri tanımlar.|
|[Gruplar öğesi](../extensibility/groups-element.md)|VSPackage komut gruplarını tanımlayan girişler içerir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
