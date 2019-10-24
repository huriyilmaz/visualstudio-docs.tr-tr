---
title: UsedCommand öğesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718779"
---
# <a name="usedcommand-element"></a>UsedCommand Öğesi
Bir VSPackage 'ın, başka bir. vsct dosyasında tanımlı bir komuta erişmesine olanak sağlar. Örneğin, VSPackage, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kabuğu tarafından tanımlanan standart **Copy** komutunu kullanıyorsa, komutu yeniden uygulamadan bir menü veya araç çubuğuna ekleyebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|'ini|Gerekli. Komutu tanımlayan GUID KIMLIK çiftinin GUID 'SI.|
|kimlik|Gerekli. Komutu tanımlayan GUID KIMLIK çiftinin KIMLIĞI.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.||

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|Gruplar, UsedCommand öğeleri ve diğer UsedCommands gruplandırmaları.|

## <a name="remarks"></a>Açıklamalar
 @No__t_0 öğesine bir komut ekleyerek VSPackage, VSPackage 'ın komutunu gerektirdiğini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortamına bildirir. Paketinizin her bir komut için, Visual Studio 'nun tüm sürümlerine ve yapılandırmalarına dahil edilmeyebilir için bir `<UsedCommand>` öğesi eklemeniz gerekir. Örneğin, paketiniz görsele C++özgü bir komut çağırırsa, komut için bir `<UsedCommand>` öğesi eklemediğiniz takdirde, komut Visual Web Developer kullanıcıları tarafından kullanılamaz.

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