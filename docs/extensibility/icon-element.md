---
title: Icon Öğesi | Microsoft Docs
description: Kullanılan bit eşlem ve bit eşlem şeridinde yuva Visual Studio IDE uzantılarında kullanılan simgeleri temsil eden Icon öğesini öğrenin.
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
ms.openlocfilehash: 26f942461a8d9be31e7802fb63f0249b69046663
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626223"
---
# <a name="icon-element"></a>Simge öğesi
Icon etiketinin guid özniteliği, tanımlı bir bit eşlem guid değeridir. özniteliği `id` bit eşlem şeridinde yuvayı seçer. Bu öğe isteğe bağlıdır. Bu öğe dahil yoksa **guidOfficeIcon:msotcidNoIcon değeri** örtüşecek.

## <a name="syntax"></a>Syntax

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. Tanımlı bir bit eşlem guid'si.|
|kimlik|Gereklidir. Bit eşlem şeridinde yuvayı seçer.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.|Yok.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
