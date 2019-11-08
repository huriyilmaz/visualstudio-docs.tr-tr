---
title: 'Nasıl yapılır: betik belgelerini görüntüleme | Microsoft Docs'
ms.date: 11/05/2019
ms.topic: conceptual
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
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714433"
---
# <a name="how-to-view-script-documents-javascript"></a>Nasıl yapılır: betik belgelerini görüntüleme (JavaScript)

Sunucu tarafı betik dosyaları Çözüm Gezgini görünür. İstemci tarafı betik dosyaları yalnızca hata ayıklama modundayken veya kesme modundayken görülebilir. İstemci tarafı betik dosyaları, **betik belgeleri** düğümünde görünür.

Dinamik olarak sayfa üreten bazı uygulama türleri için, tarayıcıya yüklenen bir betik belgesinden bir kesme noktası ayarladığınızda kesme modu ve hata ayıklama girmek daha kolay olur. Benzer şekilde, bir komut dosyası belgesinden kesme moduna girmek için `debugger` ifadesini de ekleyebilirsiniz. Bu makalede, bu belgelerin nasıl görüntüleneceği gösterilmektedir.

> [!NOTE]
> [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]' den önceki, sunucu tarafı komut dosyasından oluşturulan istemci tarafı betik dosyaları komut dosyası Gezgini penceresinde göründü.

### <a name="to-view-a-server-side-script-document"></a>Sunucu tarafı betik belgesini görüntülemek için

1. **Çözüm Gezgini**' de, **\<Website PathName >** düğümünü açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     Sunucu tarafı betik dosyası bir kaynak penceresinde açılır.

### <a name="to-view-a-client-side-script-document"></a>İstemci tarafı betik belgesini görüntülemek için

1. **Çözüm Gezgini**, **komut dosyası belgeleri** düğümünü açın.

2. Görüntülemek istediğiniz betik dosyasına çift tıklayın.

     İstemci tarafı betik dosyası bir kaynak penceresinde açılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)