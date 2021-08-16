---
title: Betik Belgelerini | Microsoft Docs
description: JavaScript sunucu tarafı betik belgelerini uygulama ve Visual Studio görüntülemeyi Çözüm Gezgini.
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: db8d6ab713b745e63c2ab419fbb6d134a2e0284b521e9633cdda45185e1e3505
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378664"
---
# <a name="how-to-view-script-documents-javascript"></a>Nasıl kullanılır: Betik Belgelerini Görüntüleme (JavaScript)

Sunucu tarafı betik dosyaları, dosyalarda Çözüm Gezgini. İstemci tarafı betik dosyaları yalnızca hata ayıklama modunda veya kesme modundayken görünür. İstemci tarafı betik dosyaları Betik Belgeleri **düğümünde** görünür.

Sayfaları dinamik olarak oluşturan bazı uygulama türleri için, tarayıcıda yüklenen bir betik belgesinde kesme noktası ayarsanız kesme moduna girmek ve hata ayıklamak daha kolaydır. Benzer şekilde, kesme moduna girmek `debugger` için yüklenen bir betik belgesinde deyimini ekleyebilirsiniz. Bu makalede, bu belgelerin nasıl görüntülen bir görünümü olduğu gösterir.

> [!NOTE]
> daha [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] önce, sunucu tarafı betikten oluşturulan istemci tarafı betik dosyaları Betik Gezgini penceresinde görüntülandı.

### <a name="to-view-a-server-side-script-document"></a>Sunucu tarafı betik belgesini görüntülemek için

1. Bu **Çözüm Gezgini** düğümü **\<Website Pathname>** açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     Sunucu tarafı betik dosyası bir kaynak pencerede açılır.

### <a name="to-view-a-client-side-script-document"></a>İstemci tarafı betik belgesini görüntülemek için

1. Bu **Çözüm Gezgini** Betik Belgeleri **düğümünü** açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     İstemci tarafı betik dosyası bir kaynak pencerede açılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)