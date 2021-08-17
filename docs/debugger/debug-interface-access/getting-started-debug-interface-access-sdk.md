---
description: Arabirim ErişimiNde Hata Ayıklama (DIA) SDK'sı size yönerge belgeleri ve DIA API'sini kullanmayı gösteren bir örnek sağlar.
title: Başlarken (Arabirim Erişimi SDK'sı Hata Ayıklama) | Microsoft Docs
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
ms.openlocfilehash: bc3ffc7dddab91a674dbdb09cb53556d17b86cca420f2ba02a7f9ac100bcac6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345367"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Başlarken (Arabirim Erişimi SDK'sında Hata Ayıklama)
Arabirim ErişimiNde Hata Ayıklama (DIA) SDK'sı size yönerge belgeleri ve DIA API'sini kullanmayı gösteren bir örnek sağlar. .pdb ve .dbg dosyalarını açıp içeriklerinde semboller, değerler, öznitelikler, adresler ve diğer hata ayıklama bilgileri için arama yapılan özel uygulamalar geliştirmek için DIA SDK'daki arabirimleri ve yöntemleri kullanın. Bu SDK, C++ uygulamalarında bulunan sembollerle ilişkili özellikler için başvuru tabloları da sağlar.

 En iyi DIA SDK için aşağıdakilere aşina olmak gerekir:

- C++ programlama dili

- COM programlama

- Visual Studio derlemek için tümleşik geliştirme ortamı (IDE)

  DIA SDK normalde Visual Studio ile yüklenir ve varsayılan konumu *[sürücü]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK. Yüklemenin bir parçası olarak, msdia90.dll'i uygulayan DIA SDK otomatik olarak kaydedilir, böylece bunu kullanmak için tek gereken programınıza dahil etmek ve bağlantısını `dia2.h` `diaguids.lib` yapmaktır.

  Üst bilgi: include\dia2.h

  Kitaplık: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>Bu Bölümde

[Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

DIA'nın temel mimarisini gözden okur.

[.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Bir .pdb dosyasını sorgulamak için DIA API'sini kullanma hakkında adım adım yönergeler sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
