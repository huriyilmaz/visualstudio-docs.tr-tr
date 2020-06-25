---
title: Betik belgelerini görüntüleme | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcd9823e414005a1711ddccf9d972da929090920
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348450"
---
# <a name="how-to-view-script-documents-javascript"></a>Nasıl yapılır: betik belgelerini görüntüleme (JavaScript)

Sunucu tarafı betik dosyaları Çözüm Gezgini görünür. İstemci tarafı betik dosyaları yalnızca hata ayıklama modundayken veya kesme modundayken görülebilir. İstemci tarafı betik dosyaları, **betik belgeleri** düğümünde görünür.

Dinamik olarak sayfa üreten bazı uygulama türleri için, tarayıcıya yüklenen bir betik belgesinden bir kesme noktası ayarladığınızda kesme modu ve hata ayıklama girmek daha kolay olur. Benzer şekilde, `debugger` kesme moduna girmek için yüklenmiş bir betik belgesinden ifadesini de ekleyebilirsiniz. Bu makalede, bu belgelerin nasıl görüntüleneceği gösterilmektedir.

> [!NOTE]
> [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]Sunucu tarafı betiğinden oluşturulan istemci tarafı betik dosyaları, komut dosyası Gezgini penceresinde göründü.

### <a name="to-view-a-server-side-script-document"></a>Sunucu tarafı betik belgesini görüntülemek için

1. **Çözüm Gezgini**, **\<Website Pathname>** düğümünü açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     Sunucu tarafı betik dosyası bir kaynak penceresinde açılır.

### <a name="to-view-a-client-side-script-document"></a>İstemci tarafı betik belgesini görüntülemek için

1. **Çözüm Gezgini**, **komut dosyası belgeleri** düğümünü açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     İstemci tarafı betik dosyası bir kaynak penceresinde açılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)