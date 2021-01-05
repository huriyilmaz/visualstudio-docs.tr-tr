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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03f1709184126d31845bfe1145afdebfeffcd1d1
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863336"
---
# <a name="parent-element"></a>Üst öğe
Bir düğme veya Birleşik giriş kutusunun üst öğesi yalnızca bir grup olabilir. Bir menünün veya grubun üstü başka bir menü veya grup olabilir. [Commandyerleştirme öğesinde](../extensibility/commandplacement-element.md)bu öğe gereklidir; diğer tüm örneklerde, bu isteğe bağlıdır. Bu öğe atlanırsa, üst öğesi de `Group_Undefined:0` kapsanır.

## <a name="syntax"></a>Sözdizimi

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
 Hiçbiri

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları.|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Gruplar [düğme öğesi](../extensibility/button-element.md) öğeleri.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|
|[Groups öğesi](../extensibility/groups-element.md)|VSPackage 'un komut gruplarını tanımlayan girişleri içerir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
