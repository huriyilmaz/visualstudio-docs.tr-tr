---
title: Düğme öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58f63968ed02f49b0ccfa4dda24f684fed339bc4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184548"
---
# <a name="button-element"></a>Button Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcının etkileşime girebileceği bir öğe tanımlar. Düğmeler farklı türlerde olabilir: Button, Menubtan ve SplitDropDown.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|  
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|  
|Priority|İsteğe bağlı. Önceliği belirten sayısal bir değer.|  
|tür|İsteğe bağlı. Düğme türünü belirten numaralandırılmış bir değer.<br /><br /> Verilmezse, düğme kullanır.<br /><br /> Düğme<br /> Araç çubuklarında (genellikle absolut düğmesi olarak), menülerde ve bağlam menülerinde görüntülenen standart bir komut.<br /><br /> MenuButton<br /> Bir komut yürütülemez ancak başka bir menü üreten bir menü öğesi.<br /><br /> Bölünmüş aşağı açılan<br /> Microsoft Word 'deki Standart araç çubuğunda yer alan geri al ve Yinele düğmeleri gibi denetimler.|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Üst Öğe](../extensibility/parent-element.md)|İsteğe bağlı. Düğmenin üst öğesi.|  
|[Icon Öğesi](../extensibility/icon-element.md)|İsteğe bağlı. Düğme ile ilişkili simge.|  
|[Command Flag Öğesi](../extensibility/command-flag-element.md)|Gereklidir. Bir düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> - DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -PICT<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -Textbasamakdeusebtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Dizeler öğesi](../extensibility/strings-element.md)|Gereklidir. Alt [ButtonText öğesi](../extensibility/buttontext-element.md) tanımlanmalıdır.|  
|Ek Açıklama|İsteğe bağlı açıklama.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Buttons Öğesi](../extensibility/buttons-element.md)|Düğme öğelerini gruplandırır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir. vsct dosyasındaki bir düğmeyi tanımlar.  
   
 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
