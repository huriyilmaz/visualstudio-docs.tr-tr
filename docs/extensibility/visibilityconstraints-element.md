---
title: Visibilitykýsýtlamaöğesi | Microsoft Docs
description: Visibilitykýsýtlamalarý öğesi, komut ve araç çubuklarının grup gruplarının statik görünürlüğünü belirler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0a24761a7f0c71f50be70b12de1203c0f22d2b8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049252"
---
# <a name="visibilityconstraints-element"></a>Visibilitykýsýtlamaöğesi
Visibilitykýsýtlamalarý öğesi, komut ve araç çubuklarının grup gruplarının statik görünürlüğünü belirler. Görünürlük öncelikle, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage yüklenmeden tümleşik geliştirme ortamı (IDE) tarafından denetlenir.

## <a name="syntax"></a>Syntax

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[VisibilityItem öğesi](../extensibility/visibilityitem-element.md)|Komutların ve araç çubuklarının statik görünürlüğünü belirler.|
|[Visibilitykýsýtlamalarý](../extensibility/visibilityconstraints-element.md)|Komut ve araç çubuğu gruplarının statik görünürlüğünü belirler.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları (örneğin, menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları) temsil eden tüm öğeleri tanımlar.|

## <a name="example"></a>Örnek

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VisibilityItem öğesi](../extensibility/visibilityitem-element.md)
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
