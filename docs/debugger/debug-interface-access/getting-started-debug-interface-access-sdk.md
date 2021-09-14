---
description: Hata ayıklama arabirimi erişimi (DIA) SDK 'Sı size, size bir öğretici belgesi ve bir DIA API 'sinin nasıl kullanılacağını gösteren bir örnek sağlar.
title: Başlarken (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4e74262594e23af3819851bcf23d69692fd7d64c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630567"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Başlarken (Arabirim Erişimi SDK'sında Hata Ayıklama)
Hata ayıklama arabirimi erişimi (DIA) SDK 'Sı size, size bir öğretici belgesi ve bir DIA API 'sinin nasıl kullanılacağını gösteren bir örnek sağlar. . Pdb ve. dbg dosyalarını açan ve içeriklerini semboller, değerler, öznitelikler, adresler ve diğer hata ayıklama bilgileri için aramak üzere DIA SDK arabirimlerini ve yöntemlerini kullanın. Bu SDK, C++ uygulamalarında bulunan simgelerle ilişkili özellikler için de başvuru tabloları sağlar.

 DIA SDK en iyi şekilde kullanmak için aşağıdakiler hakkında bilgi sahibi olmanız gerekir:

- C++ programlama dili

- COM programlama

- örnekleri derlemek için tümleşik geliştirme ortamı (ıde) Visual Studio

  DIA SDK normalde Visual Studio ile yüklenir ve varsayılan konumu *[sürücü]* \program Files \ Microsoft Visual Studio 9.0 \ DIA SDK olur. Yüklemenin bir parçası olarak, DIA SDK uygulayan msdia90.dll otomatik olarak kaydedilir, böylece kullanmak için yapmanız gereken tek şey, programınıza dahil etmek `dia2.h` ve ' a bağlantı kullanmaktır `diaguids.lib` .

  Üstbilgi: include\dia2,h

  Kitaplık: lib\diaguids.exe

  DLL: bin\msdia80.dll

  IDL: ıdl\dia2.IDL

## <a name="in-this-section"></a>Bu Bölümde

[Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

DIA 'in temel mimarisini inceler.

[.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Bir. pdb dosyasını sorgulamak için ÇYA API 'sini kullanma hakkında adım adım yönergeler sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
