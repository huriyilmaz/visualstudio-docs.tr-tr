---
title: ~SAK Dosyalarının Ortadan Kaldırılması | Microsoft Docs
description: Kaynak Denetimi Eklentisi API 1.2'den ~SAK dosyalarının ortadan kaldırılması ve bunların yetenek bayrakları ve yeni işlevlerle nasıl değiştirildiklerini öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c4fb89b2bb6ab3e895e77257bce83f1308ea73b7ca72209453e2d32f3440c344
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359500"
---
# <a name="elimination-of-sak-files"></a>~SAK dosyalarının ortadan kaldırılması
Kaynak Denetimi Eklentisi API 1.2'de~ *SAK* dosyaları, bir kaynak denetimi eklentisinin *MSSCCPRJ* dosyasını ve paylaşılan onayları destekleyip destekleme olmadığını algılayan özellik bayrakları ve yeni işlevlerle değiştirilmiştir.

## <a name="sak-files"></a>~SAK dosyaları
Visual Studio .NET 2003 tarafından *~SAK* ön ekli geçici dosyalar oluşturuldu. Bu dosyalar, bir kaynak denetimi eklentisinin şunları destekleyip destekleme olmadığını belirlemek için kullanılır:

- *MSSCCPRJ.SCC* dosyası.

- Birden çok (paylaşılan) onay.

Kaynak Denetimi Eklentisi API 1.2'de sağlanan gelişmiş işlevleri destekleyen eklentiler için IDE, aşağıdaki bölümlerde ayrıntılı olarak verilen yeni özellikleri, bayrakları ve işlevleri kullanarak geçici dosyaları oluşturmadan bu özellikleri algılanabilir.

## <a name="new-capability-flags"></a>Yeni özellik bayrakları
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Yeni işlevler
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Bir kaynak denetimi eklentisi birden çok (paylaşılan) onayları destekliyorsa, özelliği `SCC_CAP_MULTICHECKOUT` bildirer ve işlevi `SccIsMultiCheckOutEnabled` uygulamaz. Bu işlev, kaynak denetimli projelerden herhangi biri üzerinde bir ödeme işlemi oluştuğunda çağrılır.

 Kaynak denetimi eklentisi *MSSCCPRJ.SCC* dosyasının oluşturulmasını ve kullanımını destekliyorsa, özelliği bildirer ve `SCC_CAP_SCCFILE` [SccWillCreateSccFile'ı kullanır.](../../extensibility/sccwillcreatesccfile-function.md) Bu işlev bir dosya listesiyle çağrılır. İşlev, her `TRUE' or 'FALSE` dosya için bir *MSSCCPRJ.SCC* Visual Studio olup olmadığını belirtmek üzere döndürür. Kaynak denetimi eklentisi bu yeni özellikleri ve işlevleri desteklemezse, bu dosyaların oluşturulmasını devre dışı bırakmak için aşağıdaki kayıt defteri anahtarını kullanabilir:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl**  =  *dword:00000001*

> [!NOTE]
> Bu kayıt defteri anahtarı *dword:00000000* olarak ayarlanırsa, anahtarın var olup Visual Studio geçici dosyaları oluşturma girişiminde de bulunmaktadır. Ancak, kayıt defteri anahtarı *dword:00000001* olarak Visual Studio geçici dosyaları oluşturma girişiminde bulunamıyor. Bunun yerine, kaynak denetimi eklentisinin *MSSCCPRJ.SCC* dosyasını desteklemez ve paylaşılan onayları desteklemez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API'si Sürüm 1.2'de neler var?](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
