---
title: Genel Bakış (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738600"
---
# <a name="overview-debug-interface-access-sdk"></a>Genel Bakış (Arabirim Erişimi SDK'sında Hata Ayıklama)
Microsoft hata ayıklama bilgilerine erişmek için DIA SDK kullanın. DIA SDK, Microsoft hata ayıklama bilgilerinin biçimini her değiştirdiğinde kodunuzu yeniden yazma gereksinimini ortadan kaldıran COM tabanlı bir API kümesi sağlar. DIA SDK Ayrıca, 5,0 ve üzeri sürümleri [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tarafından oluşturulan. pdb ve. dbg dosyalarında bulunan önceki hata ayıklama bilgileri kümesinden bir seçim kümesinden okumanızı de sağlar.

 DIA SDK her arabirim, aksi belirtilmedikçe farklı bir COM nesnesini temsil eder. Ek arabirimler ve bu nedenle ek nesneler, var olan arabirim işaretçilerinde `QueryInterface` çağırmak yerine [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) veya [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)gibi açık sorgular aracılığıyla oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)