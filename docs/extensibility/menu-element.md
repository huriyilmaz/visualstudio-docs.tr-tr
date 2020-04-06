---
title: Menü Elemanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702592"
---
# <a name="menu-element"></a>Menü öğesi
Bir menü öğesini tanımlar. Bunlar altı tür menü: Bağlam, Menü, MenuController, MenuControllerLatched, Araç Çubuğu ve ToolWindowToolbar.

## <a name="syntax"></a>Sözdizimi

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
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.|
|id|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|Öncelik|İsteğe bağlı. Bir menü grubunda bir menünün göreli konumunu belirten sayısal bir değer.|
|Araç ÇubuğuÖncelikli Bant|İsteğe bağlı. Pencere kenetlendiğinde bir banttaki araç çubuğunun göreli konumunu belirten sayısal bir değer.|
|type|İsteğe bağlı. Öğetürünü belirten numaralandırılmış bir değer.<br /><br /> Yoksa, varsayılan tür Menü'dür.<br /><br /> Bağlam<br /> Bir kullanıcı pencereyi sağ tıklattığında gösterilen kısayol menüsü. Kısayol menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Menü kısayol menüsü olarak görüntülenecekken **Veli** ve **Öncelik** alanlarını kullanmaz.<br />- Alt menü ve kısayol menüsü olarak da kullanılabilir. Bu durumda, hem **Grup Kimliği** hem de **Öncelik** alanlarına saygı duyulur.<br />- Her zaman mevcut değildir.<br /><br /> Kısayol menüsü yalnızca aşağıdaki koşullar doğru olduğunda görüntülenir:<br /><br /> - Ana bilgisayar penceresi görüntülenir.<br />- VSPackage'daki bir fare işleyicisi pencereye sağ tıklama algılar ve ardından komutu işleyen bir yöntem çağırır.<br />- Kısayol <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> menüsü, yöntem (önerilen yaklaşım) veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> yöntem çağırılarak görüntülenir.<br /><br /> Menü<br /> Açılır menü sağlar. Açılır menü aşağıdaki özelliklere sahiptir:<br /><br /> - Tanımında Veliye Saygı Duyar.<br />- Bir Üst grup veya bir gruba bir Komut Yerleştirme olmalıdır.<br />- Menü başka bir tür bir alt menü olabilir.<br />- Üst menüsü görüntülendiğinde otomatik olarak görüntülenir.<br />- Görüntülenmesi için herhangi bir VSPackage kodunun uygulanmasını gerektirmez.<br /><br /> MenüDenetleyici<br /> Genellikle araç çubuklarında kullanılan bölünmüş düğme açılır menü sağlar. MenuController menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Veli veya CommandPlacement aracılığıyla başka bir menüde yer almalıdır.<br />- Tanımında Veliye Saygı Duyar.<br />- Ebeveyni olarak her türlü menüye sahip olabilir.<br />- Üst menüsü görüntülendiğinde otomatik olarak kullanılabilir hale getirilir.<br />- Menüyü görüntülemek için programlı destek gerektirmez.<br /><br /> Menü düğmesinde bölme düğmesinden bir komut görüntülenir. Görüntülenen komut aşağıdaki özelliklerden birine sahiptir:<br /><br /> - Komut hala görüntüleniyor ve etkinse kullanılan son komutdur.<br />- Görüntülenen ilk komutdur.<br /><br /> MenüDenetleyiciLatched<br /> Komutu mandallı olarak işaretleyerek varsayılan seçim olarak bir komutun belirtilebileceği bölünmüş düğme açılır menü sağlar.<br /><br /> Mandallı komut, genellikle bir onay işareti görüntüleyerek menüde seçili olarak işaretlenmiş bir komutdur. Bir komut, `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimin yönteminin uygulanmasında üzerinde OLECMDF_LATCHED bayrağı ayarlanmışsa mandallı olarak işaretlenebilir. MenuControllerLatched menüsü aşağıdaki özelliklere sahiptir:<br /><br /> - Bir Veli grubu veya CommandPlacement aracılığıyla başka bir menüde yer almalıdır.<br />- Tanımında Veliye Saygı Duyar.<br />- Ebeveyni olarak her türlü menüye sahip olabilir.<br />- Üst menüsü görüntülendiğinde kullanılabilir hale getirilir.<br />- Menüyü görüntülemek için programlı destek gerektirmez.<br /><br /> Menü düğmesinde bölme düğmesinden bir komut görüntülenir. Görüntülenen komut aşağıdaki özelliklerden birine sahiptir:<br /><br /> - Bu mandallı ilk görüntülenen komutudur.<br />- Görüntülenen ilk komutdur.<br /><br /> Araç Çubuğu<br /> Araç çubuğu sağlar. Araç çubuğu aşağıdaki özelliklere sahiptir:<br /><br /> - Üst öğeyi tanımında yok sayar.<br />- CommandPlacement kullanılarak bile hiçbir grubun alt menüsü yapılamaz.<br />- **Görünüm** menüsündeki **Araç Çubukları'na** tıklayarak her zaman görüntülenebilir.<br />- [Görünürlük Öğesi](../extensibility/visibilityitem-element.md)kullanılarak görüntülenebilir.<br />- Oluşturmak için herhangi bir kod gerektirmez. Araç çubuğu oluşturma hakkında bir örnek [için](../extensibility/adding-a-toolbar.md)bkz.<br /><br /> ToolWindowToolToolbar<br /> Geliştirme ortamına bir araç çubuğu bağlı olduğu gibi, belirli bir araç penceresine bağlı bir araç çubuğu sağlar.<br /><br /> - Üst öğeyi tanımında yok sayar.<br />- CommandPlacement kullanılarak bile hiçbir grubun alt menüsü yapılamaz.<br />- Yalnızca araç çubuğunu barındıran araç penceresi görüntülendiğinde ve VSPackage araç çubuğunu araç penceresine açıkça eklediğinde görüntülenir. Bu genellikle araç penceresi araç penceresi özelliği <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> (arabirim tarafından temsil edildiği gibi) elde edilerek ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> yöntem çağırarak araç penceresi oluşturulduğunda yapılır.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Menü öğesinin üst öğesi.|
|Komut Bayrağı|Gereklidir. Bkz. [Komut bayrak öğesi.](../extensibility/command-flag-element.md) Menü için geçerli CommandFlag değerleri aşağıdaki gibidir:<br /><br /> -   **Her Zaman Oluştur**<br />-   **Varsayılan Docked**<br />-   **DefaultInvisible** - Bu bayrak araç çubuklarının görüntülenmesini etkilemez.<br />-   **DontÖnbellek**<br />-   **DynamicGörünürlik** - Bu bayrak araç çubuklarının ekranını etkilemez.<br />-   **Simgeve Metin**<br />-   **NoCustomizE**<br />-   **Notintblist**<br />-   **NoToolbarClose**<br />-   **Metin Değişiklikleri**<br />-   **TextisAnchorCommand**|
|Dizeler|Gereklidir. Bkz. [Dizeleri öğesi.](../extensibility/strings-element.md) Alt `ButtonText` öğe tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı yorum.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uyguladığı tüm menüleri tanımlar.|

## <a name="example"></a>Örnek

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
