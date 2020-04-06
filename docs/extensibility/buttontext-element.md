---
title: ButtonText Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739914"
---
# <a name="buttontext-element"></a>ButtonText öğesi
Bu alan, çeşitli menülerde görünen metni belirtmenizi sağlar. Varsayılan olarak, `ButtonText` öğe menü denetleyicilerinde görünür. Diğer `ButtonText` metin alanları boşsa öğe de varsayılan olur. Diğer `ButtonText` metin alanları belirtilse bile öğe boş olamaz.

## <a name="syntax"></a>Sözdizimi

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
|[Dizeleri Öğe](../extensibility/strings-element.md)|Metin öğelerini grupla, örneğin. `ButtonText` `CommandName`|

## <a name="text-value"></a>Metin değeri
 Öğenin `ButtonText` metin değeri, görünür metin ekiolan menü öğeleri, kombinasyonlar ve diğer kullanıcı arabirimi (UI) öğeleri için görüntülenen metni sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
