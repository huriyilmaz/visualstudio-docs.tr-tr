---
title: Menü öğesi | Microsoft Docs
description: Menü öğesi bir menü öğesi tanımlar. Menü türleri bağlam, menü, MenuController, Menucontrollerlalenmiş, Toolbar ve ToolWindowToolbar.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f20e05c50bf208490edd237299653a3caa6b559f
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616084"
---
# <a name="menu-element"></a>Menü öğesi
Bir menü öğesini tanımlar. Bunlar arasında altı menü türü bulunur: bağlam, menü, MenuController, Menucontrollerlalenmiş, Toolbar ve ToolWindowToolbar.

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
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|
|Priority|İsteğe bağlı. Bir menü grubundaki bir menünün göreli konumunu belirten sayısal bir değer.|
|Toolbarpriorityınband|İsteğe bağlı. Pencere yerleştirildiğinde bir bantta bir araç çubuğunun göreli konumunu belirten sayısal bir değer.|
|tür|İsteğe bağlı. Öğe türünü belirten numaralandırılmış bir değer.<br /><br /> Yoksa, varsayılan tür menü olur.<br /><br /> Bağlam<br /> Bir Kullanıcı bir pencereye sağ tıkladığında gösterilen kısayol menüsü. Bir kısayol menüsü aşağıdaki özelliklere sahiptir:<br /><br /> -Menü, kısayol menüsü olarak görüntülenmek için **üst** ve **Öncelik** alanlarını kullanmaz.<br />-Bir alt menü ve ayrıca bir kısayol menüsü olarak kullanılabilir. Bu durumda, hem **Grup Kimliği** hem de **Öncelik** alanları dikkate alınır.<br />-Her zaman kullanılabilir değildir.<br /><br /> Kısayol menüsü yalnızca aşağıdaki koşullar doğru olduğunda görüntülenir:<br /><br /> -Onu barındıran pencere görüntülenir.<br />-VSPackage içindeki bir fare işleyicisi, pencerenin sağ tıklamasını algılar ve ardından komutu işleyen bir yöntemi çağırır.<br />-Kısayol menüsü <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Yöntemi (önerilen yaklaşım) veya yöntemi çağırarak görüntülenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> .<br /><br /> Menü<br /> Bir açılır menü sağlar. Açılan menü aşağıdaki özelliklere sahiptir:<br /><br /> -Üst öğeyi tanımında uyar.<br />-Bir üst gruba veya bir gruba bir Commandyerleştirmesini içermelidir.<br />-Diğer bir menü türü içinde bir alt menü olabilir.<br />-, Ana menüsü her görüntülendiğinde otomatik olarak görüntülenir.<br />-Görüntülenmesini sağlamak için herhangi bir VSPackage kodu uygulamasının uygulanmasını gerektirmez.<br /><br /> MenuController<br /> Genellikle araç çubuklarında kullanılan bir bölünmüş düğme açılan menüsü sağlar. Bir MenuController menüsü aşağıdaki özelliklere sahiptir:<br /><br /> -Üst veya Commandyerleştirmesi aracılığıyla başka bir menüde bulunmalıdır.<br />-Üst öğeyi tanımında uyar.<br />-Üst öğesi olarak herhangi bir menü türü olabilir.<br />-Otomatik olarak, üst menü görüntülenişinde kullanılabilir hale getirilir.<br />-Menüyü görüntülenmesini sağlamak için programlı destek gerektirmez.<br /><br /> Menü düğmesinde bölünmüş düğme menüsünden bir komut görüntülenir. Görünen komut aşağıdaki özelliklerden birine sahiptir:<br /><br /> -Komut hala görüntüleniyorsa ve etkinse kullanılan son komuttur.<br />-İlk görüntülenmiş komuttur.<br /><br /> Menucontrollerlalenmiş<br /> Komutun varsayılan seçim olarak işaretlenmesi için bir komutun varsayılan seçim olarak belirtibileceği bir bölünmüş düğme açılır menü sağlar.<br /><br /> Bir lalelenmiş komut, genellikle bir onay işareti görüntüleyerek, menüde seçili olarak işaretlenen bir komuttur. Bir komut, arabirim yönteminin bir uygulamasında üzerinde ayarlanmış OLECMDF_LATCHED bayrağını içeriyorsa, bir komut, lalenmiş olarak işaretlenebilir `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Bir Menucontrollerlalenmiş menü aşağıdaki özelliklere sahiptir:<br /><br /> -Bir üst grup veya Commandyerleştirmesi aracılığıyla başka bir menüde bulunmalıdır.<br />-Üst öğeyi tanımında uyar.<br />-Üst öğesi olarak herhangi bir menü türü olabilir.<br />-Her üst menü görüntülendiğinde kullanılabilir hale getirilir.<br />-Menüyü görüntülenmesini sağlamak için programlı destek gerektirmez.<br /><br /> Menü düğmesinde bölünmüş düğme menüsünden bir komut görüntülenir. Görünen komut aşağıdaki özelliklerden birine sahiptir:<br /><br /> -Bu, açılan ilk görüntülenen komuttur.<br />-İlk görüntülenmiş komuttur.<br /><br /> Araç Çubuğu<br /> Bir araç çubuğu sağlar. Bir araç çubuğu aşağıdaki özelliklere sahiptir:<br /><br /> -Tanımındaki üst öğeyi yoksayar.<br />-Commandyerleştirmesi kullanılarak bile değil, herhangi bir grubun alt menüsü yapılamaz.<br />- **Görünüm** menüsünde **araç çubukları** öğesine tıklanarak her zaman görüntülenebilir.<br />-Bir [VisibilityItem](../extensibility/visibilityitem-element.md)kullanılarak görüntülenebilir.<br />-Oluşturmak için herhangi bir kod gerekmez. Bir araç çubuğu oluşturma hakkında bir örnek için bkz. [araç çubuğu ekleme](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Yalnızca bir araç çubuğunun geliştirme ortamına eklendiği gibi, belirli bir araç penceresine eklenmiş bir araç çubuğu sağlar.<br /><br /> -Tanımındaki üst öğeyi yoksayar.<br />-Commandyerleştirmesi kullanılarak bile değil, herhangi bir grubun alt menüsü yapılamaz.<br />-Yalnızca araç çubuğunu barındıran araç penceresi görüntülenirken ve VSPackage araç çubuğunu araç penceresine açıkça eklediğinde görüntülenir. Bu genellikle araç penceresi araç penceresi <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> çerçevesisinden ve sonra yöntemini çağırarak araç çubuğu ana bilgisayar özelliği (arabirim tarafından temsil edildiğinde) ile oluşturulduğunda yapılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> .|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Menü öğesinin üst öğesi.|
|CommandFlag|Gereklidir. Bkz. [komut bayrağı öğesi](../extensibility/command-flag-element.md). Bir menü için geçerli CommandFlag değerleri aşağıdaki gibidir:<br /><br /> -   **AlwaysCreate**<br />-   **Defaultsabitlenmiş**<br />-   **Defaulınvisible** -bu bayrak, araç çubuklarının görüntülenmesini etkilemez.<br />-   **DontCache**<br />-   **DynamicVisibility** -bu bayrak araç çubuklarının görüntülenmesini etkilemez.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Dizeler|Gereklidir. Bkz. [dizeler öğesi](../extensibility/strings-element.md). Alt `ButtonText` öğe tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı açıklama.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|

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
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
