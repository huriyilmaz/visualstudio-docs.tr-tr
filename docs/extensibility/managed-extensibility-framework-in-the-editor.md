---
title: Editörde Yönetilen Genişletilebilirlik Çerçevesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702876"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Editörde Yönetilen Genişletilebilirlik Çerçevesi
Düzenleyici Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenleri kullanılarak oluşturulur. Düzenleyiciyi genişletmek için kendi MEF bileşenlerinizi oluşturabilirsiniz ve kodunuz düzenleyici bileşenlerini de tüketebilir.

## <a name="overview-of-the-managed-extensibility-framework"></a>Yönetilen Genişletilebilirlik Çerçevesine Genel Bakış
 MEF, MEF programlama modelini izleyen bir uygulamanın veya bileşenin özelliklerini eklemenize ve değiştirmenize olanak tanıyan bir .NET kitaplığıdır. Visual Studio editörü MEF bileşen parçalarını hem sağlayabilir hem de tüketebilir.

 MEF.NET Framework sürüm 4 *System.ComponentModel.Composition.dll* derlemesinde bulunur.

 MEF hakkında daha fazla bilgi için [Yönetilen Genişletilebilirlik Çerçevesi 'ne (MEF)](/dotnet/framework/mef/index)bakın.

### <a name="component-parts-and-composition-containers"></a>Bileşen parçaları ve bileşim kapları
 Bileşen parçası, aşağıdakilerden birini (veya her ikisini) yapabilen bir sınıf veya sınıfın üyesidir:

- Başka bir bileşen tüketin

- Başka bir bileşen tarafından tüketilmelidir

  Örneğin, ambar stok bileşeni tarafından sağlanan ürün kullanılabilirlik verilerine bağlı bir sipariş giriş bileşeni olan bir alışveriş uygulaması düşünün. MEF açısından, stok parçası ürün kullanılabilirlik verilerini *dışa* aktarabilir ve sipariş giriş bölümü verileri *içe aktarabilir.* Sipariş giriş bölümü ve stok parçasının birbirleri hakkında bilinmesi gerekmez; *kompozisyon konteyner* (ana bilgisayar uygulaması tarafından sağlanan) ihracat kümesinin korunması ve ihracat ve ithalat çözme sorumludur.

  Kompozisyon kapsayıcı, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>genellikle ana bilgisayara aittir. Kompozisyon kapsayıcısı dışa aktarılan bileşen parçalarının *kataloğunu* tutar.

### <a name="export-and-import-component-parts"></a>Bileşen parçalarını dışa aktarma ve alma
 Ortak sınıf veya bir sınıfın ortak üyesi (özellik veya yöntem) olarak uygulandığı sürece, herhangi bir işlevselliği dışa aktarabilirsiniz. Bileşen parçanızı <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Bunun yerine, dışa aktarmak istediğiniz sınıf veya sınıf üyesine bir <xref:System.ComponentModel.Composition.ExportAttribute> öznitelik eklemeniz gerekir. Bu öznitelik, başka bir bileşen parçasının işlevselliğinizi içe aktarabileceği *sözleşmeyi* belirtir.

### <a name="the-export-contract"></a>İhracat sözleşmesi
 Dışa <xref:System.ComponentModel.Composition.ExportAttribute> aktarılan varlığı (sınıf, arabirim veya yapı) tanımlar. Genellikle, dışa aktarma özniteliği dışa aktarma türünü belirten bir parametre alır.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Varsayılan olarak, <xref:System.ComponentModel.Composition.ExportAttribute> öznitelik dışa aktarma sınıfının türü olan bir sözleşme tanımlar.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Örnekte, varsayılan `[Export]` öznitelik ' `[Export(typeof(TestAdornmentLayerDefinition))]`e eşdeğerdir.

 Aşağıdaki örnekte gösterildiği gibi bir özellik veya yöntem de dışa aktarabilirsiniz.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>MEF Dışa Aktarma Alma
 Bir MEF dışa aktarımını tüketmek istediğinizde, sözleşmenin (genellikle türü) dışa <xref:System.ComponentModel.Composition.ImportAttribute> aktarıldığını bilmeniz ve bu değere sahip bir öznitelik eklemeniz gerekir. Varsayılan olarak, alma özniteliği, modladığı sınıfın türü olan bir parametre alır. Kod <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> türü aşağıdaki satırları alma.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF bileşen kısmından düzenleyici işlevselliği alma
 Varolan kodunuz bir MEF bileşen parçasıysa, düzenleyici bileşen parçalarını tüketmek için MEF meta verilerini kullanabilirsiniz.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF bileşen işlemisişini bir MEF bileşeni parçasından çıkmak için

1. Genel montaj önbelleğinde (GAC) bulunan *System.Composition.ComponentModel.dll'ye*ve düzenleyici derlemelerine göndermeler ekleyin.

2. İlgili yönergeleri ekleyin.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. `[Import]` Hizmet arabiriminize aşağıdaki gibi öznitelik ekleyin.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Hizmeti aldığınızda, herhangi bir bileşenini tüketebilirsiniz.

5. Derlemenizi derlediğinizde, *...' a koyun. \Common7\IDE\Visual\* Studio yüklemenizin bileşenler klasörü.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
