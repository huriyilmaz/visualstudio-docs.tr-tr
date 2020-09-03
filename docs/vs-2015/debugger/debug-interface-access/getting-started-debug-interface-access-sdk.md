---
title: Başlarken (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164166"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Başlarken (Arabirim Erişimi SDK'sında Hata Ayıklama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama arabirimi erişimi (DIA) SDK 'Sı size, size bir öğretici belgesi ve bir DIA API 'sinin nasıl kullanılacağını gösteren bir örnek sağlar. . Pdb ve. dbg dosyalarını açan ve içeriklerini semboller, değerler, öznitelikler, adresler ve diğer hata ayıklama bilgileri için aramak üzere DIA SDK arabirimlerini ve yöntemlerini kullanın. Bu SDK, C++ uygulamalarında bulunan simgelerle ilişkili özellikler için de başvuru tabloları sağlar.  
  
 DIA SDK en iyi şekilde kullanmak için aşağıdakiler hakkında bilgi sahibi olmanız gerekir:  
  
- C++ programlama dili  
  
- COM programlama  
  
- Örnekleri derlemek için Visual Studio tümleşik geliştirme ortamı (IDE)  
  
  DIA SDK normalde Visual Studio ile yüklenir ve varsayılan konumu *[sürücü]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK ' dir. Yüklemenin bir parçası olarak, DIA SDK uygulayan msdia90.dll otomatik olarak kaydedilir, böylece kullanmak için yapmanız gereken tek şey, programınıza dahil etmek `dia2.h` ve ' a bağlantı kullanmaktır `diaguids.lib` .  
  
  Üstbilgi: include\dia2,h  
  
  Kitaplık: lib\diaguids.exe  
  
  DLL: bin\msdia80.dll  
  
  IDL: ıdl\dia2.IDL  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 DIA 'in temel mimarisini inceler.  
  
 [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Bir. pdb dosyasını sorgulamak için ÇYA API 'sini kullanma hakkında adım adım yönergeler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
