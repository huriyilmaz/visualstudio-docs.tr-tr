---
title: Eleme ~ SAK Files | Microsoft Docs
description: Kaynak denetimi eklentisi API 1,2 ' den ~ SAK dosyalarının eleme ve bunların nasıl değiştirildiğini yetenek bayrakları ve yeni işlevlerle nasıl değiştirdikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf0f8bc567a097d4bb7d400f829489c517e9a68f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061244"
---
# <a name="elimination-of-sak-files"></a>~ SAK dosyaları için eleme
Kaynak denetimi eklentisi API 1,2 ' de, *~ sak* dosyaları yetenek bayraklarıyla ve kaynak denetimi eklentisinin *Mssccprj* dosyasını ve paylaşılan kullanıma alma işlemleri destekleyip desteklemediğini algılayan yeni işlevlerle değiştirilmiştir.

## <a name="sak-files"></a>~ SAK dosyaları
Visual Studio .NET 2003 ön eki olan geçici dosyalar oluşturuldu *~ sak*. Bu dosyalar, bir kaynak denetimi eklentisinin destekleyip desteklemediğini tespit etmek için kullanılır:

- *Mssccprj. SCC* dosyası.

- Çoklu (paylaşılan) kullanıma alma işlemleri.

Kaynak denetimi eklentisi API 1,2 ' de sunulan gelişmiş işlevleri destekleyen eklentiler için, IDE, aşağıdaki bölümlerde ayrıntılı olarak açıklanan yeni özellikleri, bayrakları ve işlevleri kullanarak geçici dosyaları oluşturmadan bu özellikleri algılayabilir.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Yeni işlevler
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Bir kaynak denetimi eklentisi çoklu (paylaşılan) kullanıma alma işlemleri destekliyorsa, `SCC_CAP_MULTICHECKOUT` özelliği bildirir ve `SccIsMultiCheckOutEnabled` işlevi uygular. Bu işlev, kaynak denetimli projelerin herhangi birinde bir kullanıma alma işlemi gerçekleştiğinde çağrılır.

 Bir kaynak denetimi eklentisi bir *Mssccprj. SCC* dosyasının oluşturulmasını ve kullanımını destekliyorsa, `SCC_CAP_SCCFILE` özelliği bildirir ve [sccwillcreatesccdosyasını](../../extensibility/sccwillcreatesccfile-function.md)uygular. Bu işlev, bir dosya listesi ile çağırılır. İşlevi, `TRUE' or 'FALSE` Visual Studio 'nun kendisi için bir *Mssccprj. SCC* dosyası kullanması gerekip gerekmediğini belirtmek için her bir dosya için döndürür. Kaynak denetimi eklentisi bu yeni özellikleri ve işlevleri desteklememe seçerse, bu dosyaların oluşturulmasını devre dışı bırakmak için aşağıdaki kayıt defteri anahtarını kullanabilir:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Bu kayıt defteri anahtarı *DWORD: 00000000* olarak ayarlandıysa, varolmayan anahtarla eşdeğerdir ve Visual Studio yine de geçici dosyaları oluşturmaya çalışır. Ancak, kayıt defteri anahtarı *DWORD: 00000001* olarak ayarlandıysa, Visual Studio geçici dosyaları oluşturmayı denemez. Bunun yerine, kaynak denetimi eklentisinin *Mssccprj. SCC* dosyasını desteklemediğini varsayar ve paylaşılan kullanıma alma işlemleri desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API sürümü 1,2 ' deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
