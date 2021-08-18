---
title: Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
description: Visual Studio'da modelleri ve diyagramları okumanın yanı sıra model oluşturma desteği olmayan bir Visual Studio salt okunur davranış hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4adcdb442e31a0de834a05a06ea96981b761ea73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100783"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma

Modeli, model oluşturma desteği olmayan Visual Studio sürümde açtığında, model salt okunur modda açılır. Bu modda diyagramların düzenini değiştirebilirsiniz ancak modeli değiştiremezsiniz.

Model oluşturma desteğinin hangi Visual Studio için [bkz. Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Modele ve Diyagramlara Erişim Alma

Bağımlılık diyagramını okumak için önce Visual Studio kullanarak modelleme projesini ve ardından içindeki diyagramı açabilirsiniz.

Bu nedenle, bir bağımlılık diyagramını okumak için, oluşturulduktan sonra modelleme projesine de erişiminizin olması gerekir. Bunu yapmak için kaynak denetiminden projeye erişebilirsiniz veya proje dosyalarının bir kopyasını edinebilirsiniz.

> [!NOTE]
> Bu, koddan oluşturulan kod eşlemeleri ve .NET sınıf diyagramları için geçerli değildir. Bu diyagramlar bir modelleme projesinin bağımsız olarak görünüme sahip olabilir.

Bağımlılık diyagramını okumak için ihtiyacınız olan minimum dosya kümesi aşağıdaki gibidir:

- Okumak istediğiniz diyagram için iki diyagram dosyası; örneğin, **MyDiagram.classdiagram ve MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > Bağımlılık diyagramları için _MyDiagram_**.layerdiagram.suppressions adlı dosyaya da sahipsiniz.**

- Modelleme proje dosyası (**MyModel.modelproj**)

- Kök model dosyası (**ModelDefinition\MyModel.uml**)

- Diyagramda başvurulan herhangi bir paket için paket dosyaları (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Read-Only Modunda Read-Only Yapabilirsiniz

Modeli ve diyagramlarını model oluşturma desteği Visual Studio bir sürümde açarsanız modeli değiştiremezsiniz. Başka bir ifadeyle diyagramlarda veya model gezgininde görüntülenen öğeleri ve ilişkileri değiştiremezsiniz. Ancak diyagramların düzeninde bazı değişiklikler yapabilirsiniz:

- Diyagramda şekilleri ve bağlayıcıları yeniden düzenleme.

- Şekilleri genişletme ve daraltma.

Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılara görünür yapmak için en azından güncelleştirilmiş .layout dosyalarını **göndermeniz** gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
