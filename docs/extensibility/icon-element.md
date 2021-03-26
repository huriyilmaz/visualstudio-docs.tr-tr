---
title: Icon öğesi | Microsoft Docs
description: Kullanılan bit eşlem ve bit eşlem şeridindeki yuva özniteliklerini içeren Visual Studio IDE uzantılarında kullanılan simgeleri temsil eden Icon öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52ccb8093b61e0458f7c3caefea6f826609aa51d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082146"
---
# <a name="icon-element"></a>Icon öğesi
Simge etiketinin GUID özniteliği, tanımlı bir bit eşlemin GUID 'sidir. `id`Özniteliği, bit eşlem şeridinde yuva seçer. Bu öğe isteğe bağlıdır. Bu öğe GuidOfficeIcon değerini içeriyorsa, **Msotcıdnoıcon** dahil edilir.

## <a name="syntax"></a>Syntax

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. Tanımlı bir bit eşlemin GUID 'si.|
|kimlik|Gereklidir. Bit eşlem şeridinde yuva seçer.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.|Yok.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
