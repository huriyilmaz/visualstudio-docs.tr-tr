---
title: Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
description: model oluşturmayı desteklemeyen bir Visual Studio sürümünü kullanırken Visual Studio modelleri ve diyagramları okuma ve salt okuma davranışı hakkında bilgi edinin.
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
ms.openlocfilehash: b06e5796f5e0ad754b7df915187c5cf3e18b246318508cb7e5b122ede9806849
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271231"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma

modeli oluşturmayı desteklemeyen bir Visual Studio sürümünde bir modeli açtığınızda, model salt okuma modunda açılır. Bu modda, diyagramların yerleşimini değiştirebilirsiniz, ancak modeli değiştiremezsiniz.

hangi Visual Studio sürümünün model oluşturmayı desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Model ve diyagramlara erişim sağlama

bir bağımlılık diyagramını okumak için, önce modelleme projesini açmak üzere Visual Studio kullanmanız ve sonra diyagramı içinde açmanız gerekir.

Bu nedenle, bir bağımlılık diyagramını okumak istiyorsanız, oluşturulduğu modelleme projesine de erişiminizin olması gerekir. Bunu, projeye kaynak denetiminden erişerek ya da proje dosyalarının bir kopyasını alarak yapabilirsiniz.

> [!NOTE]
> Bu, koddan oluşturulan kod haritaları ve .NET sınıf diyagramları için geçerlidir. Bu diyagramlar, modelleme projesinden bağımsız olarak görüntülenebilir.

Bir bağımlılık diyagramını okumak için, ihtiyacınız olan minimum dosya kümesi aşağıdaki gibidir:

- Okumak istediğiniz diyagram için iki Diyagram dosyası; örneğin, **MyDiagram. classdiagram ve MyDiagram. classdiagram. Layout**.

    > [!NOTE]
    > Bağımlılık diyagramlarında, _MyDiagram_**. layerdiagram. suppressions** adlı dosyaya da sahip olmanız gerekir.

- Modelleme proje dosyası (**MyModel. modelproj**)

- Kök model dosyası (**Modeldefinition\mymodel.exe**)

- Diyagramda başvurulan herhangi bir paket için paket dosyaları (**Modeldefinition\mypackage.exe**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Read-Only modunda yapabileceğiniz değişiklikler

model oluşturmayı desteklemeyen bir Visual Studio sürümünde model ve diyagramlarını açarsanız, modeli değiştiremezsiniz. Diğer bir deyişle, diyagramlarda veya model Gezgininde görüntülenen öğeleri ve ilişkileri değiştiremezsiniz. Ancak, diyagramların düzeninde bazı değişiklikler yapabilirsiniz:

- Diyagramdaki şekilleri ve bağlayıcıları yeniden düzenleyin.

- Şekilleri Genişlet ve daralt.

Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılara görünür yapmak istiyorsanız, en azından güncelleştirilmiş **. Layout** dosyalarını göndermeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
