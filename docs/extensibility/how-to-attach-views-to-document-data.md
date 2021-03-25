---
title: 'Nasıl yapılır: belge verilerine görünümler Iliştirme | Microsoft Docs'
description: Varolan bir belge veri nesnesine yeni bir belge görünümü iliştirebilirsiniz. Görünümü iliştireip eklenemediğini öğrenmek için bu yordamı kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a034fc1c7cded7de4ead38cfba5d3410341c95d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057422"
---
# <a name="how-to-attach-views-to-document-data"></a>Nasıl yapılır: belge verilerine görünümler Iliştirme
Yeni bir belge görünümleriniz varsa, varolan bir belge veri nesnesine iliştirebilirsiniz.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Varolan bir belge verisi nesnesine bir görünüm iliştirilemiyor olup olmadığını belirleme

1. Uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .

2. Uygulamanızda `IVsEditorFactory::CreateEditorInstance` `QueryInterface` uygulamanızı çağırdığında mevcut belge verileri nesnesini çağırın `CreateEditorInstance` .

    Çağırmak `QueryInterface` , parametresinde belirtilen varolan belge verileri nesnesini incelemenizi sağlar `punkDocDataExisting` .

    Bununla birlikte, sorgu yapmanız gereken tam arabirimler, 4. adımda özetlenen belgeyi açan düzenleyiciye bağlıdır.

3. Mevcut belge verileri nesnesinde uygun arabirimleri bulamazsanız, belge verileri nesnesinin düzenleyicinizle uyumsuz olduğunu belirten bir hata kodu düzenleyicinize döndürün.

    IDE 'nin uygulamasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , bir ileti kutusu, belgenin başka bir düzenleyicide açık olduğunu ve bunu kapatmak isteyip istemediğinizi sorar.

4. Bu belgeyi kapatırsanız, Visual Studio, düzenleyici fabrikasını ikinci bir kez çağırır. Bu çağrıda, `DocDataExisting` PARAMETRESI null değerine eşittir. Düzenleyici Fabrika uygulamanız daha sonra belge verileri nesnesini kendi Düzenleyicinizde açabilir.

   > [!NOTE]
   > Varolan bir belge verileri nesnesiyle çalışamayacağını öğrenmek için özel uygulamanızın gerçek sınıfına bir işaretçi atayarak arabirim uygulamasının özel bilgisini de kullanabilirsiniz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] . Örneğin, ' den devralan tüm standart düzenleyiciler uygular `IVsPersistFileFormat` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Bu nedenle, için ' i çağırabilir `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> ve var olan belge verileri NESNESINDEKI sınıf kimliği UYGULAMANıZıN sınıf kimliğiyle eşleşiyorsa, belge verileri nesnesiyle çalışabilirsiniz.

## <a name="robust-programming"></a>Güçlü programlama
 Visual Studio yöntemi uygulamanızı çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , varsa, parametresindeki mevcut belge veri nesnesine bir işaretçi geçirir `punkDocDataExisting` . `punkDocDataExisting`Belge verileri nesnesinin, bu konudaki yordamın 4. adımında gösterildiği gibi, düzenleyicinize göre uygun olup olmadığını öğrenmek için ' de döndürülen belge verileri nesnesini inceleyin. Uygunsa, Düzenleyici fabrikanızın, [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md)bölümünde özetlenen verilerin ikinci bir görünümünü sağlaması gerekir. Aksi takdirde, uygun bir hata iletisi görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çoklu belge görünümlerini destekleme](../extensibility/supporting-multiple-document-views.md)
- [Özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)
