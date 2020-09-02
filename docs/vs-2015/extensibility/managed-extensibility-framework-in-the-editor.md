---
title: Düzenleyicide Managed Extensibility Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f19b71c86d972b59a9d46f379bf7ec93f63aeb9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679951"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Düzenleyicide Managed Extensibility Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici, Managed Extensibility Framework (MEF) bileşenleri kullanılarak oluşturulur. Düzenleyiciyi genişletmek için kendi MEF bileşenlerinizi oluşturabilirsiniz ve kodunuz da düzenleyici bileşenlerini kullanabilir.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework genel bakış  
 MEF, MEF programlama modelini izleyen bir uygulamanın veya bileşenin özelliklerini eklemenize ve değiştirmenize olanak tanıyan bir .NET kitaplığıdır. Visual Studio Düzenleyicisi, MEF bileşen parçalarını sağlayabilir ve kullanabilir.  
  
 MEF .NET Framework sürüm 4 System.ComponentModel.Composition.dll derlemesinde bulunur.  
  
 MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Bileşen parçaları ve bileşim kapsayıcıları  
 Bileşen bölümü, aşağıdakilerden birini (veya her ikisini de) yapan bir sınıf veya sınıf üyesidir:  
  
- Başka bir bileşen tüketme  
  
- Başka bir bileşen tarafından tüketilmelidir  
  
  Örneğin, bir ambar envanteri bileşeni tarafından sunulan ürün kullanılabilirliği verilerine bağlı bir sipariş girişi bileşeni olan bir alışveriş uygulamasını düşünün. MEF koşullarında, envanter bölümü ürün kullanılabilirlik verilerini *dışa aktarabilir* ve sipariş girişi bölümü verileri *içeri aktarabilir* . Order entry bölümü ve stok bölümünün birbirleriyle ilgili bilmeleri gerekmez; *birleştirme kapsayıcısı* (konak uygulama tarafından sağlanır), dışarı aktarmalar kümesini korumadan ve dışarı aktarmaları ve içeri aktarmaları çözümlemeden sorumludur.  
  
  Birleşim kapsayıcısı, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> genellikle ana bilgisayara aittir. Bileşim kapsayıcısı, dışarıya aktarılmış bileşen bölümlerinin *kataloğunu* tutar.  
  
### <a name="exporting-and-importing-component-parts"></a>Bileşen parçalarını dışarı ve Içeri aktarma  
 Bir genel sınıf veya bir sınıfın genel üyesi (özellik veya yöntem) olarak uygulandığı sürece tüm işlevleri dışarı aktarabilirsiniz. Bileşen parçasını ' den türetmeniz gerekmez <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Bunun yerine, <xref:System.ComponentModel.Composition.ExportAttribute> dışarı aktarmak istediğiniz sınıfa veya sınıf üyesine bir öznitelik eklemeniz gerekir. Bu öznitelik, başka bir bileşen bölümünün işlevselliği içeri aktarabileceği *sözleşmeyi* belirtir.  
  
### <a name="the-export-contract"></a>Sözleşmeyi dışarı aktar  
 , <xref:System.ComponentModel.Composition.ExportAttribute> Verilirken varlığı (sınıf, arabirim veya yapı) tanımlar. Genellikle, Export özniteliği dışa aktarma türünü belirten bir parametre alır.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Varsayılan olarak öznitelik, <xref:System.ComponentModel.Composition.ExportAttribute> dışarı aktarma sınıfının türü olan bir sözleşmeyi tanımlar.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Örnekte, varsayılan `[Export]` özniteliği değerine eşdeğerdir `[Export(typeof(TestAdornmentLayerDefinition))]` .  
  
 Ayrıca, aşağıdaki örnekte gösterildiği gibi bir özelliği veya yöntemi de dışarı aktarabilirsiniz.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>MEF dışarı aktarma içeri aktarılıyor  
 Bir MEF dışarı aktarma kullanmak istediğinizde, bir sözleşmeyi (genellikle türü) dışa aktarıldığında ve <xref:System.ComponentModel.Composition.ImportAttribute> bu değere sahip bir özniteliği eklemeniz gerekir. Varsayılan olarak, içeri aktarma özniteliği, değiştirdiği sınıfın türü olan bir parametre alır. Aşağıdaki kod satırları türü içeri aktarır <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> .  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>MEF bileşeni bölümünden düzenleyici Işlevselliği alma  
 Mevcut kodunuz bir MEF bileşeni parçasıysa, düzenleyici bileşen parçalarını kullanmak için MEF meta verilerini kullanabilirsiniz.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Bir MEF bileşeni bölümünden düzenleyici işlevlerini kullanmak için  
  
1. Genel derleme önbelleğinde (GAC) ve düzenleyici derlemelerindeki System.Composition.ComponentModel.dll başvuruları ekleyin.  
  
2. İlgili using deyimlerini ekleyin.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. `[Import]`Özniteliğini aşağıdaki gibi hizmet arayüzüne ekleyin.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. Hizmeti edindiğinizde, bileşenlerinden birini kullanabilirsiniz.  
  
5. Derlemenizi derledikten sonra içine koyun. Visual Studio yüklemenizin \Common7\IDE\Components\ klasörü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)
