---
title: Düzenleyicide Managed Extensibility Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632616"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Düzenleyicide Managed Extensibility Framework
Düzenleyici, Managed Extensibility Framework (MEF) bileşenleri kullanılarak oluşturulur. Düzenleyiciyi genişletmek için kendi MEF bileşenlerinizi oluşturabilirsiniz ve kodunuz da düzenleyici bileşenlerini kullanabilir.

## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework genel bakış
 MEF, MEF programlama modelini izleyen bir uygulamanın veya bileşenin özelliklerini eklemenize ve değiştirmenize olanak tanıyan bir .NET kitaplığıdır. Visual Studio Düzenleyicisi, MEF bileşen parçalarını sağlayabilir ve kullanabilir.

 MEF, .NET Framework sürüm 4 *System. ComponentModel. Composition. dll* derlemesinde bulunur.

 MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Bileşen parçaları ve bileşim kapsayıcıları
 Bileşen bölümü, aşağıdakilerden birini (veya her ikisini de) yapan bir sınıf veya sınıf üyesidir:

- Başka bir bileşen tüketme

- Başka bir bileşen tarafından tüketilmelidir

  Örneğin, bir ambar envanteri bileşeni tarafından sunulan ürün kullanılabilirliği verilerine bağlı bir sipariş girişi bileşeni olan bir alışveriş uygulamasını düşünün. MEF koşullarında, envanter bölümü ürün kullanılabilirlik verilerini *dışa aktarabilir* ve sipariş girişi bölümü verileri *içeri aktarabilir* . Order entry bölümü ve stok bölümünün birbirleriyle ilgili bilmeleri gerekmez; *birleştirme kapsayıcısı* (konak uygulama tarafından sağlanır), dışarı aktarmalar kümesini korumadan ve dışarı aktarmaları ve içeri aktarmaları çözümlemeden sorumludur.

  @No__t_0 bileşim kapsayıcısı, genellikle ana bilgisayara aittir. Bileşim kapsayıcısı, dışarıya aktarılmış bileşen bölümlerinin *kataloğunu* tutar.

### <a name="export-and-import-component-parts"></a>Bileşen parçalarını dışarı ve içeri aktarma
 Bir genel sınıf veya bir sınıfın genel üyesi (özellik veya yöntem) olarak uygulandığı sürece tüm işlevleri dışarı aktarabilirsiniz. Bileşen parçasını <xref:System.ComponentModel.Composition.Primitives.ComposablePart> türetmeniz gerekmez. Bunun yerine, dışarı aktarmak istediğiniz sınıfa veya sınıf üyesine bir <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği eklemeniz gerekir. Bu öznitelik, başka bir bileşen bölümünün işlevselliği içeri aktarabileceği *sözleşmeyi* belirtir.

### <a name="the-export-contract"></a>Sözleşmeyi dışarı aktar
 @No__t_0, dışarıya aktarılmakta olan varlığı (sınıf, arabirim veya yapı) tanımlar. Genellikle, Export özniteliği dışa aktarma türünü belirten bir parametre alır.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Varsayılan olarak, <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği dışa aktarma sınıfının türü olan bir sözleşmeyi tanımlar.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Örnekte, varsayılan `[Export]` özniteliği `[Export(typeof(TestAdornmentLayerDefinition))]` eşdeğerdir.

 Ayrıca, aşağıdaki örnekte gösterildiği gibi bir özelliği veya yöntemi de dışarı aktarabilirsiniz.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>MEF dışarı aktarmayı içeri aktarma
 Bir MEF dışarı aktarma kullanmak istediğinizde, (genellikle türü), dışarı aktarılırken sözleşmeyi bilmeniz ve bu değere sahip bir <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği eklemeniz gerekir. Varsayılan olarak, içeri aktarma özniteliği, değiştirdiği sınıfın türü olan bir parametre alır. Aşağıdaki kod satırları <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> türünü içeri aktarır.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF bileşeni bölümünden düzenleyici işlevselliği al
 Mevcut kodunuz bir MEF bileşeni parçasıysa, düzenleyici bileşen parçalarını kullanmak için MEF meta verilerini kullanabilirsiniz.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Bir MEF bileşeni bölümünden düzenleyici işlevlerini kullanmak için

1. Genel derleme önbelleğinde (GAC) ve düzenleyici derlemelerindeki *System. Composition. ComponentModel. dll*' ye başvurular ekleyin.

2. İlgili using yönergelerini ekleyin.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. @No__t_0 özniteliğini aşağıdaki gibi hizmet arayüzüne ekleyin.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Hizmeti edindiğinizde, bileşenlerinden birini kullanabilirsiniz.

5. Derlemenizi derledikten sonra *... Visual Studio yüklemenizin \Common7\IDE\Components \* klasörü.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
