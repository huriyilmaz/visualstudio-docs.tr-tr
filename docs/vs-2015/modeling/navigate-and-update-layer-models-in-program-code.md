---
title: Program kodundaki katman modellerini gezin ve güncelleştirin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668568"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Program kodunda katman modellerini gezinme ve güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, program kodu kullanarak gezinebileceğiniz ve güncelleştirebileceğiniz katman modellerindeki öğeler ve ilişkiler açıklanmıştır. Kullanıcının Görünüm noktasındaki katman diyagramları hakkında daha fazla bilgi için bkz. [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md) ve [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).

 Bu konuda açıklanan `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` modeli, daha genel bir <xref:Microsoft.VisualStudio.GraphModel> modelinde bir façlade 'dir. Bir [menü komutu veya hareket uzantısı](../modeling/add-commands-and-gestures-to-layer-diagrams.md)yazıyorsanız `Layer` modelini kullanın. [Katman doğrulama uzantısı](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)yazıyorsanız `GraphModel` kullanmak daha kolay olur.

## <a name="transactions"></a>İşlemler
 Bir modeli güncelleştirdiğinizde, değişiklikleri `ILinkedUndoTransaction` yerleştirmeyi göz önünde bulundurun. Bu, değişikliklerinizi tek bir işlem halinde gruplandırır. Değişikliklerden herhangi biri başarısız olursa, tüm işlem geri alınacaktır. Kullanıcı bir değişikliği geri alıyorsa, tüm değişiklikler birlikte geri alınacaktır.

 Daha fazla bilgi için bkz. [işlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Kapsama
 ![ILayer ve ILayerModel, her ikisi de ıkatmanları içerebilir.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Katmanlar ([ILayer](/previous-versions/ff644251(v=vs.140))) ve katman modeli ([ILayerModel](/previous-versions/ff643069(v=vs.140))), açıklamalar ve katmanlar içerebilir.

 Katman (`ILayer`) bir katman modelinde (`ILayerModel`) bulunabilir ya da başka bir `ILayer` içinde iç içe geçmiş olabilir.

 Bir açıklama veya katman oluşturmak için ilgili kapsayıcıda oluşturma yöntemlerini kullanın.

## <a name="dependency-links"></a>Bağımlılık bağlantıları
 Bir bağımlılık bağlantısı bir nesne tarafından temsil edilir. Her iki yönde de gezinilebilir:

 ![ILayerDependencyLink iki ıkatmanlı bağlar.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Bir bağımlılık bağlantısı oluşturmak için `source.CreateDependencyLink(target)` çağırın.

## <a name="comments"></a>Açıklamalar
 Açıklamalar katmanların veya katman modelinin içinde bulunabilir ve ayrıca herhangi bir katman öğesiyle bağlantılı olabilir:

 ![Açıklamalar, herhangi bir katman öğesine iliştirilebilir.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Bir yorum, None dahil olmak üzere herhangi bir sayıda öğe ile bağlantılı olabilir.

 Bir katman öğesine iliştirilmiş açıklamaları almak için şunu kullanın:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> Bir `ILayer` `Comments` özelliği, `ILayer` içinde yer alan açıklamaları alır. Onunla bağlantılı olan açıklamaları almaz.

 Uygun kapsayıcıda `CreateComment()` çağırarak bir açıklama oluşturun.

 Yorum üzerinde `CreateLink()` kullanarak bir bağlantı oluşturun.

## <a name="layer-elements"></a>Katman öğeleri
 Bir modelde yer alan tüm öğe türleri katman öğeleridir:

 ![Katman diyagramı içerikleri ılayerelements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Özellikler
 Her `ILayerElement` `Properties` adlı bir dize sözlüğüne sahiptir. Bu sözlüğü, herhangi bir katman öğesine rastgele bilgi eklemek için kullanabilirsiniz.

## <a name="artifact-references"></a>Yapıt başvuruları
 Yapıt başvurusu ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))), bir katman ve dosya, sınıf veya klasör gibi bir proje öğesi arasındaki bağlantıyı temsil eder. Kullanıcı bir katman oluştururken veya Çözüm Gezgini, Sınıf Görünümü veya Nesne Tarayıcısı öğeleri bir katman diyagramına sürükleyerek yapılar oluşturur. Herhangi bir sayıda yapıt başvurusu bir katmana bağlanabilir.

 Katman Gezgini 'ndeki her satır bir yapıt başvurusu görüntüler. Daha fazla bilgi için, bkz. [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

 Yapıt başvurularıyla ilgilenen asıl türler ve yöntemler aşağıdaki gibidir:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). Categories özelliği, bir sınıf, yürütülebilir dosya veya derleme gibi ne tür bir yapıya başvurulduğunu gösterir. Kategoriler, tanımlayıcının hedef yapıtı nasıl tanımladığını belirler.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) , bir <xref:EnvDTE.Project> veya <xref:EnvDTE.ProjectItem> yapıt başvurusu oluşturur. Bu zaman uyumsuz bir işlemdir. Bu nedenle, genellikle oluşturma işlemi tamamlandığında çağrılan bir geri çağırma sağlarsınız.

 Katman yapıt başvuruları, kullanım örneği diyagramlarında yapıtlarla karıştırılmamalıdır.

## <a name="shapes-and-diagrams"></a>Şekiller ve diyagramlar
 İki nesne, bir katman modelinde her bir öğeyi temsil etmek için kullanılır: bir `ILayerElement` ve bir [IBir IShape](/previous-versions/ee806673(v=vs.140)). @No__t_0, diyagramdaki şeklin konumunu ve boyutunu temsil eder. Katman modellerinde, her `ILayerElement` bir `IShape` ve bir katman diyagramındaki her `IShape` bir `ILayerElement` vardır. `IShape` UML modelleri için de kullanılır. Bu nedenle, her `IShape` bir katman öğesine sahip değildir.

 Aynı şekilde, `ILayerModel` tek bir [IDiagram](/previous-versions/ee789658(v=vs.140))üzerinde görüntülenir.

 Özel bir komut veya hareket işleyicisi kodunda, `DiagramContext` içeri aktarma işleminde geçerli diyagramı ve şekillerin geçerli seçimini alabilirsiniz:

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

 ![Her ILayerElement bir IShape tarafından sunulur.](../modeling/media/layerapi-shapes.png)

 [IShapes](/previous-versions/ee806673(v=vs.140)) ve [ıDIAGRAM](/previous-versions/ee789658(v=vs.140)) , UML modellerini göstermek için de kullanılır. Daha fazla bilgi için bkz. [DIYAGRAMLARDA UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Katman diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Katman diyagramlarına özel özellikler ekleme](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)
