---
title: UsedCommand Öğesi | Microsoft Docs
description: UsedCommand öğesi, vsPackage'ın başka bir .vsct dosyasında tanımlanan bir komuta erişmesi için olanak sağlar.
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
ms.openlocfilehash: 0333b3a83333eebdb25da83206b9da2a4c9082ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049291"
---
# <a name="usedcommand-element"></a>UsedCommand Öğesi
VsPackage'ın başka bir .vsct dosyasında tanımlanan bir komuta erişmesi için olanak sağlar. Örneğin, VSPackage'nız kabuk tarafından tanımlanan standart **Copy** komutunu kullanıyorsa, komutu yeniden uygulamadan bir menüye veya araç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çubuğuna ekleyebilirsiniz.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. Komutu tanımlayan GUID kimlik çiftinin GUID'si.|
|kimlik|Gereklidir. Komutu tanımlayan GUID kimliği çiftinin kimliği.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu Öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|Hiçbiri||

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|UsedCommand öğelerini ve diğer UsedCommands gruplamalarını gruplar.|

## <a name="remarks"></a>Açıklamalar
 öğesine bir komut ekleyerek `<UsedCommands>` VSPackage, ortama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage'ın komutunu gerektirdiğini bildirmektedir. Paketinizin gerektirdiği herhangi bir komut için, paketinizin tüm sürümlerine ve yapılandırmalara dahil edilecek `<UsedCommand>` bir öğe Visual Studio. Örneğin, paketiniz özel bir komut Visual C++, komutu için bir öğe dahil olmadığınız sürece komut Visual Web Developer kullanıcıları `<UsedCommand>` tarafından kullanılamaz.

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
