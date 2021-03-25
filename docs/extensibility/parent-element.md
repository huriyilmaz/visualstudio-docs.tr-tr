---
title: Üst öğe | Microsoft Docs
description: Üst öğe, bir öğenin bir düğme, Birleşik giriş kutusu, menü veya grubun üst öğesi olduğunu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac914fd3245982af89facb97ff2d528b410da99
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090388"
---
# <a name="parent-element"></a>Üst öğe
Bir düğme veya Birleşik giriş kutusunun üst öğesi yalnızca bir grup olabilir. Bir menünün veya grubun üstü başka bir menü veya grup olabilir. [Commandyerleştirme öğesinde](../extensibility/commandplacement-element.md)bu öğe gereklidir; diğer tüm örneklerde, bu isteğe bağlıdır. Bu öğe atlanırsa, üst öğesi de `Group_Undefined:0` kapsanır.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|

### <a name="child-elements"></a>Alt öğeleri
 Yok

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Gruplar [düğme öğesi](../extensibility/button-element.md) öğeleri.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|
|[Groups öğesi](../extensibility/groups-element.md)|VSPackage 'un komut gruplarını tanımlayan girişleri içerir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
