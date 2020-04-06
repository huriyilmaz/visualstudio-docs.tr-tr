---
title: Eski dil hizmetinde gizli metin desteği sağlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707924"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Nasıl yapilir: Eski bir dil hizmetinde gizli metin desteği sağlayın
Anahat bölgelerine ek olarak gizli metin bölgeleri oluşturabilirsiniz. Gizli metin bölgeleri istemci veya düzenleyici denetiminde olabilir ve metin bölgesini tamamen gizlemek için kullanılır. Düzenleyici, gizli bir bölgeyi yatay çizgiler olarak görüntüler. Bunun bir örneği, HTML düzenleyicisindeki **Yalnızca Komut Dosyası** görünümüdür.

## <a name="to-implement-a-hidden-text-region"></a>Gizli metin bölgesi uygulamak için

1. Çağrı `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>için .

     Bu bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>döndürür.

2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>bir metin arabelleği için işaretçiyi çağırın. Bu, arabellek için gizli bir metin oturumunun zaten var olup olmadığını belirler.

3. Biri zaten varsa, o zaman bir oluşturmanız gerekmez ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> varolan nesneye bir işaretçi döndürülür. Gizli metin bölgelerini sayısallandırmak ve oluşturmak için bu işaretçiyi kullanın. Aksi takdirde, arabellek için gizli bir metin oturumu oluşturmak için arayın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>

     Nesneye <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> bir işaretçi döndürülür.

    > [!NOTE]
    > `CreateHiddenTextSession`Aradiğinizde, gizli bir metin istemcisi belirtebilirsiniz (yani. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Gizli metin istemcisi, gizli metin veya anahat kullanıcı tarafından genişletildiğinde veya daraltıldığında sizi size iletir.

4. Bir seferde bir veya daha fazla yeni anahat bölgesi eklemek için<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>çağrı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> ( ) parametreaşağıdaki bilgileri belirterek: `reHidReg`

    1. Anahat bölgesi `hrtConcealed` yerine `iType` gizli <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> bir bölge oluşturduğunuzu belirtmek için yapının üyesinin değerini belirtin.

        > [!NOTE]
        > Gizli bölgeler gizlendiğinde, düzenleyici varlıklarını göstermek için gizli bölgelerin etrafındaki satırları otomatik olarak görüntüler.

    2. Yapının üyeleri için bölgenin istemci tarafından mı `dwBehavior` yoksa düzenleyici denetiminde mi olduğunu belirtin. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Akıllı anahat uygulamanız, düzenleyici ve istemci kontrollü anahat ve gizli metin bölgelerinin bir karışımını içerebilir.
