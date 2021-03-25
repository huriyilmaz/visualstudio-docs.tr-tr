---
title: VisibilityItem öğesi | Microsoft Docs
description: VisibilityItem öğesi, komutların ve araç çubuklarının statik görünürlüğünü belirler. Girdiler bir komutu veya menüyü ve ilişkili bir komut UI bağlamını belirler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1229c5e63838a8192c7622cdddd9881799a2da11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062518"
---
# <a name="visibilityitem-element"></a>VisibilityItem öğesi
`VisibilityItem`Öğesi, komutların ve araç çubuklarının statik görünürlüğünü belirler. Her giriş bir komutu veya menüyü ve ayrıca ilişkili bir komut UI bağlamını tanımlar. Visual Studio, bunları tanımlayan VSPackages 'ları yüklemeden komutları, menüleri ve araç çubuklarını ve bunların görünürlüğünü algılar. IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> bir komut UI bağlamının etkin olup olmadığını anlamak için yöntemini kullanır.

 VSPackage yüklendikten sonra Visual Studio, komut görünürlüğünü, yerine VSPackage tarafından belirlenecek şekilde bekler `VisibilityItem` . Komutınızın görünürlüğünü öğrenmek için, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> komutunuza nasıl uyguladığınıza bağlı olarak olay işleyicisini ya da yöntemini uygulayabilirsiniz.

 `VisibilityItem`Yalnızca ilişkili bağlam etkin olduğunda bir öğesi olan bir komut veya menü görünür. Her komut bağlamı kombinasyonu için bir giriş ekleyerek, tek bir komutu, menüyü veya araç çubuğunu bir veya daha fazla komut UI bağlamıyla ilişkilendirebilirsiniz. Bir komut veya menü birden çok komut UI bağlamlarına ilişkiliyse, ilişkili komut Kullanıcı arabirimi bağlamlarından herhangi biri etkin olduğunda komut veya menü görünür olur.

 `VisibilityItem`Öğe yalnızca komutlar, menüler ve araç çubukları için geçerlidir, gruplar için geçerli değildir. İlişkili bir öğesi olmayan bir öğe, `VisibilityItem` üst menüsü etkin olduğunda görünür olur.

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|
|bağlam|Gereklidir. Komutun görünür olduğu kullanıcı arabirimi bağlamı.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri
 Yok

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Visibilitykýsýtlamaöğesi](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`Öğesi, komut ve araç çubuklarının statik görünürlüğünü belirler.|

## <a name="remarks"></a>Açıklamalar
 Standart Visual Studio Kullanıcı arabirimi bağlamları, ve sınıflarının yanı sıra *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc\vsshlids.h dosyasında da tanımlanmıştır <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Sınıfında daha kapsamlı bir UI bağlamı kümesi tanımlanmıştır <xref:Microsoft.VisualStudio.VSConstants> .

## <a name="example"></a>Örnek

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Visibilitykýsýtlamaöğesi](../extensibility/visibilityconstraints-element.md)
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
