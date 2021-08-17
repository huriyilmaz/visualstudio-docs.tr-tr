---
title: Extern öğe | Microsoft Docs
description: Extern öğesi, derleme zamanında. vsct dosyası ile birleştirmek için herhangi bir dış üstbilgi (. h) dosyasına başvurur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 22f10cb94421d891f62bc5e57769e740e25dc05089c7dd442a145ebd1077b060
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401797"
---
# <a name="extern-element"></a>Extern öğesi
Extern öğesi, derleme zamanında *. vsct* dosyası ile birleştirmek için herhangi bir dış üstbilgi (*. h*) dosyasına başvurur. Birleştirilecek dosyalar, VSCT derleyicisine verilen veya bir [Include öğesi](../extensibility/include-element.md)tarafından başvurulan içerme yolunda olmalıdır. Dosyalar, diğer *. vsct* dosyaları veya C++ üst bilgi dosyaları olabilir.

 Üstbilgi dosyalarındaki tanımlar "#define [symbol] [Value]" biçiminde olmalıdır, daha önceden tanımlanmışsa değer başka bir sembol olabilir. Tanımlar, komut öğelerinin koşullu deyimlerinde kullanılabilir. Gerçekte kullanılmayan herhangi bir sembol atılır.

 CommandTable öğesi extern öğesi

## <a name="syntax"></a>Syntax

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|değerini|Gereklidir. Üst bilgi dosyasının yolu:<br /><br /> href = "Stdidcmd. h"|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|İsteğe bağlı. [\<Strings>](../extensibility/strings-element.md)Komut tablosundaki tüm öğelerin varsayılan dili:<br /><br /> Language = "en-US"|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.|Yok.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları (menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları) temsil eden tüm öğeleri tanımlar.|

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
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
