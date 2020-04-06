---
title: 'Nasıl Kullanılır: Belge Verilerine Görünüm Ekleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711086"
---
# <a name="how-to-attach-views-to-document-data"></a>Nasıl kullanılır: Belge verilerine görünüm ekleme
Yeni bir belge görünümünüz varsa, varolan bir belge veri nesnesine ekleyebilirsiniz.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Varolan bir belge veri nesnesine görünüm ekleyebilir misiniz belirlemek için

1. Uygulayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>

2. IDE uygulamanızı aradığında, varolan belge veri nesnesini `IVsEditorFactory::CreateEditorInstance`uygulamanızda `QueryInterface` `CreateEditorInstance` arayın.

    Arama, `QueryInterface` parametrede belirtilen varolan belge veri nesnesini `punkDocDataExisting` incelemenize olanak tanır.

    Ancak, tam olarak sorgulamanız gereken arabirimler, adım 4'te belirtildiği gibi belgeyi açan düzenleyiciye bağlıdır.

3. Varolan belge veri nesnesinde uygun arabirimleri bulamazsanız, belge veri nesnesinin düzenleyicinizle uyumsuz olduğunu belirten bir hata kodunu düzenleyicinize döndürün.

    IDE'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>uygulamasında, bir ileti kutusu belgenin başka bir düzenleyicide açık olduğunu size bildirimde ve kapatmak isteyip istemediğiniz sorulur.

4. Bu belgeyi kapatırsanız, Visual Studio editör fabrikanızı ikinci kez arar. Bu çağrıda, `DocDataExisting` parametre NULL eşittir. Düzenleyici fabrika uygulamanız daha sonra belge veri nesnesini kendi düzenleyicinizde açabilir.

   > [!NOTE]
   > Varolan bir belge veri nesnesi ile çalışıp çalışamayacağınızı belirlemek için, özel uygulamanızın gerçek [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] sınıfına bir işaretçi atarak arabirim uygulamasının özel bilgilerini de kullanabilirsiniz. Örneğin, tüm standart düzenleyiciler `IVsPersistFileFormat`, <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>hangi devralır. Bu nedenle, `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>varolan belge veri nesnesindeki sınıf kimliği uygulamanızın sınıf kimliğiyle eşleşirse, belge veri nesnesiyle çalışabilirsiniz.

## <a name="robust-programming"></a>Sağlam programlama
 Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemin uygulamanızı aradığında, varsa `punkDocDataExisting` parametredeki varolan belge veri nesnesine bir işaretçi geri geçirir. Belge veri nesnesinin `punkDocDataExisting` bu konudaki yordamın 4. Uygunsa, düzenleyici fabrikanız [Destek birden çok belge görünümünde](../extensibility/supporting-multiple-document-views.md)özetlenen veriler için ikinci bir görünüm sağlamalıdır. Değilse, uygun bir hata iletisi görüntülemesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Birden çok belge görüntülemeyi destekleme](../extensibility/supporting-multiple-document-views.md)
- [Özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)
