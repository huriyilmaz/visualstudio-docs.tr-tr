---
title: Başlarken (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745100"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Başlarken (Arabirim Erişimi SDK'sında Hata Ayıklama)
Hata ayıklama arabirimi erişimi (DIA) SDK 'Sı size, size bir öğretici belgesi ve bir DIA API 'sinin nasıl kullanılacağını gösteren bir örnek sağlar. . Pdb ve. dbg dosyalarını açan ve içeriklerini semboller, değerler, öznitelikler, adresler ve diğer hata ayıklama bilgileri için aramak üzere DIA SDK arabirimlerini ve yöntemlerini kullanın. Bu SDK, C++ uygulamalarda bulunan simgelerle ilişkili özellikler için de başvuru tabloları sağlar.

 DIA SDK en iyi şekilde kullanmak için aşağıdakiler hakkında bilgi sahibi olmanız gerekir:

- C++programlama dili

- COM programlama

- Örnekleri derlemek için Visual Studio tümleşik geliştirme ortamı (IDE)

  DIA SDK normalde Visual Studio ile yüklenir ve varsayılan konumu *[sürücü]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK ' dir. Yüklemenin bir parçası olarak, DIA SDK uygulayan msdia90. dll dosyası otomatik olarak kaydedilir, böylece bunu kullanmak için yapmanız gerekir. bu sayede, programınıza `dia2.h` ve `diaguids.lib`bağlantı kurma.

  Üstbilgi: include\dia2,h

  Kitaplık: lib\diaguids.exe

  DLL: bin\msdia80.dll

  IDL: ıdl\dia2.IDL

## <a name="in-this-section"></a>Bu Bölümde

[Genel bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

DIA 'in temel mimarisini inceler.

[.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Bir. pdb dosyasını sorgulamak için ÇYA API 'sini kullanma hakkında adım adım yönergeler sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)