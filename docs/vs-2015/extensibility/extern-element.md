---
title: Extern öğe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204402"
---
# <a name="extern-element"></a>Extern Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extern öğesi, derleme zamanında. vsct dosyası ile birleştirmek için herhangi bir dış üstbilgi (. h) dosyasına başvurur. Birleştirilecek dosyalar, VSCT derleyicisine verilen veya bir [Include öğesi](../extensibility/include-element.md)tarafından başvurulan içerme yolunda olmalıdır. Dosyalar, diğer. vsct dosyaları veya C++ üst bilgi dosyaları olabilir.  
  
 Üstbilgi dosyalarındaki tanımlar "#define [symbol] [Value]" biçiminde olmalıdır, daha önceden tanımlanmışsa değer başka bir sembol olabilir. Tanımlar, komut öğelerinin koşullu deyimlerinde kullanılabilir. Gerçekte kullanılmayan herhangi bir sembol atılır.  
  
 CommandTable Öğesi  
Extern Öğesi  
  
## <a name="syntax"></a>Syntax  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|değerini|Gereklidir. Üst bilgi dosyasının yolu:<br /><br /> href = "Stdidcmd. h"|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|İsteğe bağlı. [\<Strings>](../extensibility/strings-element.md)Komut tablosundaki tüm öğelerin varsayılan dili:<br /><br /> Language = "en-US"|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Yok.|Yok.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları (menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları) temsil eden tüm öğeleri tanımlar.|  
  
## <a name="example"></a>Örnek  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
