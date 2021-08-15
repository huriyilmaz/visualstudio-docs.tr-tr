---
title: Modelleme SDK'sı için API Başvurusu
description: Visual Studio Görselleştirme ve Modelleme SDK'sı'nın etki alanına özgü diller (DSL) araçlarınız üzerinde oluşturulduğu platformu nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5674486ec330dc804fa43836f64dcc439e0fc4a169244db217a41fe4cecd193c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316922"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Visual Studio için Modelleme SDK'sı için API Başvurusu

Visual Studio Görselleştirme ve Modelleme SDK'sı, etki alanına özgü dil (DSL) araçlarınız üzerinde oluşturulduğu platformu sağlar.

Bu bölüm, "Microsoft.VisualStudio.Modeling" ile başlayan ad alanlarına başvuru malzemeleri içerir.

|Ad Alanı|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|DSL'de tanımladığınız tüm etki alanı sınıflarının temel sınıfı olan ModelElement gibi sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|DSL tanımının bir parçası olan sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model Store Viewer ve performans ölçümü araçları.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|DSL'de tanımladığınız tüm şekillerin temel sınıfı olan ShapeElement gibi sınıflar.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Hareket ve Seçim yöntemleri.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL Tanım tasarımcısının API'si.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL Tanım tasarımcısının iç sınıfları.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|DSL tasarımcısını komutlar, hareketlerle ve doğrulamayla genişletmeye olanak sağlayan öznitelikler.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|DSL Genişletilebilirliği uygulayan ModelElement için uzantı yöntemleri.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Genişletilebilirlik öznitelikleri|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Bir modelin bölümlerini salt okunur hale alasiniz.|
|[Microsoft.VisualStudio.Modeling.Integration](/previous-versions/ee904412(v=vs.140))|Farklı modelleri tümleştirebilirsiniz.|
|[Microsoft.VisualStudio.Modeling.Integration.Picker](/previous-versions/ee904394(v=vs.140))|Kullanıcıların Modelbus başvuruları oluşturmak için modellere ve öğelere gezinmelerine olanak sağlayan iletişim kutusu.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Seçici hizmeti.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell](/previous-versions/ee869435(v=vs.140))|Visual Studio için Modelbus bağdaştırıcısı çerçevesi.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell.Picker](/previous-versions/ee886769(v=vs.140))|Kullanıcıların modellere ve öğelere gidip Modelbus başvuruları oluşturmalarını sağlayan Seçici iletişim kutusu.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|DSL'ler ile Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Kısayol (bağlam) menü komutlarını tanımlamaya olanak sağlar.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Doğrulama kısıtlamalarını tanımlamaya olanak sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)
