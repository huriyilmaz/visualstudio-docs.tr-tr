---
title: Birden Çok Belge Görüntüleme | Microsoft Docs
description: Visual Studio SDK'daki özel düzenleyiciniz için ayrı belge verileri ve belge görünümü nesneleri kullanarak bir belgenin birden fazla görünümünü sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 67c61071ee877e147d806a29f7c36c0dad1eb848
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117442"
---
# <a name="supporting-multiple-document-views"></a>Birden Çok Belge Görünümünü Destekleme
Düzenleyiciniz için ayrı belge verileri ve belge görünümü nesneleri oluşturarak bir belgenin birden fazla görünümünü sekleyebilirsiniz. Ek belge görünümünün yararlı olduğu bazı durumlar:

- Yeni pencere desteği: Düzenleyicinizin aynı türde iki veya daha fazla görünüm sağlamalarını, böylece düzenleyicide zaten penceresi açık olan  bir kullanıcının Pencere  menüsünden Yeni Pencere komutunu seçerek yeni bir pencere açabilirsiniz.

- Form ve kod görünümü desteği: Düzenleyicinizin farklı türlerde görünümler sağlamalarını istediğiniz. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], örneğin, hem form görünümü hem de kod görünümü sağlar.

  Bu konuda daha fazla bilgi için, Visual Studio Paket Şablonu tarafından oluşturulan özel düzenleyici projesinde EditorFactory.cs dosyasındaki CreateEditorInstance yordamına bakın. Bu proje hakkında daha fazla bilgi için [bkz. Kılavuz: Özel Düzenleyici Oluşturma.](../extensibility/walkthrough-creating-a-custom-editor.md)

## <a name="synchronizing-views"></a>Görünümleri Eşitleme
 Birden çok görünüm uygulayan belge veri nesnesi, tüm görünümlerin verilerle eşitlenmiş durumda tutmakla sorumludur. Verilerle birden çok görünüm eşitlemek için <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> üzerinde olay işleme arabirimlerini kullanabilirsiniz.

 Birden çok görünümleri eşitlemek için nesnesini kullansanız, belge veri nesnesinde yapılan değişiklikleri işlemek için kendi olay <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sisteminizi uygulamanız gerekir. Birden çok görünümleri güncel tutmak için farklı ayrıntı düzeyleri kullanabilirsiniz. En fazla ayrıntı ayrıntı ayarıyla, siz bir görünümde yazarak diğer görünümler hemen güncelleştirilir. Minimum ayrıntıyla, diğer görünümler etkinleştirilene kadar güncelleştirilmez.

## <a name="determining-whether-document-data-is-already-open"></a>Belge Verileri'nin Zaten Açık Olup Olmadığını Belirleme
 Tümleşik geliştirme ortamında (IDE) çalışan belge tablosu (RDT), aşağıdaki diyagramda gösterildiği gibi bir belge için verilerin zaten açık olup olmadığının izlenmesinde yardımcı olur.

 ![DocDataView grafiği](../extensibility/media/docdataview.gif "Docdataview") Birden çok görünüm

 Varsayılan olarak, her görünüm (belge görünümü nesnesi) kendi pencere çerçevesinde ( ) yer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> alır. Ancak daha önce de not edildiklerine göre belge verileri birden çok görünümde görüntülenebilir. Bunu etkinleştirmek için Visual Studio ilgili belgenin zaten bir düzenleyicide açık olup olmadığını belirlemek üzere RDT'yi denetler. IDE düzenleyiciyi oluşturmak için çağırsa, parametresinde döndürülen NULL olmayan bir değer belgenin zaten başka bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> `punkDocDataExisting` düzenleyicide açık olduğunu gösterir. RDT işlevleri hakkında daha fazla bilgi için bkz. [Belge Tablosu Çalıştırma.](../extensibility/internals/running-document-table.md)

 Uygulamanıza, belge verilerini düzenleyiciniz için uygun olup olmadığını belirlemek için içinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> döndürülen belge veri nesnesini `punkDocDataExisting` incele. (Örneğin, bir HTML düzenleyicisi tarafından yalnızca HTML verileri görüntüleniyor.) Uygunsa düzenleyici fabrikanız veriler için ikinci bir görünüm sağlasa iyi olur. parametresi yoksa, belge veri nesnesinin başka bir düzenleyicide açık olması veya belge verisi büyük olasılıkla aynı düzenleyiciye sahip farklı bir görünümde zaten açık olması `punkDocDataExisting` `NULL` mümkündür. Belge verileri düzenleyici fabrikanız tarafından desteklemez farklı bir düzenleyicide açıksa Visual Studio fabrikanızı açamazsınız. Daha fazla bilgi için, [bkz. How to: Attach Views to Document Data](../extensibility/how-to-attach-views-to-document-data.md).
