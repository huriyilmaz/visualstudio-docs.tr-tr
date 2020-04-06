---
title: Extern Element | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711496"
---
# <a name="extern-element"></a>Extern elemanı
Extern öğesi, derleme zamanında *.vsct* dosyasıyla birleştirmek için herhangi bir dış üstbilgi (*.h*) dosyasına başvurur. Birleştirilecek dosyalar VSCT derleyicisine verilen veya Bir [Ekle öğesi](../extensibility/include-element.md)tarafından başvurulan Ekle yolunda olmalıdır. Dosyalar diğer *.vsct* dosyaları veya C++ üstbilgi dosyaları olabilir.

 Üstbilgi dosyalarındaki tanımlar "#define [Sembol] [Değer]" biçiminde olmalıdır, değer daha önce tanımlanmışsa başka bir sembol olabilir. Tanımlar komut öğelerinin koşullu ifadelerinde kullanılabilir. Gerçekte kullanılmayan herhangi bir sembol atılır.

 CommandTable Elemanı Extern Elemanı

## <a name="syntax"></a>Sözdizimi

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Href|Gereklidir. Üstbilgi dosyasına giden yol:<br /><br /> href="stdidcmd.h"|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|
|language|İsteğe bağlı. Komut tablosundaki tüm [ \<String'lerin>](../extensibility/strings-element.md) öğelerinin varsayılan dili:<br /><br /> dil="en-us"|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.|Yok.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage'In IDE'ye sağladığı komutları (yani menü öğeleri, menüler, araç çubukları ve açılan kutular) temsil eden tüm öğeleri tanımlar.|

## <a name="example"></a>Örnek

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
