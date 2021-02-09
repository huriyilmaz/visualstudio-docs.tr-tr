---
title: Dil hizmetinde ana hat desteği sağlama | Microsoft Docs
description: Düzenleyici denetimli ana hat bölgelerini ve istemci denetimli ana hat bölgelerini ekleyerek eski dil hizmetinde genişletilmiş anahat oluşturma desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db7c4f886a071b4b759072a1b141690f4e4b097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890727"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Nasıl yapılır: eski dil hizmetinde genişletilmiş anahat desteği sağlama
**Tanımlarınız Için daraltma** desteğini genişletmek Için, tanımlara göre Daralt komutunu desteklemeye yönelik iki seçenek vardır. Düzenleyiciyle denetlenen ana hat bölgelerini ekleyebilir ve istemci denetimli ana hat bölgelerini ekleyebilirsiniz.

## <a name="adding-editor-controlled-outline-regions"></a>Düzenleyici denetimli ana hat bölgeleri ekleme
 Bu yaklaşımı kullanarak bir anahat bölgesi oluşturun ve ardından düzenleyicinin bölgenin genişletilip genişletilmeyeceğini, daraltılması ve benzer şekilde işleme devam edebilmesi için bu yaklaşımı kullanın. Ana hat desteği sağlamaya yönelik iki seçenekten en az güçlü seçenektir. Bu seçenek için, kullanarak belirli bir metin aralığı üzerinde yeni bir ana hat bölgesi oluşturacaksınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Bu bölge oluşturulduktan sonra, davranışı düzenleyici tarafından denetlenir. Düzenleyici denetimli ana hat bölgelerini uygulamak için aşağıdaki yordamı kullanın.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Düzenleyici denetimli bir ana hat bölgesi uygulamak için

1. Çağrı `QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Bu, için bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Belirli bir metin arabelleği için bir işaretçiye geçerek çağrı yapın. Bu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> arabellek için nesnesine bir işaretçi döndürür.

3. <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> İçin bir işaretçi çağrısı yapın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Tek seferde bir veya daha fazla yeni ana hat bölgesi eklemek için çağırın.

     Bu yöntem, ana hat için metin yayılımını, mevcut ana hat bölgelerinin kaldırılıp kaldırılmadığını veya korunacağını, ana hat bölgesinin varsayılan olarak genişletilip genişletilmeyeceğini veya daraltılacağını belirtmenize olanak tanır.

## <a name="add-client-controlled-outline-regions"></a>İstemci denetimli ana hat bölgelerini ekleme
 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Ve dil Hizmetleri tarafından kullanılan gibi istemci denetimli (veya akıllı) anahat uygulamak için bu yaklaşımı kullanın [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . Kendi anahat oluşturmayı yöneten bir dil hizmeti, eski ana hat bölgelerini geçersiz hale geldiklerinde yok etmek ve gerektiğinde yeni ana hat bölgeleri oluşturmak için metin arabelleği içeriğini izler.

### <a name="to-implement-a-client-controlled-outline-region"></a>İstemci denetimli bir ana hat bölgesi uygulamak için

1. `QueryService`İçin çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Bu, için bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>Belirli bir metin arabelleği için bir işaretçiye geçerek çağrı yapın. Bu, bir gizli metin oturumunun arabellekte zaten mevcut olup olmadığını belirler.

3. Bir metin oturumu zaten varsa, bir tane oluşturmanız gerekmez ve var olan nesneye yönelik bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür. Bu işaretçiyi, ana hat bölgelerini numaralandırmak ve oluşturmak için kullanın. Aksi takdirde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> arabellek için gizli metin oturumu oluşturma çağrısı yapın. Nesneye yönelik bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> döndürülür.

    > [!NOTE]
    > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>' İ çağırdığınızda gizli bir metin istemcisi (yani, bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> nesnesi) belirtebilirsiniz. Bu istemci, gizli bir metin veya ana hat bölgesi Kullanıcı tarafından genişletildiğinde veya daraltıldığında size bildirir.

4. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> yapısı) parametresi: bir <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> gizli bölge yerine bir anahat bölgesi oluşturduğunuz belirten yapının üyesinde bir değer belirtin. Bölgenin, yapının üyesinde istemci denetimli mi yoksa düzenleyici denetimli mi olduğunu belirtin `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Akıllı anahat uygulamanız, düzenleyici ve istemci denetimli ana hat bölgelerinin bir karışımını içerebilir. Ana hat bölgeniz, yapının üyesinde "..." gibi daraltıldığında görüntülenen başlık metnini belirtin `pszBanner` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Düzenleyicinin gizli bölge için varsayılan başlık metni "..." dir.
