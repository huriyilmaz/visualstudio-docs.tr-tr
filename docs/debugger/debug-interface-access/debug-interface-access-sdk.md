---
description: Microsoft hata ayıklama arabirimi erişimi yazılım geliştirme seti (DIA SDK), Microsoft postcompiler araçları tarafından oluşturulan program veritabanı (. pdb) dosyaları içinde depolanan hata ayıklama bilgilerine erişim sağlar.
title: Hata ayıklama arabirimi erişim SDK 'Sı | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbb7c9025094249715f1d69a8d58d8725d294107
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149307"
---
# <a name="debug-interface-access-sdk"></a>Arabirim Erişimi SDK'sında Hata Ayıklama

Microsoft hata ayıklama arabirimi erişimi yazılım geliştirme seti (DIA SDK), Microsoft postcompiler araçları tarafından oluşturulan program veritabanı (. pdb) dosyaları içinde depolanan hata ayıklama bilgilerine erişim sağlar. Postcompiler araçları tarafından oluşturulan. pdb dosyasının biçimi sabit düzeltme ile devam ettiğinden, biçimi açığa çıkarmak pratik değildir. DIA API 'sini kullanarak bir. pdb dosyasında depolanan hata ayıklama bilgilerini aramak ve bunları taramak için uygulamalar geliştirebilirsiniz. Örneğin, bu gibi uygulamalar, rapor yığını izleme geri bilgilerini ve performans verilerini analiz edebilir.

## <a name="in-this-section"></a>Bu bölümde

[Başlarken](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

DIA SDK özelliklerine genel bir bakış sağlar ve gereken başlık ve kitaplık dosyalarının yanı sıra DIA SDK nereye yükleneceğini belirtir.

[.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

. Pdb dosyasını sorgulamak için ÇYA API 'sinin nasıl kullanılacağına ilişkin yönergeler sağlar.

[Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Sembol ve sembol etiketlerinin ÇYA API 'de nasıl kullanıldığını açıklar.

[Başvuru](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

DIA API 'sinin arabirimlerini, yöntemlerini, Numaralandırmaların ve yapılarını içerir.

[Dia2dump Örneği](../../debugger/debug-interface-access/dia2dump-sample.md)

Hata ayıklama bilgilerini aramak ve taramak için, DIA API 'sinin nasıl kullanılacağını gösterir.
