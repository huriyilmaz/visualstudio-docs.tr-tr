---
title: UsedCommand öğesi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698834"
---
# <a name="usedcommand-element"></a>UsedCommand Öğesi
Bir VSPackage 'ın, başka bir. vsct dosyasında tanımlı bir komuta erişmesine olanak sağlar. Örneğin, VSPackage, kabuk tarafından tanımlanan standart **kopyalama** komutunu kullanıyorsa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , komutu yeniden uygulamadan bir menü veya araç çubuğuna ekleyebilirsiniz.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. Komutu tanımlayan GUID KIMLIK çiftinin GUID 'SI.|
|kimlik|Gereklidir. Komutu tanımlayan GUID KIMLIK çiftinin KIMLIĞI.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|Hiçbiri||

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|Gruplar, UsedCommand öğeleri ve diğer UsedCommands gruplandırmaları.|

## <a name="remarks"></a>Açıklamalar
 Öğeye bir komut eklenerek `<UsedCommands>` VSPackage, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage 'ın komutunu gerektirdiğini bildirir. `<UsedCommand>`Paketinizin her bir komut için, Visual Studio 'nun tüm sürümlerine ve yapılandırmalarına dahil edilmemelidir. Örneğin, paketiniz Visual C++ özgü bir komut çağırırsa, komut için bir öğe eklemediğiniz takdirde, komut Visual Web Developer kullanıcıları tarafından kullanılamaz `<UsedCommand>` .

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
