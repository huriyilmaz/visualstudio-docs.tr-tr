---
title: GörünürlükKısıtlamalar Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698186"
---
# <a name="visibilityconstraints-element"></a>GörünürlükKısıtlamalar öğesi
Görünürlük Kısıtlamaları öğesi komut gruplarının ve araç çubuklarının statik görünürlüğünü belirler. Görüş mesafesi ilk olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage yüklemeden entegre geliştirme ortamı (IDE) tarafından kontrol edilir.

## <a name="syntax"></a>Sözdizimi

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
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[GörünürlükÖğe öğesi](../extensibility/visibilityitem-element.md)|Komutların ve araç çubuklarının statik görünürlüğünü belirler.|
|[GörünürlükKısıtlamalar](../extensibility/visibilityconstraints-element.md)|Komut gruplarının ve araç çubuklarının statik görünürlüğünü belirler.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın IDE'ye sağladığı komutları (örneğin, menü öğeleri, menüler, araç çubukları ve açılan kutular) temsil eden tüm öğeleri tanımlar.|

## <a name="example"></a>Örnek

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.
- [GörünürlükÖğe öğesi](../extensibility/visibilityitem-element.md)
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
