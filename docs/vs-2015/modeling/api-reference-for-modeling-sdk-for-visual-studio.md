---
title: Modelleme SDK 'Sı için API başvurusu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672839"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Visual Studio için Modelleme SDK'sı için API Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio görselleştirme ve modelleme SDK 'Sı, etki alanına özgü dillerinizin (DSL) ve UML araçlarının oluşturulduğu platformu sağlar.

> [!NOTE]
> UML modelleme API 'SI hakkında daha fazla bilgi için bkz. [UML modelleme genişletilebilirliği Için API başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md). Metin dönüşümü hakkında daha fazla bilgi için bkz. [T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md).

 Bu bölüm, "Microsoft. VisualStudio. Modellendirme" ile başlayan adlara sahip ad alanları için başvuru malzemeleri içerir.

|Ad Alanı|İçerik|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Bir DSL içinde tanımladığınız tüm etki alanı sınıflarının temel sınıfı olan ModelElement gibi sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|DSL tanımının bir kısmını oluşturan sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model deposu Görüntüleyicisi ve performans ölçümü araçları.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Bir DSL içinde tanımladığınız tüm şekillerin temel sınıfı olan ShapeElement gibi sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Hareket ve seçim yöntemleri.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL tanımı tasarımcısının API 'SI.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL tanımı tasarımcısının iç sınıfları.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|DSL tasarımcısını komutlar, hareketler ve doğrulamayla genişletmenize imkan tanıyan öznitelikler.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|DSL genişletilebilirliği uygulayan ModelElement için uzantı yöntemleri.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Genişletilebilirlik öznitelikleri|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Bir modelin parçalarını salt okunurdur yapmanızı sağlar.|
|[Microsoft. VisualStudio. modelle tümleştirme](/previous-versions/ee904412(v=vs.140))|Farklı modelleri tümleştirmenize yardımcı olan ModelBus API 'SI.|
|[Microsoft. VisualStudio. modelle Integration. Picker](/previous-versions/ee904394(v=vs.140))|Kullanıcıların ModelBus başvuruları oluşturmak için modeller ve öğelere gezinmelerini sağlayan iletişim kutusu.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Seçici hizmeti.|
|[Microsoft. VisualStudio. modelle Integration. Shell](/previous-versions/ee869435(v=vs.140))|@No__t_0 için ModelBus bağdaştırıcı çerçevesi.|
|[Microsoft. VisualStudio. modelle Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|Kullanıcıların ModelBus başvuruları oluşturmak için modeller ve öğelere gezinmelerini sağlayan Seçici iletişim kutusu.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|DSLs ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] arasındaki arabirim.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Kısayol (bağlam) menü komutları tanımlamanızı sağlar.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Doğrulama kısıtlamalarını tanımlamanızı sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [UML Genişletilebilirlik Modellemesi için API Başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)
