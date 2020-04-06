---
title: ~SAK Dosyalarının Ortadan Kaldırılması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708494"
---
# <a name="elimination-of-sak-files"></a>~SAK dosyalarının ortadan kaldırılması
Kaynak Denetimi Eklentisi API 1.2'de~ *SAK* dosyaları, kaynak denetim eklentisinin *MSSCCPRJ* dosyasını ve paylaşılan kullanıma sahip denetimleri destekleyip desteklemediğini algılayan yetenek bayrakları ve yeni işlevlerle değiştirildi.

## <a name="sak-files"></a>~SAK dosyaları
Visual Studio .NET 2003 ~ *SAK*ile önceden belirlenmiş geçici dosyalar oluşturdu. Bu dosyalar, kaynak denetimi eklentisi destekleyip desteklemedi belirlemek için kullanılır:

- *MSSCCPRJ.SCC* dosyası.

- Birden çok (paylaşılan) ödeme.

Kaynak Denetimi Eklentisi API 1.2'de sağlanan gelişmiş işlevleri destekleyen eklentiler için IDE, aşağıdaki bölümlerde ayrıntılı olarak belirtilen yeni özellikler, bayraklar ve işlevler kullanarak geçici dosyaları oluşturmadan bu özellikleri algılayabilir.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Yeni işlevler
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Kaynak denetim eklentisi birden çok (paylaşılan) ödemeyi destekliyorsa, `SCC_CAP_MULTICHECKOUT` bu `SccIsMultiCheckOutEnabled` özelliği bildirir ve işlevi uygular. Bu işlev, kaynak denetimli projelerden herhangi birinde bir ödeme işlemi oluştuğunda çağrılır.

 Bir kaynak denetim eklentisi bir *MSSCCPRJ.SCC* dosyasının oluşturulmasını ve `SCC_CAP_SCCFILE` kullanımını destekliyorsa, o zaman bu özelliği bildirir ve [SccWillCreateSccFile'ı](../../extensibility/sccwillcreatesccfile-function.md)uygular. Bu işlev, dosyaların bir listesi ile çağrılır. İşlev, `TRUE' or 'FALSE` Visual Studio'nun bunun için bir *MSSCCPRJ.SCC* dosyası kullanıp kullanmaması gerektiğini belirtmek için her dosya için döndürür. Kaynak denetimi eklentisi bu yeni yetenekleri ve işlevleri desteklememeyi seçerse, bu dosyaların oluşturulmasını devre dışı bırakmayı devre dışı kullanabilirsiniz:

 **[HKEY_CURRENT_USER\Yazılım\Microsoft\VisualStudio\8.0\Kaynak Denetimi] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Bu kayıt defteri anahtarı *dword:00000000*olarak ayarlanmışsa, anahtar var olmayan eşdeğerdir ve Visual Studio hala geçici dosyaları oluşturmaya çalışır. Ancak, kayıt defteri anahtarı *dword:00000001*olarak ayarlanmışsa, Visual Studio geçici dosyaları oluşturmaya çalışmaz. Bunun yerine, kaynak denetimi eklentisinin *MSSCCPRJ.SCC* dosyasını desteklemediğini ve paylaşılan ödemeleri desteklemediğini varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürüm 1.2'deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
