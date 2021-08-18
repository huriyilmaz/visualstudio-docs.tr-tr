---
title: Managed Extensibility Framework Düzenleyicisi'nde | Microsoft Docs
description: Visual Studio SDK Managed Extensibility Framework da düzenleyiciyi genişletmek için kendi bileşenlerinizi oluşturmanızı sağlayan Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 52492e48ed9b5e2150f31c18ac07f66e45486054
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102317"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework düzenleyicide
Düzenleyici, Managed Extensibility Framework (MEF) bileşenleri kullanılarak oluşur. Düzenleyiciyi genişletmek için kendi MEF bileşenlerinizi de derlemeniz gerekir ve kodunuz düzenleyici bileşenlerini de tüketir.

## <a name="overview-of-the-managed-extensibility-framework"></a>Genel bakış Managed Extensibility Framework
 MEF, MEF programlama modelini izleyen bir uygulamanın veya bileşenin özelliklerini eklemenize ve değiştirmenize olanak sağlayan bir .NET kitaplığıdır. Bu Visual Studio, MEF bileşen parçalarını hem s hem de tüketir.

 MEF, derlemenin 4. .NET Framework sürümünde *System.ComponentModel.Composition.dll* içerir.

 MEF hakkında daha fazla bilgi için [bkz. Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Bileşen parçaları ve bileşim kapsayıcıları
 Bileşen bölümü, aşağıdakilerden birini (veya ikisini birden) gerçekleştiren bir sınıf veya sınıfın üyesidir:

- Başka bir bileşeni kullanma

- Başka bir bileşen tarafından tüketilme

  Örneğin, bir ambar envanter bileşeni tarafından sağlanan ürün kullanılabilirlik verilerine bağlı olan bir sipariş girişi bileşenine sahip olan bir alışveriş uygulamasını düşünün. MEF açısından, envanter bölümü ürün *kullanılabilirlik* verilerini dışarı aktarabilirsiniz ve sipariş girişi bölümü verileri *içeri* aktarabilirsiniz. Sipariş girişi bölümü ve envanter bölümü birbirini bilmek zorunda değildir; bileşim *kapsayıcısı* (konak uygulama tarafından sağlanır) dışarı aktarma kümelerinin korunmasından ve dışarı aktarmaların ve içeri aktarmaların çözümden sorumludur.

  Oluşturma <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> kapsayıcısı, genellikle ana bilgisayar tarafından aittir. Bileşim kapsayıcısı, dışarı *aktaran bileşen* parçalarının kataloğunu sağlar.

### <a name="export-and-import-component-parts"></a>Bileşen parçalarını dışarı ve içeri aktarma
 Genel sınıf olarak veya bir sınıfın genel üyesi (özellik veya yöntem) olarak uygulanmış olduğu sürece, herhangi bir işlevi dışarı aktarabilirsiniz. bileşeni parçanızı 'den türetmek zorunda <xref:System.ComponentModel.Composition.Primitives.ComposablePart> değildir. Bunun yerine, dışarı <xref:System.ComponentModel.Composition.ExportAttribute> aktarmayı istediğiniz sınıf veya sınıf üyesine bir öznitelik eklemeniz gerekir. Bu öznitelik, başka *bir bileşen* parçasının işlevselliğinizi içeri aktarama sözleşmesini belirtir.

### <a name="the-export-contract"></a>Dışarı aktarma sözleşmesi
 <xref:System.ComponentModel.Composition.ExportAttribute>, dışarı aktaran varlığı (sınıf, arabirim veya yapı) tanımlar. Genellikle, dışarı aktarma özniteliği dışarı aktarma türünü belirten bir parametre alır.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Varsayılan olarak, <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği dışarı aktarma sınıfının türü olan bir sözleşme tanımlar.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Örnekte, varsayılan öznitelik `[Export]` ile `[Export(typeof(TestAdornmentLayerDefinition))]` eşdeğerdir.

 Ayrıca, aşağıdaki örnekte gösterildiği gibi bir özelliği veya yöntemi dışarı aktarabilirsiniz.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>MEF Dışarı Aktarmayı İçeri Aktarma
 BIR MEF dışarı aktarması tüketmek istediğiniz zaman, dışarı aktarıldı olduğu sözleşmeyi (genellikle türü) biliyor ve bu değere sahip bir <xref:System.ComponentModel.Composition.ImportAttribute> öznitelik eklemeniz gerekir. Varsayılan olarak, içeri aktarma özniteliği değiştirerek sınıf türü olan bir parametre alır. Aşağıdaki kod satırları türünü içeri <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> aktarın.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF bileşen parçasından düzenleyici işlevselliği elde et
 Mevcut kodunuz bir MEF bileşeni parçası ise, düzenleyici bileşen parçalarını kullanmak için MEF meta verilerini kullanabilirsiniz.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Bir MEF bileşen parçasından düzenleyici işlevselliğini kullanmak için

1. genel derleme *önbelleğinde (GAC)* olanSystem.Composition.ComponentModel.dllve düzenleyici derlemelerine başvurular ekleyin.

2. İlgili using yönergelerini ekleyin.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. özniteliğini `[Import]` aşağıdaki gibi hizmet arabiriminize ekleyin.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Hizmeti edinirsiniz, bileşenlerinden herhangi birini tüketebilirsiniz.

5. Derlemenizi derledik, *.. Uygulama yüklemenizin \Common7\IDE\Components \* Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)
