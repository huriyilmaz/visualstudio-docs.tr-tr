---
title: VisibilityItem Öğesi | Microsoft Docs
description: VisibilityItem öğesi, komutların ve araç çubuklarının statik görünürlüğünü belirler. Girişler bir komutu veya menüyü ve ilişkili bir komut kullanıcı arabirimi bağlamını tanımlıyor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 95a3cdaddd10cefabaa166e045f5b2f4b1a8d517
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078640"
---
# <a name="visibilityitem-element"></a>VisibilityItem öğesi
`VisibilityItem`öğesi, komutların ve araç çubuklarının statik görünürlüğünü belirler. Her giriş bir komutu veya menüyü ve ayrıca ilişkili bir komut kullanıcı arabirimi bağlamını tanımlar. Visual Studio, komutları, menüleri ve araç çubuklarını ve bunların görünürlüğünü tanımlayan VSPackage'ları yüklemeden algılar. IDE, bir komut <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> kullanıcı arabirimi bağlamının etkin olup olmadığını belirlemek için yöntemini kullanır.

 VSPackage yüklendikten sonra Visual Studio, komut görünürlüğünün yerine VSPackage tarafından belirlenecek şekilde olmasını `VisibilityItem` bekler. Komutun görünürlüğünü belirlemek için, komutlarınızı nasıl uygulaymış olduğunu bağlı olarak olay <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> işleyicisini veya yöntemini kullanabilirsiniz.

 Öğesi olan bir komut veya `VisibilityItem` menü yalnızca ilişkili bağlam etkin olduğunda görünür. Tek bir komutu, menüyü veya araç çubuğunu bir veya daha fazla komut kullanıcı arabirimi bağlamıyla ilişkilendirmek için her komut bağlamı birleşimi için bir giriş ekleyebilirsiniz. Bir komut veya menü birden çok komut kullanıcı arabirimi bağlamıyla ilişkili ise, ilişkili komut kullanıcı arabirimi bağlamlarından herhangi biri etkin olduğunda komut veya menü görünür.

 öğesi `VisibilityItem` gruplara değil yalnızca komutlara, menülere ve araç çubuklarına uygulanır. üst menüsü etkin olduğunda ilgili `VisibilityItem` öğeye sahip bir öğe görünür.

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
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|bağlam|Gereklidir. Komutun görünür olduğu kullanıcı arabirimi bağlamı.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri
 Hiçbiri

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`öğesi, komut gruplarının ve araç çubuklarının statik görünürlüğünü belirler.|

## <a name="remarks"></a>Açıklamalar
 Standart Visual Studio KULLANıCı Arabirimi *bağlamları, Visual Studio SDK* yükleme yolu \VisualStudioIntegration\Common\Inc\vsshlids.h dosyasında ve <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> sınıflarında <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> tanımlanır. sınıfında daha eksiksiz bir kullanıcı arabirimi bağlam kümesi <xref:Microsoft.VisualStudio.VSConstants> tanımlanır.

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
- [VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md)
- [Visual Studio tablosu () seçin. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
