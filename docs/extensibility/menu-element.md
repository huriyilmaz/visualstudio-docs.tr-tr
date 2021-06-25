---
title: Menü Öğesi | Microsoft Docs
description: Menü öğesi bir menü öğesi tanımlar. Menü türleri Bağlam, Menü, MenuController, MenuControllerLatched, Araç Çubuğu ve ToolWindowToolbar'dır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2ffa029dd05e7fe3d32a9df4a1d06c90c8b9c6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901545"
---
# <a name="menu-element"></a>Menü öğesi
Bir menü öğesini tanımlar. Menülerin altı türü vardır: Bağlam, Menü, MenuController, MenuControllerLatched, Araç Çubuğu ve ToolWindowToolbar.

## <a name="syntax"></a>Syntax

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|Öncelik|İsteğe bağlı. Bir menü grubunda bir menenin göreli konumunu belirten sayısal bir değer.|
|ToolbarPriorityInBand|İsteğe bağlı. Pencere yerleştiriken bir bantta araç çubuğunun göreli konumunu belirten sayısal bir değer.|
|tür|İsteğe bağlı. Öğenin tür belirten bir numaralandı değer.<br /><br /> Yoksa varsayılan tür Menü'yü kullanır.<br /><br /> Bağlam<br /> Kullanıcı pencereye sağ tıkladığında gösterilen kısayol menüsü. Kısayol menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Menü bir **kısayol menüsü** olarak **görüntülendiğinde** Üst ve Öncelik alanlarını kullanmaz.<br />- Alt menü olarak ve kısayol menüsü olarak kullanılabilir. Bu durumda, hem **Grup Kimliği hem** de **Öncelik** alanları kabul edildi.<br />- Her zaman kullanılabilir değildir.<br /><br /> Kısayol menüsü yalnızca aşağıdaki koşullar doğru olduğunda görüntülenir:<br /><br /> - Bunu barındıran pencere görüntülenir.<br />- VSPackage'daki bir fare işleyicisi pencereye sağ tıklamayı algılar ve ardından komutun işleyicisini çağıran bir yöntem kullanır.<br />- Kısayol menüsü yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> (önerilen yaklaşım) veya yöntemi çağrılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> görüntülenir.<br /><br /> Menü<br /> Açılan menüyü sağlar. Açılan menü aşağıdaki özelliklere sahiptir:<br /><br /> - Tanımında Üst öğeye saygı sağlar.<br />- Bir grup için Bir Üst grubu veya CommandPlacement olması gerekir.<br />- Diğer menü türlerden herhangi bir alt menü olabilir.<br />- Üst menüsü her görüntülendiğinde otomatik olarak görüntülenir.<br />- Herhangi bir VSPackage kodunun görüntülenebilir hale uygulanmasını gerektirmez.<br /><br /> MenuController<br /> Genellikle araç çubuklarında kullanılan bölünmüş düğme açılan menüsü sağlar. MenuController menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Parent veya CommandPlacement aracılığıyla başka bir menüde yer alan bir menü olması gerekir.<br />- Tanımında Üst öğeye saygı sağlar.<br />- Üst öğesi olarak herhangi bir tür menüye sahip olabilir.<br />- Üst menüsü her görüntülendiğinde otomatik olarak kullanılabilir.<br />- Menüyü görüntüley etmek için program aracılığıyla destek gerektirmez.<br /><br /> Bölünmüş düğme menüsünden bir komut menü düğmesinde görüntülenir. Görüntülenen komut aşağıdaki özelliklerden birini içerir:<br /><br /> - Komut hala görüntüleniyorsa ve etkinse kullanılan son komuttur.<br />- İlk görüntülenen komuttur.<br /><br /> MenuControllerLatched<br /> Komutun kilitli olarak işaretlenmesiyle varsayılan seçim olarak belirtilebilir, bölünmüş düğme açılan menüsü sağlar.<br /><br /> Mandallı komut, genellikle bir onay işareti görüntüleyerek menüde seçili olarak işaretlenen bir komut. Bir komut, arabiriminin yönteminin bir uygulamasında OLECMDF_LATCHED bayrağı ayarlanmışsa, bu komut `QueryStatus` kilitli olarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işaretlenir. MenuControllerLatched menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Bir Üst grup veya CommandPlacement aracılığıyla başka bir menüde yer alan gerekir.<br />- Tanımında Üst öğeye saygı sağlar.<br />- Üst öğesi olarak herhangi bir tür menüye sahip olabilir.<br />- Üst menüsü her görüntülendiğinde kullanılabilir yapılır.<br />- Menüyü görüntüley etmek için program aracılığıyla destek gerektirmez.<br /><br /> Bölünmüş düğme menüsünden bir komut menü düğmesinde görüntülenir. Görüntülenen komut aşağıdaki özelliklerden birini içerir:<br /><br /> - Bu, kilitli ilk görüntülenen komuttur.<br />- İlk görüntülenen komuttur.<br /><br /> Araç Çubuğu<br /> Bir araç çubuğu sağlar. Araç çubuğu aşağıdaki özelliklere sahiptir:<br /><br /> - Tanımında Üst öğeyi yoksayır.<br />- CommandPlacement kullanılarak bile hiçbir grubun alt menüsü olamaz.<br />- Görünüm menüsündeki Araç **Çubukları'ya tıklayarak** her zaman **görüntülenebilir.**<br />- [VisibilityItem kullanılarak görüntülenebilir.](../extensibility/visibilityitem-element.md)<br />- Oluşturmak için herhangi bir kod gerektirmez. Araç çubuğu oluşturma hakkında bir örnek için bkz. [Araç çubuğu ekleme.](../extensibility/adding-a-toolbar.md)<br /><br /> ToolWindowToolbar<br /> Geliştirme ortamına bir araç çubuğu ekli olduğu gibi, belirli bir araç penceresine eklenmiş bir araç çubuğu sağlar.<br /><br /> - Tanımında Üst öğeyi yoksayır.<br />- CommandPlacement kullanılarak bile hiçbir grubun alt menüsü olamaz.<br />- Yalnızca araç çubuğunu barındıran araç penceresi görüntülendiğinde görüntülenir ve VSPackage araç çubuğunu araç penceresine açıkça ekler. Bu genellikle araç penceresi oluşturulduğunda araç çubuğu ana bilgisayar özelliği (arabirim tarafından temsil edilir) araç penceresi çerçevesinden alınarak ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> yöntemi çağrılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> yapılır.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Menü öğesinin üst öğesi.|
|CommandFlag|Gereklidir. Bkz. [Komut bayrağı öğesi.](../extensibility/command-flag-element.md) Bir Menü için geçerli CommandFlag değerleri aşağıdaki gibidir:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** - Bu bayrak, araç çubuklarının görüntülenmesini etkilemez.<br />-   **DontCache**<br />-   **DynamicVisibility** - Bu bayrak, araç çubuklarının display'ini etkilemez.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Dizeler|Gereklidir. Bkz. [Dizeler öğesi.](../extensibility/strings-element.md) Alt `ButtonText` öğe tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı açıklama.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri tanımlar.|

## <a name="example"></a>Örnek

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
