---
title: Bir Dil Hizmetinde AnaHat Desteği Sağlayın | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707963"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Nasıl?
Dillerinizin anahat desteğini **Genişletme'yi Tanımlara Daralt** komutunu desteklemenin ötesinde genişletmek için iki seçenek vardır. Düzenleyici denetimine göre anahat bölgeleri ekleyebilir ve istemci denetiminde anahat bölgeleri ekleyebilirsiniz.

## <a name="adding-editor-controlled-outline-regions"></a>Düzenleyici kontrollü anahat bölgeleri ekleme
 Anahat bölgesi oluşturmak için bu yaklaşımı kullanın ve ardından düzenleyicinin bölgenin genişletilip genişletilip genişletilip genişletilmediğini, daraltılıp sürülmediğini vb. işlemesine izin verin. Anahat desteği sağlamak için iki seçenek, bu seçenek en az sağlam. Bu seçenek için, metin belirli bir yayılma alanı üzerinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>yeni bir anahat bölge kullanarak oluşturun. Bu bölge oluşturulduktan sonra, davranışı editör tarafından denetlenir. Düzenleyici denetimli anahat bölgelerini uygulamak için aşağıdaki yordamı kullanın.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Düzenleyici kontrollü anahat bölgesini uygulamak için

1. Çağrı `QueryService` için<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Bu bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>döndürür.

2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>bir metin arabelleği için işaretçiyi çağırın. Bu arabellek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> nesneye bir işaretçi döndürür.

3. Bir <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> işaretçi için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>çağrı.

4. Aynı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> anda bir veya daha fazla yeni anahat bölgesi eklemek için arayın.

     Bu yöntem, anahat bölgelerinin kaldırılıp kaldırılmadığını veya korunup korunmadığını ve anahat bölgesinin varsayılan olarak genişletilip genişletilmediğini veya daraltılıp sürülmediğini anahatolarak anahatlandırmak için metnin açıkliğini belirtmenize olanak tanır.

## <a name="add-client-controlled-outline-regions"></a>İstemci denetimli anahat bölgeleri ekleme
 İstemci kontrollü (veya akıllı) anahat [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] dil hizmetleri tarafından kullanılan gibi anahat uygulamak için bu yaklaşımı kullanın. Kendi anahatlarını yöneten bir dil hizmeti, geçersiz olduklarında eski anahat bölgelerini yok etmek ve gerektiğinde yeni anahat bölgeleri oluşturmak için metin arabelleği içeriğini izler.

### <a name="to-implement-a-client-controlled-outline-region"></a>İstemci tarafından denetlenmeyen anahat bölgesini uygulamak için

1. Çağrı `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>için . Bu bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>döndürür.

2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>bir metin arabelleği için işaretçiyi çağırın. Bu, arabellek için gizli bir metin oturumunun zaten var olup olmadığını belirler.

3. Bir metin oturumu zaten varsa, bir tane oluşturmanız gerekmez ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> varolan nesneye işaretçi döndürülür. Anahat bölgelerini sayısallandırmak ve oluşturmak için bu işaretçiyi kullanın. Aksi takdirde, arabellek için gizli bir metin oturumu oluşturmak için arayın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Nesneye <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> bir işaretçi döndürülür.

    > [!NOTE]
    > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>Aradiğinizde, gizli bir metin istemcisi (yani <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> bir nesne) belirtebilirsiniz. Bu istemci, gizli bir metin veya anahat bölgesi kullanıcı tarafından genişletildiğinde veya daraltıldığında sizi size iletir.

4. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> yapısı) parametresi: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> Gizli `iType` bir bölge <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> yerine bir anahat bölgesi oluşturduğunuzu belirtmek için yapının üyesinin değerini belirtin. Yapının üyesinde bölgenin istemci tarafından mı `dwBehavior` yoksa düzenleyici denetiminde mi olduğunu belirtin. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Akıllı anahat uygulamanız, düzenleyici ve istemci denetimialtındaki anahat bölgelerinin bir karışımını içerebilir. Anahat bölgeniz daraltıldığında görüntülenen "...", yapının `pszBanner` üyesinde görüntülenen banner metnini belirtin. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Editörün gizli bir bölge için varsayılan banner metni "...".
