---
title: GörünürlükÖğe Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698156"
---
# <a name="visibilityitem-element"></a>GörünürlükÖğe öğesi
Öğe `VisibilityItem` komutların ve araç çubuklarının statik görünürlüğünü belirler. Her giriş bir komut veya menü ve aynı zamanda ilişkili bir komut UI bağlamı tanımlar. Visual Studio, komutları, menüleri ve araç çubuklarını tanımlayan VSPackages'ı yüklemeden algılar. IDE, komut <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> ui bağlamınının etkin olup olmadığını belirlemek için yöntemi kullanır.

 VSPackage yüklendikten sonra, Visual Studio komut görünürlüğünün VSPackage tarafından `VisibilityItem`değil, VSPackage tarafından belirlenmesini bekliyor. Komutunuzun görünürlüğünü belirlemek için, komutunuzu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> nasıl uyguladığınıza <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> bağlı olarak olay işleyicisini veya yöntemi uygulayabilirsiniz.

 Öğesi olan bir `VisibilityItem` komut veya menü yalnızca ilişkili bağlam etkin olduğunda görüntülenir. Tek bir komut, menü veya araç çubuğunu, her komut bağlamı birleşimi için bir giriş ekleyerek bir veya daha fazla komut UI bağlamıyla ilişkilendirebilirsiniz. Bir komut veya menü birden çok komut UI bağlamıyla ilişkiliyse, ilişkili komut ui bağlamlarından herhangi biri etkin olduğunda komut veya menü görünür.

 Öğe `VisibilityItem` yalnızca komutlar, menüler ve araç çubukları için geçerlidir, gruplar için değil. Üst menüsü etkin olduğunda `VisibilityItem` ilgili öğesi olmayan bir öğe görünür.

## <a name="syntax"></a>Sözdizimi

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.|
|id|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|bağlam|Gereklidir. Komutun görünür olduğu UI bağlamı.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri
 None

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GörünürlükKısıtlamalar öğesi](../extensibility/visibilityconstraints-element.md)|Öğe `VisibilityConstraints` komut ve araç çubukları gruplarının statik görünürlüğünü belirler.|

## <a name="remarks"></a>Açıklamalar
 Standart Visual Studio UI bağlamları *Visual Studio SDK yükleme yolu*\VisualStudioIntegration\Common\Inc\vsshlids.h <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> dosyasının yanı sıra ve <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> sınıflarda tanımlanır. <xref:Microsoft.VisualStudio.VSConstants> Sınıfta daha eksiksiz bir UI bağlamkümesi tanımlanır.

## <a name="example"></a>Örnek

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [GörünürlükKısıtlamalar öğesi](../extensibility/visibilityconstraints-element.md)
- [Visual Studio komut tablosu (. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
