---
title: Commands öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184300"
---
# <a name="commands-element"></a>Commands Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage araç çubuğundaki komutların koleksiyonunu temsil eder. Koleksiyonda en fazla beş alt dizi olabilir: menüler, gruplar, düğmeler, comboler ve bit eşlemler.  
  
 Her alt bölüm alt öğesi, örneğin,, \<Menu> BIR GUID ve sayısal tanımlayıcı çifti olan benzersiz bir komut kimliğiyle tanımlanır. GUID, "komut kümesini" tanımlar ve mantıksal olarak ilişkili komutları gruplandırmak için kullanılır. VSPackage, diğer VSPackages tarafından tanımlanan komut kimlikleriyle çakışmaları önlemek için kendi komut kümesini tanımlamalıdır.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|leyebilir|Komutları sağlayan VSPackage 'ı tanımlayan bir GUID.<br /><br /> Örneğin, Package = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Menus Öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|  
|[Groups Öğesi](../extensibility/groups-element.md)|Bir VSPackage içindeki komut gruplarını tanımlayan girişleri içerir.|  
|[Buttons Öğesi](../extensibility/buttons-element.md)|Düğme öğelerini gruplandırır.|  
|[Bitmaps Öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğelerini gruplandırır.|  
|[Combos Öğesi](../extensibility/combos-element.md)|Grupları açılan öğeleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları temsil eden tüm öğeleri tanımlar. Olası öğeler menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutularıdır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir [Commands öğesinin](../extensibility/commands-element.md)nasıl kullanılacağını gösterir.  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
