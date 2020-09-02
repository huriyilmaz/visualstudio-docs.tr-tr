---
title: KeyBinding öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180323"
---
# <a name="keybinding-element"></a>KeyBinding Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding öğesi komutların klavye kısayollarını belirler.  
  
 Komutlarda kendileriyle ilişkilendirilmiş tek ve çift anahtar bağlamaları bulunabilir. Tek tuşla bağlama bir örnek **Kaydet** komutu için CTRL + S ' dir. Çift anahtar bağlamaları bir komutun tetiklenmesi için iki ardışık anahtar kombinasyonu gerektirir. Çift anahtar bağlamasının bir örneği CTRL + K, CTRL + K, bir yer işareti ayarlamak için bir örnektir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir.|  
|kimlik|Gereklidir.|  
|düzenleyici|Gereklidir. Düzenleyici GUID 'SI, bu klavye kısayolunun etkin olacağı düzenleme bağlamını gösterir. Genel bağlama kapsamı değeri "guidVSStd97" değeridir.|  
|key1|Gereklidir. Geçerli değerler, tüm tyıılabilen alfasayısal değerleri ve bundan önce 0x ve VK_constants olan iki basamaklı onaltılık değerler içerir.|  
|mod1|İsteğe bağlı. Boşluğa göre ayrılan CTRL, ALT ve SHIFT 'in herhangi bir birleşimi.|  
|key2|İsteğe bağlı. Geçerli değerler, tüm tyıılabilen alfasayısal değerleri ve bundan önce 0x ve VK_constants olan iki basamaklı onaltılık değerler içerir.|  
|mod2|İsteğe bağlı. Boşluğa göre ayrılan CTRL, ALT ve SHIFT 'in herhangi bir birleşimi.|  
|öykünücü|İsteğe bağlı.|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst||  
|Ek Açıklama||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[KeyBindings Öğesi](../extensibility/keybindings-element.md)|Anahtar bağlama öğelerini ve diğer KeyBindings gruplandırmaları gruplandırır.|  
  
## <a name="example"></a>Örnek  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [KeyBindings öğesi](../extensibility/keybindings-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
