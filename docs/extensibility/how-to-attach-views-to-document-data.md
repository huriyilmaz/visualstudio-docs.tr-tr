---
title: 'Nasıl kullanılır: Belge VerileriNe Görünümler Ekleme | Microsoft Docs'
description: Mevcut bir belge veri nesnesine yeni bir belge görünümü ekleyebilirsiniz. Görünümü ekp ekley olup olmadığını belirlemek için bu yordamı kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4171f80f3dc63fb00a64fc99c3620771ea8c48c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626271"
---
# <a name="how-to-attach-views-to-document-data"></a>Nasıl kullanılır: Belge verilerine görünüm ekleme
Yeni bir belge görünümünüz varsa, bunu mevcut bir belge veri nesnesine ekleyebilirsiniz.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Var olan bir belge veri nesnesine görünüm ekley olup olmadığını belirlemek için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>uygulama.

2. uygulamanıza `IVsEditorFactory::CreateEditorInstance` , `QueryInterface` IDE uygulamanızı çağıran mevcut belge veri nesnesi üzerinde `CreateEditorInstance` çağrısı.

    çağrısı, `QueryInterface` parametresinde belirtilen mevcut belge veri nesnesini incelemeye olanak `punkDocDataExisting` sağlar.

    Ancak, sorgulaması gereken tam arabirimler, 4. adımda özetlenen şekilde belgeyi açmakta olan düzenleyiciye bağlıdır.

3. Mevcut belge veri nesnesinde uygun arabirimleri bulamazsanız, düzenleyicinize belge veri nesnesinin düzenleyiciniz ile uyumsuz olduğunu belirten bir hata kodu döndürür.

    IDE'nin uygulamasında, bir ileti kutusu belgenin başka bir düzenleyicide açık olduğunu size iletir ve kapatmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> isterken sorar.

4. Bu belgeyi kapatırsanız düzenleyici Visual Studio kez çağırabilirsiniz. Bu çağrıda parametresi `DocDataExisting` NULL'a eşittir. Düzenleyici fabrika uygulamanız daha sonra belge veri nesnesini kendi düzenleyicinize açabilir.

   > [!NOTE]
   > Mevcut bir belge veri nesnesiyle çalışıp çalışılamayacaklarını belirlemek için, özel uygulamanıza yönelik gerçek sınıfına bir işaretçi atarak arabirim uygulamasına yönelik özel [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] bilgileri de kullanabilirsiniz. Örneğin, tüm standart düzenleyiciler ' den `IVsPersistFileFormat` devralan 'i <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> uygulama. Bu nedenle, için çağrısı da kullanabilirsiniz ve mevcut belge veri nesnesinde sınıf kimliği, uygulamanın sınıf kimliğiyle eşlese, belge veri `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> nesnesiyle çalışabilirsiniz.

## <a name="robust-programming"></a>Güçlü programlama
 Bu Visual Studio yöntemini uygulamanıza çağrılsa, varsa parametresinde var olan belge veri nesnesine bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> `punkDocDataExisting` işaretçi geri iletir. Belge veri nesnesinin düzenleyiciniz için uygun olup olmadığını belirlemek için bu konudaki `punkDocDataExisting` yordamın 4. adımını incelenin. Uygunsa düzenleyici fabrikanız, Birden çok belge görünümünü destek altında açıklanan şekilde veriler için ikinci [bir görünüm sağlay seçmelidir.](../extensibility/supporting-multiple-document-views.md) Yoksa, uygun bir hata iletisi görüntülemesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Birden çok belge görünümlerini destekleme](../extensibility/supporting-multiple-document-views.md)
- [Özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)
