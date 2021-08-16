---
title: UsedCommand öğesi | Microsoft Docs
description: UsedCommand öğesi, VSPackage 'ın başka bir. vsct dosyasında tanımlanan bir komuta erişmesini sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 33d6d5626f8ff96e9c52a71c4edfbc17de65eb749b90aa646d4dd53cf4edb9ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358863"
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
 Öğeye bir komut eklenerek `<UsedCommands>` VSPackage, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage 'ın komutunu gerektirdiğini bildirir. `<UsedCommand>`Paketinizin her bir komut için, Visual Studio tüm sürümlerine ve yapılandırmalara dahil edilmemelidir. Örneğin, paketiniz Visual C++ özgü bir komut çağırırsa, komut için bir öğe eklemediğiniz takdirde, komut Visual Web Developer kullanıcıları tarafından kullanılamaz `<UsedCommand>` .

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
