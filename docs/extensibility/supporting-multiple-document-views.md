---
title: Birden Çok Belge Görüntülemeyi Destekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699548"
---
# <a name="supporting-multiple-document-views"></a>Birden Çok Belge Görünümünü Destekleme
Düzenleyiciniz için ayrı belge verileri ve belge görünümü nesneleri oluşturarak belgenin birden fazla görünümünü sağlayabilirsiniz. Ek bir belge görünümünün yararlı olacağı bazı durumlar şunlardır:

- Yeni pencere desteği: Düzenleyicinizin aynı türde iki veya daha fazla görünüm sağlamasını, böylece düzenleyicide zaten penceresi açık olan bir kullanıcının **Pencere** menüsünden **Yeni Pencere** komutunu seçerek yeni bir pencere açabileceğini istersiniz.

- Form ve kod görünümü desteği: Düzenleyicinizin farklı türde görünümler sağlamasını istiyorsunuz. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], örneğin, hem form görünümü hem de kod görünümü sağlar.

  Bu konuda daha fazla bilgi için Visual Studio Package Template tarafından oluşturulan özel düzenleyici projesindeki EditorFactory.cs dosyasındaki CreateEditorInstance yordamına bakın. Bu proje hakkında daha fazla bilgi için [Walkthrough: Creating a Custom Editor](../extensibility/walkthrough-creating-a-custom-editor.md)'a bakın.

## <a name="synchronizing-views"></a>Görünümleri Eşitleme
 Birden çok görünüm uyguladığınızzaman, belge veri nesnesi tüm görünümleri verilerle eşitlenmiş tutmaktan sorumludur. Birden çok görünümü verilerle <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> eşitlemek için olay işleme arabirimlerini kullanabilirsiniz.

 Nesneyi <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> birden çok görünümü eşitlemek için kullanmıyorsanız, belge veri nesnesi üzerinde yapılan değişiklikleri işlemek için kendi olay sisteminizi uygulamanız gerekir. Birden çok görünümü güncel tutmak için farklı parçalı lık düzeyleri kullanabilirsiniz. Maksimum parçalılık ayarı ile, bir görünümde yazarken diğer görünümler hemen güncelleştirilir. Minimum parçalılıkla, diğer görünümler etkinleştirilene kadar güncelleştirilmez.

## <a name="determining-whether-document-data-is-already-open"></a>Belge Verilerinin Zaten Açık Olup Olmadığını Belirleme
 Tümleşik geliştirme ortamında (IDE) çalışan belge tablosu (RDT), aşağıdaki diyagramda gösterildiği gibi belge için verilerin zaten açık olup olmadığını izlemenize yardımcı olur.

 ![DocDataView grafiği](../extensibility/media/docdataview.gif "Docdataview") Birden çok görüntüleme

 Varsayılan olarak, her görünüm (belge görünümü nesnesi)<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>kendi pencere çerçevesi içinde bulunur ( ). Ancak, daha önce de belirtildiği gibi, belge verileri birden çok görünümde görüntülenebilir. Bunu etkinleştirmek için Visual Studio, söz konusu belgenin bir düzenleyicide zaten açık olup olmadığını belirlemek için RDT'yi denetler. IDE düzenleyiciyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> oluşturmak için aradığında, `punkDocDataExisting` parametrede döndürülen NULL olmayan bir değer belgenin başka bir düzenleyicide zaten açık olduğunu gösterir. RDT'nin nasıl çalıştığı hakkında daha fazla bilgi için [Bkz. Belge Tablosunu Çalıştır.](../extensibility/internals/running-document-table.md)

 Uygulamanızda, belge verilerinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> düzenleyiciniz `punkDocDataExisting` için uygun olup olmadığını belirlemek için döndürülen belge veri nesnesini inceleyin. (Örneğin, yalnızca HTML verileri bir HTML düzenleyicisi tarafından görüntülenmelidir.) Uygunsa, düzenleyici fabrikanız veriler için ikinci bir görünüm sağlamalıdır. `punkDocDataExisting` Parametre değilse, `NULL`belge veri nesnesinin başka bir düzenleyicide açık olması veya daha büyük olasılıkla belge verilerinin aynı düzenleyiciyle farklı bir görünümde açık olması mümkündür. Belge verileri, düzenleyici fabrikanızın desteklemediği farklı bir düzenleyicide açıksa, Visual Studio düzenleyici fabrikanızı açamaz. Daha fazla bilgi için [bkz: Belge Verilerine Görünümler Ekleme](../extensibility/how-to-attach-views-to-document-data.md).
