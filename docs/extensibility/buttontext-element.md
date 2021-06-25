---
title: ButtonText Öğesi | Microsoft Docs
description: ButtonText öğesi, çeşitli menülerde görünen metni belirtmenize olanak sağlar. Diğer metin alanları belirtilmiş olsa bile ButtonText öğesi boş olamaz.
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
ms.workload:
- vssdk
ms.openlocfilehash: cf20a6876dd7ba52413a11f30a3d0130b32e535d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900726"
---
# <a name="buttontext-element"></a>ButtonText öğesi
Bu alan, çeşitli menülerde görünen metni belirtmenize olanak sağlar. Varsayılan olarak, öğesi `ButtonText` menü denetleyicilerinde görünür. Diğer `ButtonText` metin alanları boşsa, öğesi de varsayılan olur. Diğer `ButtonText` metin alanları belirtilmiş olsa bile öğesi boş olamaz.

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
|[Strings Öğesi](../extensibility/strings-element.md)|ve gibi metin öğelerini `ButtonText` `CommandName` gruplar.|

## <a name="text-value"></a>Metin değeri
 öğesinin metin değeri menü öğeleri, birleşik girişler ve görünür metinler olan diğer kullanıcı arabirimi `ButtonText` (UI) öğeleri için görüntülenen metni sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
