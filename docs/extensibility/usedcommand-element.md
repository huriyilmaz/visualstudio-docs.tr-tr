---
title: UsedCommand Elemanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698834"
---
# <a name="usedcommand-element"></a>UsedCommand Öğesi
VSPackage'ın başka bir .vsct dosyasında tanımlanan bir komuta erişmesini sağlar. Örneğin, VSPackage'ınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kabuk tarafından tanımlanan standart **Kopyala** komutunu kullanıyorsa, komutu yeniden uygulamadan bir menüye veya araç çubuğuna ekleyebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. Komutu tanımlayan GUID ID çiftinin GUID'i.|
|id|Gereklidir. Komutu tanımlayan GUID kimlik çiftinin kimliği.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu Öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|Grupları UsedCommand elemanları ve diğer UsedCommands gruplandırmaları.|

## <a name="remarks"></a>Açıklamalar
 `<UsedCommands>` Elemana bir komut ekleyerek, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage, VSPackage'ın komutu gerektirdiği ortamı bildirir. Paketinizin gerektirdiği `<UsedCommand>` ve Visual Studio'nun tüm sürümlerine ve yapılandırmalarına dahil edilemeyecek herhangi bir komut için bir öğe eklemeniz gerekir. Örneğin, paketiniz Visual C++'a özgü bir komut çağırırsa, komut için bir `<UsedCommand>` öğe eklemediğiniz sürece komut Visual Web Developer kullanıcıları tarafından kullanılamaz.

## <a name="example"></a>Örnek

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Ayrıca bkz.
- [UsedCommands Öğesi](../extensibility/usedcommands-element.md)
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
