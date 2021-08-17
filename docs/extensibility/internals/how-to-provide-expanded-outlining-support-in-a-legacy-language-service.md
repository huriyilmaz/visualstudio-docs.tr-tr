---
title: Dil Hizmeti HizmetLerinde Açıklama Desteği | Microsoft Docs
description: Düzenleyici denetimli ana hat bölgeleri ve istemci denetimli ana hat bölgeleri ekleyerek eski dil hizmetlerinde genişletilmiş ana hat desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f3360c51e1cc2e7bc7d9e2841fc2e6f0b1a98077
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042401"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Nasıl olur: Eski dil hizmetlerinde genişletilmiş açıklama desteği sağlama
Diliniz için altı çizili desteği genişletmek için Tanımlara Daralt komutunu **desteklemenin** ötesinde iki seçenek vardır. Düzenleyici denetimli ana hat bölgeleri ekleyebilir ve istemci denetimli ana hat bölgeleri abilirsiniz.

## <a name="adding-editor-controlled-outline-regions"></a>Düzenleyici denetimli ana hat bölgeleri ekleme
 Bir ana hat bölgesi oluşturmak için bu yaklaşımı kullanın ve ardından düzenleyicinin bölgenin genişletilir, daraltılmış vb. olup olmadığını işlemesine izin verme. Bu seçenek, altı çizili destek sağlamak için 2 seçenek arasında en az sağlam seçenektir. Bu seçenek için, kullanarak belirtilen metin aralığı üzerinde yeni bir ana hat bölgesi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> oluşturun. Bu bölge oluşturulduktan sonra davranışı düzenleyici tarafından denetlenmektedir. Düzenleyici denetimli ana hat bölgelerini uygulamak için aşağıdaki yordamı kullanın.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Düzenleyici denetimli ana hat bölgesi uygulamak için

1. için `QueryService` çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Bu, için bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> döndürür.

2. Çağrısı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> belirli bir metin arabelleği için bir işaretçi geçirme. Bu, arabelleğin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> nesnesine bir işaretçi döndürür.

3. işaretçisi <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> için çağrısı. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>

4. Aynı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> anda bir veya daha fazla yeni ana hat bölgesi eklemek için çağrısı.

     Bu yöntem, ana hatların genişletilecek metin sürelerini, mevcut ana hat bölgelerinin kaldırılmış veya korunmuş olup olmadığını ve ana hat bölgenin varsayılan olarak genişlet mi yoksa daraltılmış mı olduğunu belirtmenize olanak sağlar.

## <a name="add-client-controlled-outline-regions"></a>İstemci denetimli ana hat bölgeleri ekleme
 ve dil hizmetleri tarafından kullanılana benzer istemci denetimli (veya akıllı) bir açıklama uygulamak için [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] bu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] yaklaşımı kullanın. Kendi ana hatlarını yöneten bir dil hizmeti, geçersiz hale gelen eski ana hat bölgelerini yok etmek ve gerektiğinde yeni ana hat bölgeleri oluşturmak için metin arabelleği içeriğini izler.

### <a name="to-implement-a-client-controlled-outline-region"></a>İstemci denetimli ana hat bölgesi uygulamak için

1. için `QueryService` çağrısında <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> bulundu. Bu, için bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> döndürür.

2. Çağrısı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> belirli bir metin arabelleği için bir işaretçi geçirme. Bu, arabellek için gizli bir metin oturumunun zaten mevcut olup olmadığını belirler.

3. Bir metin oturumu zaten varsa, bir tane oluşturmanıza gerek yoktur ve mevcut nesnenin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> işaretçisi döndürülür. Ana hat bölgelerini numaralarak ve oluşturmak için bu işaretçiyi kullanın. Aksi takdirde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> arabelleğe gizli bir metin oturumu oluşturmak için çağrısı yazın. Nesnenin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> işaretçisi döndürülür.

    > [!NOTE]
    > çağrısında <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> gizli bir metin istemcisi (yani bir nesne) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> belirtebilirsiniz. Gizli bir metin veya ana hat bölgesi kullanıcı tarafından genişletilir veya daraltılmışsa bu istemci size bilgi verir.

4. Çağrı yapısı) parametresi: Gizli bölge yerine ana hat bölgesi oluşturmakta olduğunu belirtmek için yapının <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> üyesinde değerini belirtin. Bölgenin yapının üyesinde istemci denetimli mi yoksa düzenleyici denetimli `dwBehavior` mi olduğunu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> belirtin. Akıllı ana hat uygulamanız, düzenleyici ve istemci denetimli ana hat bölgelerinin bir karışımını içerebilir. Ana hat bölgeniz daraltılmış durumdayken görüntülenen başlık metnini (yapının üyesinde "..." `pszBanner` gibi) <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> belirtin. Düzenleyicinin gizli bölge için varsayılan başlık metni "..." şeklindedir.
