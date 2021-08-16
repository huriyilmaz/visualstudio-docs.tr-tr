---
title: Icon öğesi | Microsoft Docs
description: kullanılan bit eşlem ve bit eşlem şeridindeki yuva özniteliklerini içeren Visual Studio ıde uzantılarında kullanılan simgeleri temsil eden ıcon öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 861bca1bc4a0f43f8e5165ae4fdf172fc858dfaf575683a921f52f3428e9c0d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414681"
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
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
