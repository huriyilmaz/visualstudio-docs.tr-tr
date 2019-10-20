---
title: Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671284"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model açtığınızda, model salt okuma modunda açılır. Bu modda, diyagramların yerleşimini değiştirebilirsiniz, ancak modeli değiştiremezsiniz.

 Hangi Visual Studio sürümünün model oluşturmayı desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Model ve diyagramlara erişim sağlama
 Bir UML diyagramını veya katman diyagramını okumak için öncelikle Visual Studio 'Yu kullanarak modelleme projesini açın ve sonra diyagramı içinde açın.

 Bu nedenle, bir UML diyagramını veya katman diyagramını okumak istiyorsanız, oluşturulduğu modelleme projesine de erişiminizin olması gerekir. Bunu, projeye [!INCLUDE[esprscc](../includes/esprscc-md.md)] erişerek ya da proje dosyalarının bir kopyasını alarak yapabilirsiniz.

> [!NOTE]
> Bu, koddan oluşturulan kod haritaları ve .NET sınıf diyagramları için geçerlidir. Bu diyagramlar, modelleme projesinden bağımsız olarak görüntülenebilir.

 Bir UML diyagramını veya katman diyagramını okumak için, ihtiyacınız olan minimum dosya kümesi aşağıdaki gibidir:

- Okumak istediğiniz diyagram için iki Diyagram dosyası; örneğin, **MyDiagram. classdiagram ve MyDiagram. classdiagram. Layout**.

    > [!NOTE]
    > Katman diyagramlarında, _MyDiagram_ **. layerdiagram. suppressions**adlı dosyaya da sahip olmanız gerekir.

- Modelleme proje dosyası (**MyModel. modelproj**)

- Kök model dosyası (**Modeldefinition\mymodel.exe**)

- Diyagramda başvurulan herhangi bir paket için paket dosyaları (**Modeldefinition\mypackage.exe**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Salt okuma modunda yapabileceğiniz değişiklikler
 Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model ve diyagramlarını açarsanız modeli değiştiremezsiniz. Diğer bir deyişle, diyagramlarda veya model Gezgininde görüntülenen öğeleri ve ilişkileri değiştiremezsiniz. Ancak, diyagramların düzeninde bazı değişiklikler yapabilirsiniz:

- Diyagramdaki şekilleri ve bağlayıcıları yeniden düzenleyin.

- Şekilleri Genişlet ve daralt.

  Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılara görünür yapmak istiyorsanız, en azından güncelleştirilmiş **. Layout** dosyalarını göndermeniz gerekir.

## <a name="RelatedTopics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)|Katman diyagramı, var olan veya önerilen bir mimarinin yapısını gösterir. Kod yazıldığında, katman diyagramına göre otomatik olarak doğrulanabilir.|
|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|Bir etkinlik diyagramı, iş sürecinde veya yazılımda iş akışını gösterir.|
|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|Bir sınıf diyagramı, kod, veritabanı şemaları, iletişim protokolleri veya bir iş etki alanını tanımlamakta kullanılan koşulların sözlüğü gibi birçok bağlamda kullanılan türleri ve ilişkileri gösterir.|
|[UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)|Bir bileşen diyagramı, yazılım tasarımında ayrılabilir parçaları ve bunların arabirimlerini gösterir.|
|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|Bir sıralı diyagram, yazılım tasarımındaki öğeler arasındaki etkileşimleri gösterir.|
|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|Kullanım durumu diyagramı, bir sistemin kullanıcılarını ve belirli hedeflere ulaşmak için gerçekleştirebilecekleri etkinlikleri gösterir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
