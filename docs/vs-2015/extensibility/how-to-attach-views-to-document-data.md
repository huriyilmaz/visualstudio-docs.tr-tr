---
title: 'Nasıl yapılır: belge verilerine görünümler Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bc1b57e189902624c13149d0264142ff66af050
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799292"
---
# <a name="how-to-attach-views-to-document-data"></a>Nasıl Yapılır: Belge Verilerine Görünüm Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeni bir belge görünümleriniz varsa, varolan bir belge veri nesnesine iliştirebilirsiniz.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Varolan bir belge verisi nesnesine bir görünüm iliştirilemiyor olup olmadığını belirleme  
  
1. Uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  
  
2. Uygulamanızda `IVsEditorFactory::CreateEditorInstance` `QueryInterface` uygulamanızı çağırdığında mevcut belge verileri nesnesini çağırın `CreateEditorInstance` .  
  
     Çağırmak `QueryInterface` , parametresinde belirtilen varolan belge verileri nesnesini incelemenizi sağlar `punkDocDataExisting` .  
  
     Bununla birlikte, sorgu yapmanız gereken tam arabirimler, 4. adımda özetlenen belgeyi açan düzenleyiciye bağlıdır.  
  
3. Mevcut belge verileri nesnesinde uygun arabirimleri bulamazsanız, belge verileri nesnesinin düzenleyicinizle uyumsuz olduğunu belirten bir hata kodu düzenleyicinize döndürün.  
  
     IDE 'nin uygulamasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , bir ileti kutusu, belgenin başka bir düzenleyicide açık olduğunu ve bunu kapatmak isteyip istemediğinizi sorar.  
  
4. Bu belgeyi kapatırsanız, Visual Studio, düzenleyici fabrikasını ikinci bir kez çağırır. Bu çağrıda, `DocDataExisting` PARAMETRESI null değerine eşittir. Düzenleyici Fabrika uygulamanız daha sonra belge verileri nesnesini kendi Düzenleyicinizde açabilir.  
  
    > [!NOTE]
    > Varolan bir belge verileri nesnesiyle çalışamayacağını öğrenmek için özel uygulamanızın gerçek sınıfına bir işaretçi atayarak arabirim uygulamasının özel bilgisini de kullanabilirsiniz [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] . Örneğin, ' den devralan tüm standart düzenleyiciler uygular `IVsPersistFileFormat` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Bu nedenle, için ' i çağırabilir `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> ve var olan belge verileri NESNESINDEKI sınıf kimliği UYGULAMANıZıN sınıf kimliğiyle eşleşiyorsa, belge verileri nesnesiyle çalışabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Visual Studio yöntemi uygulamanızı çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , varsa, parametresindeki mevcut belge veri nesnesine bir işaretçi geçirir `punkDocDataExisting` . `punkDocDataExisting`Belge verileri nesnesinin, bu konudaki yordamın 4. adımında gösterildiği gibi, düzenleyicinize göre uygun olup olmadığını öğrenmek için ' de döndürülen belge verileri nesnesini inceleyin. Uygunsa, Düzenleyici fabrikanızın [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md)bölümünde özetlenen ikinci bir görünüm sağlaması gerekir. Aksi takdirde, uygun bir hata iletisi görüntülenmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu belge görünümlerini destekleme](../extensibility/supporting-multiple-document-views.md)   
 [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)
