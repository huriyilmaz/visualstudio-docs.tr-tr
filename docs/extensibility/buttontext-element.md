---
title: ButtonText öğesi | Microsoft Docs
description: ButtonText öğesi, çeşitli menülerde görüntülenen metni belirtmenize olanak tanır. Başka metin alanları belirtilmiş olsa bile ButtonText öğesi boş olamaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f45a97ca24d61554e5901ed0322e49696dd5375c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133360"
---
# <a name="buttontext-element"></a>ButtonText öğesi
Bu alan, çeşitli menülerde görüntülenen metni belirtmenize olanak tanır. Varsayılan olarak, `ButtonText` öğesi menü denetleyicileri ' nde görünür. `ButtonText`Diğer metin alanları boşsa, öğesi de varsayılan olarak olur. `ButtonText`Diğer metin alanları belirtilmiş olsa bile öğe boş bırakılamaz.

## <a name="syntax"></a>Syntax

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Dizeler öğesi](../extensibility/strings-element.md)|Ve gibi metin öğelerini gruplandırır `ButtonText` `CommandName` .|

## <a name="text-value"></a>Metin değeri
 Öğesinin metin değeri, `ButtonText` menü öğeleri, combos ve görünür metne sahip diğer kullanıcı arabirimi (UI) öğeleri için görüntülenen metni sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
