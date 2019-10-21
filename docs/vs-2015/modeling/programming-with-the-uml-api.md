---
title: UML API ile programlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b264987818e244cf016e9b54794109cafc548439
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652106"
---
# <a name="programming-with-the-uml-api"></a>UML API ile Programlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun UML API 'SI, UML modellerini ve diyagramlarını oluşturmak, okumak ve güncelleştirmek için kod yazmanıza olanak tanır. Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 API başvuru sayfalarına ek olarak, aşağıdaki konularda API açıklanır.

|Konu|Örnek türleri ve açıklanan Yöntemler|Açıklanan özellikler|
|-----------|-----------------------------------------|------------------------|
|[UML API ile ilişkilerde gezinme](../modeling/navigate-relationships-with-the-uml-api.md)|UML öğeleri ve özellikleri ve ilişkilendirmeleri. Örneğin, IClass, IActivity, IUseCase, IComponent, Iıntercomponent, IModel, IPackage dahil olmak üzere IElement ve alt öğeleri.|UML modelleri, Visual Studio 'da UML [kaynak sayfasında](http://go.microsoft.com/fwlink/?LinkId=160796)elde edilen UML belirtim sürümü 2.1.2 'yi ile uyumlu olur. Her tür, UML türüyle aynı ada sahip olan ve "I" önekli bir arabirimdir.|
|[UML modellerinde öğe ve ilişki oluşturma](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage. CreateClass ()<br /><br /> IClass. CreateOperation ()|Her öğe türünün alt öğelerini oluşturmak için yöntemleri vardır.|
|[Diyagramlar üzerinde model görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape. Move ()|Bir modeldeki her öğe diyagram üzerinde bir şekil olarak temsil edilebilir. Bazı durumlarda, her nesne için yeni şekiller oluşturabilirsiniz. Bu şekilleri taşıyabilir, yeniden boyutlandırabilir, renkleyebilir, daraltabilir veya genişletebilirsiniz.|
|[UML modelinde gezinme](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Model deposu modeli depolar.<br /><br /> Diyagram bağlamı, geçerli diyagrama ve depoya erişmenizi sağlar.|
|[İşlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md)|Ilınkedundocontext|Bir dizi değişikliği tek bir işleme bağlayabilirsiniz.|
|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|Imtrkomutu<br /><br /> IGestureExtension<br /><br /> Iommandexgeri|Bir diyagramın işlevselliğini çift tıklayarak ve diyagram üzerine sürükleyerek çağrılan komutları tanımlayarak genişletebilirsiniz.|
|[UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Bir modelin belirtilen kısıtlamalara uyduğundan emin olmanıza yardımcı olacak doğrulama kuralları tanımlayabilirsiniz.|
|[IDataObject nesnesinden UML model öğelerini alma](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Bir öğe UML Model Gezgini 'nden veya UML diyagramından başka bir diyagrama veya uygulamaya sürüklendiğinde, bir IDataObject olarak serileştirilir.|
|[UML API kullanarak sıralama diyagramlarını düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|Iınterbir, ILifeline, IMessage|Etkileşim diyagramı oluşturma ve güncelleştirme, diğer diyagram türleriyle çalışmaktan biraz farklıdır.|
|[Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)|ILayer, ılayerdiagram|Katman diyagramları oluşturmak ve düzenlemek için kod yazabilir ve ayrıca program kodunu bunlara karşı doğrulayabilirsiniz.|

## <a name="about-the-implementation"></a>Uygulama hakkında
 UML modelleme araçları [!INCLUDE[dsl](../includes/dsl-md.md)] kurulmuştur. Her bir paket ve her diyagram bir [!INCLUDE[dsl](../includes/dsl-md.md)] modeliyle temsil edilir ve bir kural ve diğer yöntem koleksiyonu aralarında tutarlılığı sağlar.

 Bu platformdaki türler, UML uzantıları yazmak için başvurduğunuz bazı derlemelerde görünür. UML araçlarına [!INCLUDE[dsl](../includes/dsl-md.md)] API 'sine erişerek uzantılar yapabilirsiniz, ancak aşağıdaki noktaları göz önünde bulundurmanız gerekir:

- Görünüşe göre bazı basit değişikliklerin tutarsızlıklar ve beklenmeyen etkileri tanıtmasının fark edebilirsiniz.

- Uygulama gelecekte değişebilir, bu sayede [!INCLUDE[dsl](../includes/dsl-md.md)] API 'sini kullanarak yaptığınız uyarlamalar artık işe mayabilir.

## <a name="the-api-assemblies"></a>API derlemeleri
 Bu tablo, UML araçları için genişletilebilirlik sağlayan derlemeleri ve kullanmanız önerilen ad alanlarını özetler.

|Derleme|Ad Alanları|Erişim sağlar:|
|--------------|----------------|-------------------------|
|Microsoft. VisualStudio. Uml. Interfaces|Bütün|UML türleri.|
|Microsoft. VisualStudio. mimari Turetools. Extensibility|Microsoft. VisualStudio. mimari Turetools. Extensibility. Uml|[Oluşturma yöntemleri](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft. VisualStudio. mimari Turetools. Extensibility. Presentation|[Diyagramlar ve şekiller](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft. VisualStudio. mimari Turetools. Extensibility|[Modelleme projesi](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft. VisualStudio. model. SDK. sürümünüze|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Menü komut uzantısı](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Bağlı geri alma işlemleri](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Doğrulama](../modeling/define-validation-constraints-for-uml-models.md)|
||(diğer ad alanları)|Yalnızca Gelişmiş kullanım için önerilir.|
|Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Hareket işleyicileri](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|
||(diğer ad alanları)|Yalnızca Gelişmiş kullanım için önerilir.|
|Microsoft. VisualStudio. TeamFoundation. WorkItemTracking|Microsoft. VisualStudio. TeamFoundation. WorkItemTracking|[İş öğelerinin bağlantıları](../modeling/define-a-work-item-link-handler.md).|
|Microsoft. TeamFoundation. WorkItemTracking. Client|Microsoft. TeamFoundation. WorkItemTracking. Client|[İş öğeleri ve alanları](../modeling/define-a-work-item-link-handler.md).|
|Microsoft. TeamFoundation. Client|Microsoft. TeamFoundation. Client|[İş öğeleri ve alanları](../modeling/define-a-work-item-link-handler.md).|
|System. ComponentModel. Composition|<xref:System.ComponentModel.Composition>|[MEF bileşenleri için dışarı ve Içeri aktarma](../modeling/define-and-install-a-modeling-extension.md)|
|System. Linq|<xref:System.Linq>|[Özellikle ilişkilerle ilgilenirken koleksiyonların kolay düzenlemesi](../modeling/navigate-relationships-with-the-uml-api.md).|

## <a name="see-also"></a>Ayrıca Bkz.
 UML [modelleme genişletilebilirliği IÇIN](../modeling/api-reference-for-uml-modeling-extensibility.md) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) API başvurusu
