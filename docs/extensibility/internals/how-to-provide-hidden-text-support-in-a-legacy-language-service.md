---
title: Eski dil hizmetinde gizli metin desteği sağlama
description: Düzenleyici denetimli veya istemci denetimli gizli metin bölgeleri ekleyerek eski dil hizmetinde gizli metin desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2bb6d9c3c4f01c0e84c6ab437e352a86bf00448f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078740"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Nasıl yapılır: eski dil hizmetinde gizli metin desteği sağlama
Ana hat bölgelerine ek olarak gizli metin alanları da oluşturabilirsiniz. Gizli metin bölgeleri, istemci denetimli veya düzenleyiciden denetlenebilir ve bir metin bölgesini tamamen gizlemek için kullanılır. Düzenleyici, gizli bir bölgeyi yatay çizgiler olarak görüntüler. Bunun bir örneği, HTML düzenleyicisinde **yalnızca betik** görünümüdür.

## <a name="to-implement-a-hidden-text-region"></a>Gizli metin bölgesi uygulamak için

1. `QueryService`İçin çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Bu, için bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Belirli bir metin arabelleği için bir işaretçiye geçerek çağrı yapın. Bu, bir gizli metin oturumunun arabellekte zaten mevcut olup olmadığını belirler.

3. Zaten varsa, bir tane oluşturmanız gerekmez ve var olan nesneye bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür. Gizli metin bölgelerini numaralandırmak ve oluşturmak için bu işaretçiyi kullanın. Aksi takdirde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> arabellek için gizli metin oturumu oluşturma çağrısı yapın.

     Nesneye yönelik bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür.

    > [!NOTE]
    > `CreateHiddenTextSession`Öğesini çağırdığınızda gizli bir metin istemcisi (yani, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ) belirtebilirsiniz. Gizli metin istemcisi, gizli metin veya anahat oluşturma kullanıcı tarafından genişletildiğinde veya daraltıldığında size bildirir.

4. Tek seferde bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> veya daha fazla yeni ana hat bölgesi eklemek için çağırın ve `reHidReg` () parametresinde aşağıdaki bilgileri belirtin <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> :

    1. Bir `hrtConcealed` `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ana hat bölgesi yerine gizli bölge oluşturduğunuz belirten yapının üyesinde bir değer belirtin.

        > [!NOTE]
        > Gizli olmayan bölgeler gizliyse, düzenleyici, otomatik olarak gizli bölgelerin çevresindeki satırları gösterir.

    2. Bölgenin, yapının üyelerinde istemci denetimli veya düzenleyiciyle kontrol edilip edilmeyeceğini belirtin `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Akıllı anahat oluşturma uygulamanız, düzenleyici ve istemci denetimli ana hat ve gizli metin bölgelerinin bir karışımını içerebilir.
